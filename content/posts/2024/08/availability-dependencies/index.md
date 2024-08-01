---
title: "Application Availability Depends on Dependencies"
date: 2024-08-01T11:00:00-04:00
description: "No SaaS application is an island"
displayInMenu: false
featuredImage: "/posts/2024/08/availability-dependencies/islandprogram.webp"
featuredImageDescription: ""
categories: ["devops"]
draft: false
---
I fondly remember the days when a web application was nothing more than PHP code and a MySQL database.  And that database didn't do anything but drive the one, singl

John Donne was one of my favorite poets when I was in high school. [The Flea](https://en.wikipedia.org/wiki/The_Flea_(poem)) was my favorite poem from him, but a line from [Devotions upon Emergent Occasions](https://en.wikipedia.org/wiki/Devotions_upon_Emergent_Occasions) has stood the test of time better: **"No man is an island."**

Similarly, no SaaS application is an island either.  Modern applications rest on top of many APIs, databases, and layers of shared infrastructure, and often rely on other user facing applications as well, all of which spider out in a web of dependencies that can be daunting to try and visualize.  Let's look at a simple example:
![image](/posts/2024/08/availability-dependencies/tekata-arch-basic.png)
Here we have a user facing web application called [Tekata.io](https://dojo.tekata.io) that allows a user to create Teams, define Skills for those teams, and get Insights about skill gaps on the teams.  The application has seven dependencies.  It relies on a few AWS services such as Cognito for authentication, S3 for storage, and several custom APIs that drive functionality related to Teams, Skills, and Insights.  Those APIs also depend on AWS services for database (RDS) and the container that their logic runs in (Lambda).

# A practical example
If Tekata.io has a monthly availability goal of 99.9%, that means it can be down for 43 minutes and 28 seconds per month.  _(Shoutout to [Uptime.is](https://uptime.is/99.9) for this type of information, btw)_  The Tekata.io team may need to do some maintenance work that requires downtime, they may deploy a bug that breaks the application and takes it down until they can fix it, or - and this is often the case - one of those many dependencies may go down.  All of these things affect the availability of Tekata.io.  Let's focus on the dependencies.

## Dependency uptime equation
We can use an equation to express the relationship between the uptime of dependencies to the uptime of the application.  It looks like this:

    Givens:
    A = application uptime
    U = dependency uptime
    N = number of dependencies

{{< raw >}}
\[ A = U^N \]
{{< /raw >}}

So for our example architecture, we would get:

{{< raw >}}
\[ 0.999 = 0.9999^7 \]
{{< /raw >}}
    
Meaning, each dependency has to have an uptime of [99.99%](https://uptime.is/99.99) in order for Tekata.io to have a chance of hitting it's goal.  That's only 4 minutes and 21 seconds per month - much less than Tekata.io itself.  _And that doesn't allow for maintenance or unplanned outages_ - so you'll have to go even higher to account for that.  Meaning, this equation gives you the bare minimum uptime for dependencies and you'll likely need to adjust it higher based on your needs.

## Finding the required uptime of your dependencies
Now we get to use algebra to rework the equation to find the dependency uptime requirement.  When your unknown variable is `U` you'll have to take the `Nth` root of `A`.  My high school math teacher would be so proud of me right now.  It works like this:

{{< raw >}}
\[ 
\begin{aligned}
&U = A^{1/N} \\ 
&U = 0.999^{1/7} \\
&U = 0.999^{0.143} \\
&U = 0.99985
\end{aligned}
\]
{{< /raw >}}

You can use the formula in the other direction as well, to find out what your best case uptime is given the uptime of your dependencies.  For example, if the average uptime of those dependencies is actually 99.5%, then the best case scenario uptime of Tekata.io would be **96.6%**.

{{< raw >}}
\[
\begin{aligned}
&A = U^N \\
&A = 0.995^7 \\
&A = 0.9655 
\end{aligned}
\]
{{< /raw >}}
Yikes - that's pretty scary.  Because we're using exponents that means the uptime impact of dependencies is exponential as well - a small change in uptime of a dependency will have an outsized impact on the applications that rely on it.

# Conclusion
We're keeping things very simple here.  In reality you could break the equation up into multiple levels to capture the nesting nature of Tekata.io's reliance on RDS and Lambda.  When you do that it drives their uptime up even higher.  However, that math gets more complicated and I'm not sure that it really changes the numbers enough to make it worth the effort.  If any of you reading this are interested in that level of detail let me know and I'll do a follow up on it.

My goal in sharing this is to give application owners another tool to use as they engage with the owners of all their dependencies so that you can work together more effectively.  It may turn out that the SLO of 99.9999% for your application isn't possible, or is economically untenable.  Or you may have to re-architect your application to make sure you're relying on dependencies that can meet your uptime needs.  