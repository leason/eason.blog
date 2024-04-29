---
title: "Test Automation Quality - Who watches the watchmen?"
date: 2020-04-03T05:00:00-04:00
description: "Getting real about the value of test automation and the quality of that code"
displayInMenu: false
featuredImage: "/posts/2020/04/unit-test-quality/watchmen.jpg"
categories: ["devops"]
draft: false
---
In _Watchmen_, Alan Moore's incredible graphic novel, a wave of resentment against the city's superheroes drives people to start writing this question on many of the buildings: Who Watches the Watchmen?**

Here's the theory behind automated tests: they improve overall quality because they serve as living documentation of the intended behavior of the source code, and they catch unintended changes to that behavior before impacting other developers, teams, or customers.

However, given that unit tests bloat the amount of code in a project by 2-4x how do we make sure that they are of a high quality themselves?  What if the tests aren't actually doing either of those things that make them valuable?  If the tests are there to improve the quality of the system, who's checking the quality of the tests?  Who's watching the watchmen?

## Code Coverage
The most popular metric for unit test quality has been Code Coverage.  This looks at the number of lines of source code that get executed while running the unit tests VS the total number of lines of source code.  Higher means that more of the source code is run while executing the test.  

The problem is that while low coverage indicates untested code, high coverage does not indicate quality tests.  [Fowler does a good job of explaining that in more detail](https://martinfowler.com/bliki/TestCoverage.html).

At one company I studied, **60% of the test cases I looked at had zero assertions, but the code coverage averaged 70%**.  Those test cases add almost **no value** at all; they are just bloat in the codebase that future developers have to deal with.  What's a better way to measure test quality?

There's two ways to look at unit test quality I've come to trust: **mutation test coverage** and the **Assert to Invoke** ratio.

## Mutation Testing
[Mutation testing](https://en.wikipedia.org/wiki/Mutation_testing) is an automated system that alters the source code and re-runs the unit tests.  There are a myriad of frameworks and libraries for doing this in just about every major language.  [Here's a good blog post on doing it in .Net](https://opensource.com/article/19/9/mutation-testing-example-definition). I've used [PiTest](https://pitest.org/) for Java, and [MutMut](https://pypi.org/project/mutmut/) and [PyMut](https://pypi.org/project/pymut/) for Python.  There is a difference in outcomes and reporting capability from one library to another, so I'd encourage you to try a few out and see which one works best for your needs.

Mutation testing simulates a developer making an unintentional change to the source, which unit tests should catch.  The score you get is a ratio of the number of mutations that were caught by unit tests VS the total number of mutations tested.  You want a high score, just like with code coverage.  The difference is that now our score is actually related to how well the tests work.

After doing a lot of analysis, my feeling is that mutation testing is a great tool to use when learning how to write good unit tests, but probably won't be a good way to measure broad unit test quality due to the amount of time it takes to run and the amount of configuration needed to tune the tests.  I see mutation testing somewhat like Test Driven Development.  I would encourage individual teams to adopt mutation testing as a way to internally evaluate their unit testing capability.  However, if you are trying to drive a broad improvement across lots of products and teams, it may be too heavy of a lift to put it in place as a quality gate.

## Assert to Invoke
A much more interesting and efficient metric for broad scale analysis, and a better candidate for a new quality gate, is the ratio of Assertions to Invocations.  [Here is a very in depth paper that examines several metrics for unit testing](https://jserd.springeropen.com/articles/10.1186/s40411-014-0014-6).  The TL;DR; of that paper is that if you look at both Code Coverage and Assert to Invoke, you're capturing the most important things about the unit tests because those two metrics aggregate all the other more granular metrics in a simpler method.

To explain: in a unit test, you will invoke methods in the source code and then make assertions about what the results of those methods should be.  If the ratio is low, then the tests are not asserting much about how the methods behave.  This is a much better indicator of the thoroughness and quality of the tests than just measuring the code coverage percentage.

By way of example: in the source code for [Tekata.io](https://tekata.io)'s skill gap analysis tool, the code coverage was 85%, the Assert to Invoke was 94%, and the mutation testing score was 65%.  After looking at these metrics across a lot of projects lately, I really feel like an Assert to Invoke of less than 80% should be considered a bad smell and be looked into.  Obviously that needs to be tested more in the real world, but it's a baseline I'm going to adopt.

## Next Steps
The biggest challenge is actually getting the Assert to Invoke stat.  Most unit testing frameworks are not exposing these numbers yet.  In order to do this analysis I had to write some creative regex searches (I know, I know).  Some languages work better for that than others.  I'd love to see jUnit and PyTest actually gather these stats so we can be more accurate.  I'm also interested in writing a SonarQube plugin that could track and put quality gates in place for Assert to Invoke.  If someone wants to team up to do that, let me know.

** *Trivia fun: This phrase comes from [Juvenal's Satires](https://en.wikipedia.org/wiki/Quis_custodiet_ipsos_custodes%3F) written in the 2nd century.  He posed the question, "Quis custodiet ipsos custodes" or "Who will guard the guards themselves?"*
