---
title: "Product Development Leadership Essentials"
date: 2020-02-05T05:00:00-04:00
description: "What are the core abilities I think a technical product leader needs to have?"
displayInMenu: false
featuredImage: "/posts/2020/02/product-development-leadership/three_columns.jpg"
categories: ["leadership"]
draft: false
---
When I distill the key abilities of my greatest mentors, and think about my own progression from a self-taught coder to a CTO, I come up with three main very connected things:

1. Scaling Product Usage
1. Scaling Product Development
1. Quality

When a senior leader comes to me for help, it's usually some combination of these things that are in trouble.  I'm going to cover these very high level here, and maybe expand on these topics on future posts.  If one of these topics strikes a nerve, let me know.

## Scaling Usage
Usually when someone is talking about scaling challenges, this is what they're referring to.  It's very important to have some idea about the market size you are going after.  You also need to understand what the journey is likely to look like as you gain more and more of it.  All of this is to help you design a technical system that can cost effectively grow to accommodate customers.

Folks early in their career can have a hard time seeing how a system they are building will behave when there are 20x or 1000x more users.  This can cause the system to lack the knobs and dials you need in order to grow.  Fixing those mistakes is costly, often requiring re-architecture or a complete rewrite in some cases.  The last thing any business leader wants to hear is that we can't take on more customers until some key component of the product is rewritten.

Another mistake often made is that the scaling approach is over engineered and costs too much to run before we reach those growth goals.  It's one thing to take advantage of economies of scale, but if you can't run the system efficiently with a small number of customers then you need to go back to the whiteboard and keep thinking.

## Scaling Product Development
So you can build a system that grows predictably when you add thousands of new customers, but what happens when you add hundreds of developers?

The architectures of our products tend to follow the communication structure of the people who built it, [according to Conway](https://en.wikipedia.org/wiki/Conway%27s_law).  A good product development leader will use that to their advantage, and design systems that allow you to add teams to increase overall velocity without adding friction.  This is one of my favorite things about service oriented architectures, these days called Microservices.

In legacy monolithic systems, it is very difficult for lots of developers to contribute at the same time.  That's because there is so much interdependency between different components of the codebase.  In a monolith, there's no easy way to version those interfaces, so teams end up colliding with each other and spending a lot of time resolving conflicts in their changes.

![Cloud based enterprise architecture](/posts/2020/02/product-development-leadership/Enterprise Architecture.001.png "Cloud Based Enterprise Architecture")
However, when you build products on top of platforms which are made of independent services, you can add people to your product development organization and massively parallelize your efforts without those conflicts.  Best practices like [semantic versioning](https://semver.org/), [contract testing](https://docs.pact.io/), continuous deployment, and feature flagging all come together to allow independent teams to make very rapid progress with their services without stepping on each other.

Platform based architectures are also easier to scale from a usage perspective, because each of those components will grow at different rates.

## Quality
19 years ago during [my first job](https://eason.blog/posts/2020/02/my-first-job/) when I was teaching myself to code and building an order management system for a furniture factory, my Dad asked me how I knew that my code changes worked.  I replied, "I just ask Donna if it worked for her this time."  Donna sat right across the hall from me.

My Dad has been a wonderful mentor to me throughout my career.  I think what he was really asking about was what kinds of tools and process did I have in place to make sure I wasn't breaking something by accident as I made changes.  However, the heart of my response is the heart of quality:  Quality is delighting your customer.  It is not a lack of bugs, or the presence of test automation.  You cannot test quality into a system.  

There are a lot of companies out there selling services that are trying to help us get to the very place I was at in that small factory where all my users were right down the hall.  Pendo.io, UserVoice, WalkMe, and even companies like Honeycomb.io and LaunchDarkly are all trying to help us do that at massive scale.  Because we have so many customers now, it's hard to just ask them if it "worked for you this time."  Instead we build the ability to ask that question into the system itself, and we make sure our teams understand that they all own quality together.  Give them the ability to ask the question, and make them accountable for the answer, and you will see a significant improvement in quality.  

Product development leaders have to intentionally build that culture of quality and ownership as they scale up their development efforts.  Anti-patterns like separate QA reporting structures, incredibly long bug backlogs, and a reliance on customers reporting problems are all signals that the general approach to quality is off.
