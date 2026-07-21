---
title: "I caught my first loop today, sir"
date: 2026-07-20T09:00:00-04:00
description: "AI maturity means moving humans farther and farther from the code and process of deploying changes. I built my first hands-off loop that updated and deployed code to production. Sharing some lessons learned along the way and time-saving ideas on how to use Claude Workflows."
displayInMenu: false
displayInList: true
featuredImage: "/posts/2026/07/loop-engineering/point-break.webp" 
featuredImageDescription: "One of the most epic action films of all time - Point Break"
categories: ["ai","devops"]
draft: false
---
If you haven't seen Point Break you are seriously missing out. It's a fantastic movie from the early 90's that doesn't seem ashamed at all that it could have fit right in with the epic movies of the previous decade. Keanu Reeves has to learn how to surf in order to infiltrate a criminal group and take down a crime boss. The investigation doesn't start out great, but after getting reemed out by his boss he shares one bit of good news, at least: "I caught my first tube today, sir!"

Ok, ok, it's a stretch but this is how my brain works. 

## What is a loop?
To understand loops it's helpful to think about the stages of AI adoption. There are many frameworks for organizational maturity related to AI, but I'm talking about the implementation of AI in software engineering. I prefer the [8 stages that Bassim Eledath describes](https://www.bassimeledath.com/blog/levels-of-agentic-engineering). 

That model mirrors my experience so far. In the beginning you are driving a single AI agent, explaining what you want it to do. You get frustrated because it keeps forgetting things, so you figure out how to document the project standards such that each time you spin up an agent it uses the right frameworks and conventions consistently. You then realize there's common sets of commands you keep giving the agent every time: how you want it to do code reviews, or handle a deployment process, find information, or run automated tests, etc. So you figure out how to formalize those into Skills and MCP tool calls. At this point your main role becomes defining the work you want the agent to take on. You might plug it directly into an issue tracker like Jira but you are still pointing it at one unit of work at a time, and you're still defining the work itself.

All that gets you through stage 6. And this is where you first start thinking about loops.

A loop is where you start taking yourself out of the implementation process. Instead you start designing an agent that can drive the whole thing, including self-improvement, independently.  It sounds cool but it was trickier than I expected.

## My challenge
Last week I took one of my side projects, [ClassComposer](https://classcomposer.app), and had Fable and Opus run a comprehensive analysis to look for bugs or improvement opportunities. I could write up a whole post just on that step alone, but the bottom line is between the two scans we filed 29 github issues to clean up several large files, fix a few bugs, tighten up the CI and deploy process, and improve several things about the claude code workflow itself. Claude helped figure out the order to sequence these things, and we tagged all of them in github so they were easy to find. But thinking about doing all those backend improvements one at a time, even if I'm just driving the agent, seemed boring to me.

So instead I embarked on building a prompt that could do the work for me. My first loop.

## Approach and what I learned
My first try at this approach started with just writing a really big prompt that described everything about the orchestrator and how I wanted it to use sub-agents to do the work. That entire prompt ended up being 650 lines long, so I'm not going to post the whole thing. If you want a copy, send me a message and I'll gladly share it.

The orchestrator knew the sequence of the issues to fix because the original code analysis laid that out. One a time, it spawned a sub-agent that was dedicated to fixing one of those issues. There was a detailed workflow it enforced, keeping track of progress using a state.json file so we could resume in case of a crash or something. Once the implementing sub-agent was done, it told the orchestrator the pull request number it opened. 

The orchestrator then spawned a new sub-agent. This one had a fresh context and was designed to be adversarial. It reviewed the code and made sure nothing got changed that looked outside the scope of the original github issue. It double checked that all tests pass. Some types of issues required human review - these got held until I reviewed the pull request and added a "human-approved" tag to it. Other types of issues were lower risk and could proceed on their own.

Whether it was low risk or I human-approved it, the orchestrator then merged the PR and the pipelne automation deployed the change to production.

  - Issues closed: 29
  - PRs merged: 34, including 1 hotfix
  - Net LOC: +11,581 / −9,275
  - Tests added: 114
  - Session cost: $213
  - Session duration: >6h API time, >24h total clock time from first issue
  - Fable and Opus drove analysis and planning, Opus managed orchastrator agent, Haiku did code changes (surprised me, more below)
  - Orchestrator used 39% of context window (Opus 4.7 1M context window)

### Evolution
This first pass was wild to watch. I was at my son's swim meet checking the updates on my phone thanks to claude code's remote-control feature. I'd watch him finish a heat and give him a high-five, then glance at my phone when I got back to my chair only to see Claude had deployed to production while that was going on. It was a kind of like the first time I rode in a self-driving car.

Some things didn't work perfectly. Apparently Claude has a default model setting and mine was somehow set to Haiku, which caused all my sub-agents to be spawned with Haiku. That caused some issues because Haiku is not meant for complex code changes. Another comprehensive scan to assess the damage resulted in another 7 github issues filed.

This gave me a chance to mature the approach a bit more. I formalized the definition of the agents, which allows you to specify which model claude should use for them and avoids that Haiku issue from happening. I split the work into four new agents:
 - code-triager: go through all "auto-build" tagged open github issues and find an ideal sequence for them
 - code-implementer: make the necessary code changes for one issue
 - code-reviewer: review code changes against the original intent of the github issue and check against all documented coding standards
 - deploy-checker: validate that a production deployment succeeded

 That slimmed the top level prompt down a lot for the second pass and worked fine. 7 more issues fixed, again mostly without even needing my review. This led to discovering the last optimization opportunity: Claude actually has a native construct for the parent prompt I still wasn't taking advantage of.

## Claude Code Workflows
[Workflows](https://code.claude.com/docs/en/workflows) are claude code's native approach for formalizing a deterministic process. They are written in javascript, but you can have claude write them for you. Once written you can invoke them like any skill. Workflows can leverage your agent definitions to go do work.

Converting my orchestrator prompt to a workflow was a breeze - I just had claude write it for me based on the parent prompt. The big benefit to this is I can observe the workflow much better than before using `/workflows`, and managing the state is much easier. I don't have to worry about the orchestrator hallucinating or forgetting to update the state.

For example, here is the code in my workflow the calls out to a sub-agent to implement a github issue. It waits for the agent to finish and expects the response it outputs to contain information about whether it was successful and the PR it opened.
```javascript
implRaw = await agent(brief, {
    agentType: 'code-implementer',
    label: attempt === 1 ? `impl:#${issueN}` : `impl:#${issueN}:retry`,
    phase: 'Implement + merge',
})
implStatus = extractStatus(implRaw)
pr = extractPr(implRaw)
log(`impl:#${issueN} attempt=${attempt} → status=${implStatus} pr=${pr ?? 'none'}`)
```
In that case, we are allowing a sub-agent to handle something non-deterministic (implementing code changes) but then we go back to a deterministic structure to handle the outcome. This block checks whether we've already tried and failed to implement a github issue twice:
```javascript
if (attempt === 2) {
    // Both attempts exhausted — apply `blocked` label, log, and continue.
    log(`Attempt 2 also ${implStatus} on #${issueN}. Applying \`blocked\` label and continuing to next issue.`)
    await bash(
    `gh issue comment ${issueN} --body "Auto-loop attempted this twice; both attempts returned ${implStatus}. See workflow ledger. Applying \\\`blocked\\\` label — a human needs to break the deadlock." && gh issue edit ${issueN} --add-label blocked`,
    'issue:mark-blocked'
    )
    await appendLedger({
    issue: issueN, phase: item.phase, pr, outcome: 'blocked',
    attempts: 2, note: `both attempts returned ${implStatus}`,
    })
    await writeState({ current_issue: null, status: 'idle' })
    markedBlocked = true
}
```

As you can see, there's no chance of an LLM mishandling that decision. Putting these kinds of decision points in code is a smart way to enforce deterministic outcomes.

## Pre-work was important, but I still didn't do enough
In order for this loop to work in the first place I had to do a bit of prep work. Since I was relying on myself being in the middle of context driving with agents before, I was doing things like manually testing changes in the dev environment. Sure, I had end to end tests, but I never _relied_ on them. So step one was making sure my CI process enforced running my end to end tests. I also had to audit that test coverage and make sure they were testing the right things. I also enabled formal branch protections in github so that my sub agents could never lie to me about whether they ran the tests or not.

Even with this pre-work I still ended up with a prod bug. I think having real end-to-end synthetic tests in production is going to be necessary going forward. The key consideration is where to leverage deterministic checks VS human/machine judgement. You want your pipeline automation to be the definitive source of truth when it comes to deciding whether a deploy should proceed. Don't just trust the agents to make that call based on their opinion. And although mocking and integration tests are good at catching a lot of problems, nothing beats a full test of the actual application.

## What's next
This workflow still requires me to define work and label it manually so that the workflow can pick it up and execute it. My next step is going to be defining another workflow that runs security scans, probably using the recently released [VulnHunter tool from CapitalOne](https://www.capitalone.com/tech/open-source/announcing-vulnhunter/), to define more non-user facing improvements and tag them for my automated implementation pipeline. That can run every 24 hours and proactively ensure the codebase stays secure. I need to get end to end validation working in production first, though.