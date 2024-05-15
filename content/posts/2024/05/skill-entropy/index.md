---
title: "Fighting against entropy"
date: 2024-05-14T11:00:00-04:00
description: "Development teams will devolve into silos of knowledge without active work to resist that trend."
displayInMenu: false
featuredImage: "/posts/2024/05/skill-entropy/spice-rack.webp"
featuredImageDescription: ""
categories: ["leadership","agile","training"]
draft: false
---
Pantries get less and less organized.  Don't get me started on spice racks, toy boxes, sports equipment, or tool boxes.  If you don't rigidly make sure things get put back right these things become nightmares.

Entropy is a fascinating characteristic of complex systems.  One way to define it is as the tendency for systems to become less and less organized over time.  In physics this is driven by quantum randomness.  In human systems I think it's driven by laziness.  That's definitely what plagues my spice rack.

Left unchecked, **knowledge on an engineering team will get more and more silo'd over time.**  This happens because people naturally take the path of least resistance.  When a task needs to get done, guess who does it?  The person that best knows how.  This further deepens their expertise of that task.  Rather than observing and learning that task, the other people on the team will be off doing whatever _they_ best know how to do, creating a cycle that leads to tremendous friction and risk.

We saw this illustrated in the [Phoenix Project](https://www.goodreads.com/en/book/show/17255186) in the character of Brent.  Eventually the leader had to take an extreme step to bar Brent from doing certain tasks himself and force him to teach others in order to remove Brent as a bottleneck.  This was the only way to make sure the development process couldn't get blocked by one person being unavailable or busy.

## Examples and consequences
What does that bottleneck look like in our teams? 
 - "We can't estimate/plan this story out until Bob gets back from vacation - he knows that area of the code best."
 - "I can't make that firewall config change, I have to get Susan to look at it because she's the only one with admin access to the F5."
 - Or just watch Jurassic Park.  Samuel Jackson could tell you all about what happens when only one person knows how the Unix System works.

These are all examples of how [Little's Law](https://en.wikipedia.org/wiki/Little%27s_law) and the [Theory of Constraints](https://en.wikipedia.org/wiki/Theory_of_constraints) actually play out.

There's other damages that skill entropy causes.  A Leeism I say to my folks all the time is, "If you are irreplaceable, you are unpromoteable."  When opportunities come up do you think your leader will put your name forward if they know it will crush productivity?  A great leader might, but a great leader wouldn't have let that happen in the first place.  You have to take ownership of evaluating just how irreplaceable you are in your role and whether your leader knows about your successor and trusts them.

What about requests for vacation, or being able to actually unplug while you're away?  If you're irreplaceable, you're also unvacationable.  Okay that one doesn't roll off the tongue as well, but you get it.

The bottom line is that it takes time and energy to resist this centralization of expertise, and if you're a new leader it might not even look like a problem to you yet.

## What to do
As with any problem, the first step is to visualize it.  I built [Tekata](https://tekata.io) with a friend of mine years ago to address this.  Or you can use a spreadsheet or a whiteboard.  Ultimately you need to visualize the skills your team needs against the people on the team, stack rank the skills, and identify the gaps.  My favorite thing about Tekata is that it tracks skill health over time, which can be tedious to do in a spreadsheet, but seeing that trend is helpful.
![screenshot of tekata.io application showing list of skills and how well covered the team is for each one](/posts/2024/05/skill-entropy/tekata.png "Tekata.io is free to use")
Tekata uses a weighted algorithm to make sure the most critical skills have adequate coverage, but gives grace to skills lower on the priority list.  In the example above only one person on the team is an expert with Go, and since that's the most important skill on that team, it gets an F for health, contributing to an overall C+ for the team.  If the product roadmap changes it may mean that a skill becomes more critical, and moving that up the list could highlight a new gap you need to take steps to remediate.

This process needs to become a regular part of the flow of the team.  The name "Tekata" is a fusion of "tech" and "kata," which means "dance" in Japanese.  Some ideas for cadence of re-evaluation of skill gaps:
 - Quarterly
 - When the team roster changes 
 - When product roadmaps change
 - As part of Program Increment planning
 - As part of team retrospectives

In between those check-ins, the data should drive action.  Lunch and learns, certifications, conferences, online learning, formal classes, and pair programming are all great ways to close skill and expertise gaps.  When you have someone leave, the data can help you see what skills you need to target in the backfill.

There's all kinds of interesting ways this approach can help.  Have a special project that needs some people for a few months?  Use the data to figure out where those folks are and where they can be spared with the least amount of impact.

I'd love to hear from folks on your experiences with this problem space.  It's something I may choose to target with my graduate studies I'm about to kick off.
