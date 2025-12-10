---
title: "Modernizing Legacy Code: The Challenge of Forgetting"
date: 2025-12-09T07:00:00-05:00
description: "Organizations develop a shared memory space that morphs and changes over time, just like an individual's memories.  I discuss the theory and its implications on things like turnover and modernization projects.  I also demonstrate the theory using source code examples.  Finally, we ponder how LLMs might or might not change the fundamental problem."
displayInMenu: false
featuredImage: "/posts/2025/12/modernizing-code-cognition-theory/code-tablet-3.png"
featuredImageDescription: "Ancient tablet depicting some legacy java software code being examined by an archeologist"
categories: ["philosophy", "leadership", "ai"]
draft: false
---
For those of us who have ever worked on modernizing a legacy system, you know it can feel as much like archeology as computer science.  We dig through old documents, code comments, and interview whoever we can find from when it was built to piece it all together.  We're not asking _how_ the system works, we want to know _why_ it works the way it does.  As systems age two things happen at the same time: the system improves (but usually gets more complex), and fewer people remain who were there when it was started.  As those folks move on, maintenance and modernization gets much more risky and expensive.

We have to step back a minute to understand how this phenomenon unfolds.  You see, when people spend a lot of time together, they develop a sense of what the other person knows.  This is the foundation behind a theoretical model developed by Daniel Wegner in the mid-80's.  An excerpt from a paper he co-wrote in 1991 illustrates the idea:

>  One partner may not know where to find candles around the house, for instance, but may still be able to find them in a blackout by asking the other partner where the candles are. [...] Such knowledge of one another's memory areas takes time and practice to develop, but the result is that close couples have an implicit structure for carrying out the pair's memory tasks. With this structure in place, couples in close relationships have a transactive memory that is greater than either of their individual memories.[^1]

This happens at work as well as at home.  We develop this same sense with our colleagues.  When you scale this out to larger groups, you start to get into a whole area of study called Organizational Cognition.  Work in that field has been steadily expanding since the early 90's when the US Academy of Management established a formal Interest Group for it.[^2]. A subset of this field deals specifically with the concept of Organizational Memory.

# Tacit Knowledge
When I wrote my graduate thesis on the impacts of turnover on software teams, this was one of the frameworks that help us understand how turnover hurts knowledge work teams.  Some amount of the knowledge of the group gets written down as formal documentation, and for teams that produce artifacts like databases or software code, still more of that knowledge gets transferred into the code.  However, it's impossible to capture everything a person knows.  Therefore, when a person leaves a company we know there is some amount of tacit knowledge that goes with them and cannot be replaced or recovered.

What is not clear yet is the size of the gap between what we can retrieve from those artifacts and what is actually lost, and what LLMs could change about that.

# What does our Code Preserve?
Way back in 2012 before LLMs were commonly available, a couple of researchers found they could use basic NLP to extract information about the domain areas of a program by parsing the source code directly.[^3] Since the explosion of LLMs, research in this area has been rapidly expanding.  The most recent and comprehensive survey I found on the topic had 173 references in it.[^4] 

While it's amazing that an LLM can now read most types of source code (they struggle with some languages) and tell us _how_ the code works, I think the tacit knowledge lost by turnover usually has more to do with _why_ the code works the way it does.  **Business rules become fossilized in source code.**  Policies become `if` statements, regulations become validation logic, and historical compromises become code branches and special cases.  

Let's consider some representative variable names:
 
 - `DeferredRevenuePreASC606`
 - `legacyTaxMultiplierNYPre2018`
 - `manualOverrideForHospitalAccounts`
 - `isMaterialityException`

Variable names like these have historical context.  They may reflect aspects of the state of risk tolerance or the interpretation of accounting standards.  Characteristics like these are not static.  Software code becomes a tiny window into the climate of when it was written.  Like studying ice core samples or diaries.[^9]

## Procedural Memory in Practice
Consider this block of code:
```java
if (isHealthcareClient && contractDate < ACA_CUTOFF) {
    applyLegacyBillingRules();
}
```

From this short snippet we learn quite a bit:
 - Healthcare customers are special
 - Contracts around a cutoff date behave differently
 - The business lived through a regulatory change
 - Backward compatibility mattered more than elegance

The principle here is that organizational memories often survive as symbols in software code or other artifacts, but the meaning behind those symbols often cannot be gleaned from the artifact alone. **They are memories that are preserved procedurally, but not semantically.**

# The Value of Historical Context
That matters more than you might think.  When it comes time to inevitably replace that code snippet above, the new team will have questions about why the old code was written that way.  They will look up the names of long departed engineers in vain and be left with uncertainty and doubt.  Did we apply legacy rules that way because other systems also had to call that same block of code at the time?  Did we use those `if` statements because of regulatory rules, or because of system performance issues that had to be mitigated?

Studies support the importance of historical context on the modernization process.  One study showed 37% faster implementation and 42% fewer defects when a formal knowledge transfer framework was followed.[^5] An IBM case study of modernizing a Cobol system called out knowledge of the old system as a critical component of success.[^6]  So did a multi-case study of legacy systems in European public administration tools.[^7] There are many more references like these available.

So knowing _why_ systems work a certain way is not just a nice-to-have.  I've already written about [the practical limitations of trying to "teach" an LLM with current tools](https://eason.blog/posts/2025/07/why-ai-cant-replace-developers/).  Current-gen LLMs are great at explaining how most software code works, but so far it doesn't seem possible to get much of the why.

# The Value of a Software Engineer
I think about this question a lot.  The industry tends to think of engineers primarily as code production machines.  That's why there was so much hype early on about LLMs replacing software developers - they both write code, so what's the difference?  Managers usually recognize that part of an engineer's value is the domain areas they become experts on.  Indeed, at least one study found that it was just as important to know _where_ to find expertise on a software team as the expertise itself.[^8] I'd argue, though, that we don't hire Senior Engineers at higher salaries than Jr. levels because of their prior domain knowledge - the value proposition starts at the type, amount, and quality of code they can write.  The promise of how quickly they can learn and teach has historically been secondary.

As code production becomes cheaper thanks to LLMs, the scarce skill will be the ability to bind technical systems to shared organizational meaning. That work is not automation-resistant because it is complex; it is automation-resistant because it is contextual, historical, and social.  In this way, modernization is not just a technical process, it's an act of historical interpretation.  As with archeology, once the context is lost we're stuck guessing about what the artifacts are telling us.

[^1]: Wegner, D. M., Erber, R., & Raymond, P. (1991). Transactive memory in close relationships. _Journal of Personality and Social Psychology_, 61(6), 923–929. https://doi.org/10.1037/0022-3514.61.6.923
[^2]: Eden, C., & Spender, J. (1998). _Managerial and organizational cognition: Theory, Methods and Research._ SAGE Publications Limited.
[^3]: Abebe, S. L., & Tonella, P. (2014). Extraction of domain concepts from the source code. _Science of Computer Programming_, 98, 680–706. https://doi.org/10.1016/j.scico.2014.09.012
[^4]: Jelodar, H., Meymani, M., & Razavi-Far, R. (2025, March 21). Large Language Models (LLMs) for Source Code Analysis: applications, models and datasets. arXiv.org. https://arxiv.org/abs/2503.17502
[^5]: Krishnaswamy Gnanasekaran, B. (2025). Preserving critical domain knowledge during legacy Retirement System Modernization: A knowledge Transfer framework. _International Journal of Computer Techniques,_ 12(3). https://ijctjournal.org/wp-content/uploads/2025/05/Preserving-Critical-Domain-Knowledge-During-Legacy-Retirement-System-Modernization-A-Knowledge-Transfer-Framework.pdf
[^6]: IBM, Khadka, R., Saeidi, A., Jansen, S., Hage, J., & P Haas, G. (2009). Migrating a Large scale legacy Application to SOA: Challenges and Lessons learned. _Department of Information and Computing Sciences, Utrecht University._ https://slingerjansen.nl/wp-content/uploads/2009/04/cr_wcre_ver1-1.pdf
[^7]: Irani, Z., Abril, R. M., Weerakkody, V., Omar, A., & Sivarajah, U. (2022). The impact of legacy systems on digital transformation in European public administration: Lesson learned from a multi case analysis. _Government Information Quarterly,_ 40(1), 101784. https://doi.org/10.1016/j.giq.2022.101784
[^8]: He, J., Butler, B. S., & King, W. R. (2007). Team Cognition: Development and evolution in software project teams. Journal of Management Information Systems, 24(2), 261–292. https://doi.org/10.2753/mis0742-1222240210
[^9]: For an interesting explanation of why diaries don't serve as reliable historical sources, read the forward from _The Third Reich as I See It_ [https://www.jstor.org/stable/j.ctv33pb047](https://www.jstor.org/stable/j.ctv33pb047).  It's a study of what it was like for ordinary German citizens during the rise of the Nazi party based on a broad study of personal diaries.  The author does a great job explaining what diaries can and cannot be used for in the forward.