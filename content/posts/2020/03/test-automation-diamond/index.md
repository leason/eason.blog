---
title: "The Test Automation Diamond"
date: 2020-03-12T05:00:00-04:00
description: "Revising test automation proportions in the post-API driven world."
displayInMenu: false
featuredImage: "/posts/2020/03/test-automation-diamond/test-automation-diamond.png"
categories: ["devops"]
draft: true
---
You've probably seen some version of the test automation _pyramid_ many times by now.  The story is that [Mike Cohn created it as far back as 2003](https://martinfowler.com/bliki/TestPyramid.html) as part of an agile conference.  At that time most companies were still creating monolithic architectures - meaning that all the source code for a product was wrapped up in one large repository.  In that context, the pyramid made a lot of sense.

However, over the past 15 years Service Oriented Architectures exploded in popularity eventually evolving into what we now call Microservice Architecture.  The idea is that you break up large code bases into smaller, more focused, stand-alone components called services.  These services communicate with each other but can be more easily maintained and re-written in isolation with much less risk to the overall system.  The problem is that popular ideology around test automation has not kept up with this evolution.  My guess is there's still a lot of disconnect between "QA" and development.  I still see the same test automation pyramid getting taught at conferences all over the US.  

**Test automation provides living documentation of the intended behavior of the code and system, and alerts developers quickly when intended functionality is changed unintentionally.**

But writing these tests is not cheap - they add source code that must be maintained.  They have to be carefully thought out lest they add more friction than they are worth.  To that end, skilled developers focus their test writing on the parts of the code that carry the most risk.  **In today's world of microservices, integration tests are more valuable than unit tests.**

Integration tests exercise the connection between services.  They should be code level tests, able to run in isolation (meaning they use mocks to represent the external service).  They still take longer to run than a unit test.  You should use [Pact.io](https://pact.io) or something like it to make these tests document and rely on contracts and catch changes in dependencies quickly and automatically.

[Netflix has over 700 microservices.](https://medium.com/refraction-tech-everything/how-netflix-works-the-hugely-simplified-complex-stuff-that-happens-every-time-you-hit-play-3a40c9be254b)  [Uber has over 3,000.](https://www.infoq.com/presentations/uber-microservices-distributed-tracing/)  In my experience integration tests in environments like this are essential.  There is much more risk in the relationships between services than within the services themselves.

### I'm proposing we start thinking of test automation proportions like a diamond, keeping the categories in the same order, but visually calling out that the bulk of our tests should be integration tests, not unit tests.  

An added benefit is that Pact.io style integration tests will ease semantic versioning of services.  This removes the need for cascading deployments, which are risky and require centrally managed change control and slow down overall development.

I really want to hear from you on whether you agree or not, and whether your experience lines up with mine.  Please drop me a line in the comments or on Twitter.
