---
title: "Planning for Failure"
date: 2025-11-04T15:00:00-04:00
description: "Technical teams often plan system changes based on how things are supposed to work and don't account for how things will break.  This post explores how that plays out and how we might adjust our language to address the problem."
displayInMenu: false
featuredImage: "/posts/2025/11/when-it-breaks/gears.png"
featuredImageDescription: ""
categories: ["devops"]
draft: false
---
"I understand how the system is supposed to work, but how is it supposed to break?"

During a conversation with one of our solution engineers recently it came up that too often engineers hyperfocus on the happy path.  We design systems based on how they are supposed to work.  I think we also need to design systems around how they are supposed to break.

This principle is not just for system architecture, it applies just as much to devops and deploying changes to production.  Our release systems often only account for when things go right.  We develop plans for sequencing changes to systems and databases, and don't develop plans for how to undo those things or deal with failures in those changes.  Also, consider the implications for Agentic AI, where we will have autonomous systems making changes to customer records or handling complex workflows.  How will those break?  Will we even know?

## Software architecture
Event driven architectures have been around a while.  They sit behind most of the "real time" large scale systems you use every day.  Engineers love them, because they allow us to distribute both the workload and logical complexity of high throughput systems.  It also allows us to create a protective buffer between user behavior and our precious infrastructure.  The following is a true story of how this can go sideways.

Imagine a system that takes in examination data from hospitals.  Each exam is large, it has raw images and text data about the patient, tests being done, etc.  You might use a queue in a case like this, so when a hospital uploads an exam it goes first into the queue as that only takes a split second to do.  Then another system of workers is setup to read the exams out of the queue in the order they come in, processing the images and data and making them available to the hospital portal so doctors can look at it.  Most of the time there's only a few seconds of lag between when an exam comes in and when it starts getting processed.

During really busy times when hospitals are uploading lots of exams at once the queue might back up and it takes several minutes for an exam to finish processing.  If this happens regularly, you can use the power of "the cloud" to add workers automatically and speed things up during busy times.  Normally this all works great and your hospital clients are fine waiting worst case 5 minutes for an exam.

But then something bad happens.  The network connection between your queue and your processing system goes down.  It's a busy time of day, so quickly exams pile up in the queue.  Before you know it, there's 10,000 exams waiting.  That's 10k hurt and sick people waiting on their doc to figure out what's wrong.  As the operations engineer you know this is bad, so you get the network fixed and spin up as many processing nodes as you can. 

But you notice that adding workers isn't speeding things up.  In fact, now it's going slower.  When there were 25 workers the system processed an exam in 15 seconds.  With 50 workers it is now taking 45 seconds.  The system is slowing down much more than the additional workers are speeding it up.  When you look at all the moving parts, you realize now that every worker has to make a connection to the same database, and at 50 workers the database starts to slow way down.  You've never run into this situation before, so you're not sure how to fix it.

Then the phone rings.  It's a hospital asking about an exam that's been waiting 20 minutes.  There's a trauma patient in the ER that may need surgery but the doctors don't want to go in without seeing the exam images first.  Is there any way to speed up their exam?

No, because you don't have a special "fast lane" queue, you just have one.  And there's no way to search the queue for that exam and move it up - the queue only knows how to process the next exam in the order they came in.  You can't even tell the hospital how long it's going to take.  This is what we in the industry call a _very bad day_.

## Release systems
In large companies it is common that software systems are deeply integrated.  Customer records are used across many different systems, for example.  A change to how customer records work would impact several systems at once.  I've seen many examples of teams approaching this by carefully planning the release process, rehearsing it, and hoping to god everything goes right on release night.  But what if it doesn't?

That type of approach is called a "rolling deployment" because you have to sequence system changes in a particular order for it all to work.  If one of those deployments fail, they could just unwind the whole thing one system at a time.  It's tedious, but possible.  Or is it?

Without fail, every company I've worked at that used this approach ran into release failures that required a "fix forward" approach because, inevitably, one of the systems in the chain couldn't roll back their changes on release night.  Sometimes they'll say it's just less risky to fix forward, or some other nonsense, but the bottom line is that when it came time to really do the rollback, they didn't.

The result is often dozens or hundreds of people staying up all night waiting for someone to patch a system issue so the release could continue.  It's a miserable experience for everyone involved.  Then all those tired people have to spend the morning reacting to whatever issues come up when customers start using the new system changes.  

## Why is this so hard?
I could probably write a book about this principle because there's so many examples of how it plays out.  Why are humans so susceptible to it?  As is usually the case, I think it comes down to incentive.

When a product team is testing new features, what do they do?  They design a set of test cases that exercise all the different workflows that users need to execute and make sure they all work as expected.  Hopefully, they look at production metrics and figure out what peak usage might look like, then do a load and performance test to make sure the system will handle some multiple of that number.  All these things are called positive test cases.  Once they all pass we think things are ready to go.  There's a milestone on the calendar called "testing complete" that all this has to be finished by.

When some enthusiastic engineer starts going on about an edge case failure possibility, and proposing a different kind of test where we break some part of the infrastructure to see what happens, these ideas are shot down most of the time.  Why?  Because the time and cost of that test is high, the potential of that happening is low, and we don't have time to do it before the testing complete milestone date.  I actually think this is the right call most of the time, because this is way too late in the process.

Instead, what we should be doing is designing for failure from the start.  When you're implementing a queue, you don't wait until final verification to consider what will happen if there's 10k items in the queue.  You have to think about those real world situations much earlier.  That's why it's so critical that software engineers deeply understand the customers and how the system will be used.  And we need to make sure that product leaders are rewarded for thinking about the ways something might go wrong.

Maybe we could change our vocabulary to support this shift.  Instead of having a milestone called "code complete," call that first one "happy path working."  Then explicitly set another milestone a month later called "failure cases complete" where teams will list out the different ways they think the system could break, and show how they designed for those cases.  I doubt every system change needs this, but for anything significant this could help teams understand that they are not just being asked to make the happy path work, but to build a more robust and failure resistant system.

I'd love to hear examples of how you've approached incentivizing teams to account for failure cases.  If you have fun examples of these types of failures those are always fun to read as well!