---
title: "All these DevOps cycle graphics are wrong"
date: 2019-04-29T05:00:00-04:00
description: "Recognize that a Deploy and a Release are two different things and adjust your tools and process to take advantage of that fact."
displayInMenu: false
featuredImage: "/posts/2019/04/all-those-graphics-are-wrong/devops-cycle.png"
categories: ["devops"]
draft: false
---
If you do a google image search for "[devops cycle](http://lmgtfy.com/?t=i&q=devops+cycle)" you will find a lot of variants of the above graphic.  The problem is that every one of them that breaks out _release_ from _deploy_ are putting them in the wrong order.

A _Release_ is a marketing driven event in which users are given access to new features accompanied with supporting documentation, videos, social media campaigns, press releases, and marketing website changes.  Coordinating all those activities, which are usually done by different teams, and having them all execute at the right time is not easy.  Without all that supporting work, the new features may go unnoticed, and the value of all the development work that went into them would be drastically reduced.

A _Deploy_ is the technical process of moving a specific version of a service or application from one environment to the another, such as from QA to Production.  A deploy event should not be noticeable to your users unless you're fixing a defect.  There are three keys to achieving this separation of a Release from a Deploy and doing true continuous deployment: test automation, deploy automation, and feature flags.

## Good test automation
Your team should feel confident that if all your automated tests pass, then the code is ready for production.  If they don't you may need more coverage, or a different kind of tests altogether.  For example, you may need to add in [Pact.io](https://pact.io) based contract tests if you have a lot of co-dependent APIs.  You may need also healthcheck endpoints added to your APIs that test the functionality and dependencies of the service.  Those healthchecks are very useful in validating a deployment as well as in monitoring the health of your services.

## Good deployment automation
You must be able to deploy code and database changes without downtime.  This isn't that hard to do anymore, depending on your technology stack.  There are deployment strategies such as Blue/Green or Canary that can help make your deployments safer as well.  

Don't ignore the ability to smoothly roll back changes.  Trusting that "fix forward" will always work is not a good strategy as it can wreck your Mean Time To Resolution (MTTR).  Nothing will make senior leadership distrust the team's desire to achieve continuous deployment faster than pissing off all your customers.

## Feature flagging
Finally, in order to push frequent, small changes to production without impacting customers you need to be able to hide user faces changes until you're ready to actually Release them.  There are products such as Launch Darkly that can make this a low effort improvement.  There are also numerous open source alternatives to help speed you along.  I encourage you to to try some of those options before you roll your own solution.

At a minimum, a simple binary on/off switch that can be controlled without having to deploy code changes is enough.  Over time you may find that UX and Product likes being able to turn new features on for subsets of users either to appease a key customer or perform A/B testing.

## Now What?
You should be able to separate a Release from a Deploy.  DevOps graphics should encourage that separation, but the Deploy event will always precede the Release.  Go look at your team's process and see if you are capable of separating these two events.  The value in being able to do that is increasing your deploy frequency, improving MTTR, and probably improving the quality of life for your development and engineering teams.  This all comes with the added bonus of giving Product and UX new tools to use in your pursuit of delighting customers.

If someone with more Photoshop skills than I have wants to make a good, correct version of that graphic I will happily share and give credit.
