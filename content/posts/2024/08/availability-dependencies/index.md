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
I fondly remember early in my software writing journey when a web application was nothing more than PHP code and a MySQL database.  And that database didn't do anything but drive the one, single, beautifully simple PHP app which usually ran on one server in a closet somewhere.  It ain't like that anymore.

John Donne was one of my favorite poets when I was in high school. [The Flea](https://en.wikipedia.org/wiki/The_Flea_(poem)) was my favorite poem from him, but a line from [Devotions upon Emergent Occasions](https://en.wikipedia.org/wiki/Devotions_upon_Emergent_Occasions) has stood the test of time better: **"No man is an island."**

Similarly, no SaaS application is an island either.  Modern applications rest on top of many APIs, databases, and layers of shared infrastructure, and often rely on other user facing applications as well, all of which spider out in a web of dependencies that can be daunting to try and visualize.  Let's look at a simple example:
![image](/posts/2024/08/availability-dependencies/tekata-arch-basic.png)
Here we have a user facing web application called [Tekata.io](https://dojo.tekata.io) that allows a user to create Teams, define Skills for those teams, and get Insights about skill gaps on the teams.  The application has seven dependencies.  It relies on a few AWS services such as Cognito for authentication, S3 for storage, and several custom APIs that drive functionality related to Teams, Skills, and Insights.  Those APIs also depend on AWS services for database (RDS) and the compute that their logic runs in (Lambda).

# A practical example
If Tekata.io has a monthly availability goal of 99.9%, that means it can be down for 43 minutes and 28 seconds per month.  _(Shoutout to [Uptime.is](https://uptime.is/99.9) for this type of information, btw)_  The Tekata.io team may need to do some maintenance work that requires downtime, they may deploy a bug that breaks the application and takes it down until they can fix it, or - and this is often the case - one of those many dependencies may go down.  All of these things affect the availability of Tekata.io.  Let's focus on the dependencies.

## Dependency uptime equation
We can use an equation to express the relationship between the uptime of your application to the uptime of its dependencies.  It looks like this:

    Givens:
    A = application uptime
    U = dependency uptime
    N = number of dependencies

{{< raw >}}
\[ A = U^N \]
{{< /raw >}}

So for our example architecture of Tekata.io, we would get:

{{< raw >}}
\[ 0.999 = 0.9999^7 \]
{{< /raw >}}
    
{{<smallimg src="/posts/2024/08/availability-dependencies/office-space-2.jpeg" alt="Office space screenshot" smartfloat="right" width="250px">}}Meaning, each dependency has to have an uptime of [99.99%](https://uptime.is/99.99) in order for Tekata.io to have a chance of hitting it's goal.  That's only 4 minutes and 21 seconds per month - much less than Tekata.io itself.  _And that doesn't allow for maintenance or unplanned outages_ - so you'll have to go even higher to account for that.  Meaning, this equation gives you the _bare minimum_ uptime for dependencies and you'll likely need to adjust it higher based on your needs.  Some people like to do more than the minimum, and we encourage that.

## Finding the required uptime of your dependencies
Now we get to use algebra to rework the equation to find the dependency uptime requirement.  When you have a target uptime for your application in mind, your unknown variable is `U` so you'll have to take the `Nth` root of `A`.  My high school math teacher would be so proud of me right now.  It works like this:

{{< raw >}}
\[ 
\begin{aligned}
&U = A^{1/N} \\ 
&U = 0.999^{1/7} \\
&U = 0.999^{0.143} \\
&U = 0.9999
\end{aligned}
\]
{{< /raw >}}

You can use the formula in the other direction as well, to find out what your best case uptime is given the uptime of your dependencies.  For example, if the average uptime of those dependencies is actually 99.5%, then the best case scenario uptime of Tekata.io would be [**96.6%**](https://uptime.is/96.6).  That is an eye watering 24 hours, 37 minutes, and 57 seconds per month.  Goodbye, customers

{{< raw >}}
\[
\begin{aligned}
&A = U^N \\
&A = 0.995^7 \\
&A = 0.9655 
\end{aligned}
\]
{{< /raw >}}
That's pretty scary.  Because the relationship between an application and its dependencies relies on an exponent, the uptime impact of dependencies is exponential as well - a small change in uptime of dependencies will have an outsized impact on applications that rely on them.

## Handy Dandy Calculator (because why not?)
Have some fun playing with the calculator below.  Just insert your number of dependencies and desired application uptime and it will display the required uptime of those dependencies.

{{< raw >}}
    <style>
        .widget {
            font-family: Arial, sans-serif;
            max-width: 300px;
            margin: 20px auto;
            padding: 20px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        .input-group {
            margin-bottom: 10px;
        }
        label {
            display: block;
            margin-bottom: 5px;
        }
        input {
            width: 100%;
            padding: 5px;
            box-sizing: border-box;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
        }
        .error {
            color: red;
            font-size: 0.8em;
            margin-top: 5px;
        }
    </style>

    <div class="widget">
        <div class="input-group">
            <label for="dependencies">Number of Dependencies (0-5000):</label>
            <input type="number" id="dependencies" min="0" max="5000">
            <div id="dependenciesError" class="error"></div>
        </div>
        <div class="input-group">
            <label for="uptime">Application Uptime Target (0-100):</label>
            <input type="number" id="uptime" min="0" max="100" step="0.01">
            <div id="uptimeError" class="error"></div>
        </div>
        <div id="result"></div>
    </div>

    <script>
        const dependenciesInput = document.getElementById('dependencies');
        const uptimeInput = document.getElementById('uptime');
        const resultDiv = document.getElementById('result');
        const dependenciesError = document.getElementById('dependenciesError');
        const uptimeError = document.getElementById('uptimeError');

        function validateInputs() {
            let isValid = true;
            const dependencies = parseInt(dependenciesInput.value);
            const uptime = parseFloat(uptimeInput.value);

            dependenciesError.textContent = '';
            uptimeError.textContent = '';

            if (isNaN(dependencies) || dependencies < 0 || dependencies > 5000) {
                dependenciesError.textContent = 'Please enter a number between 0 and 5000.';
                isValid = false;
            }

            if (isNaN(uptime) || uptime < 0 || uptime > 100) {
                uptimeError.textContent = 'Please enter a number between 0 and 100.';
                isValid = false;
            }

            return isValid;
        }

        function calculateUptimeRequirement() {
            if (!validateInputs()) {
                resultDiv.textContent = '';
                return;
            }

            const N = parseInt(dependenciesInput.value);
            const A = parseFloat(uptimeInput.value) / 100; // Convert percentage to decimal

            if (N === 0) {
                resultDiv.textContent = 'Dependency Uptime Requirement: N/A (No dependencies)';
                return;
            }

            const U = Math.pow(A, 1 / N) * 100; // Convert back to percentage
            resultDiv.textContent = `Dependency Uptime Requirement: ${U.toFixed(4)}%`;
        }

        dependenciesInput.addEventListener('input', calculateUptimeRequirement);
        uptimeInput.addEventListener('input', calculateUptimeRequirement);
    </script>
    {{< /raw >}}

# Conclusion
We're keeping things very simple here.  In reality you could break the equation up into multiple levels to capture the nesting nature of Tekata.io's reliance on RDS and Lambda.  When you do that it drives their uptime up even higher.  However, that math gets more complicated and I'm not sure that it really changes the numbers enough to make it worth the effort.  If any of you reading this are interested in that level of detail let me know and I'll do a follow up on it.

My goal in sharing this is to give application owners another tool to use as they engage with the owners of all their dependencies so that you can work together more effectively.  It may turn out that the SLO of 99.9999% for your application isn't possible, or is economically untenable.  Or you may have to re-architect your application to make sure you're relying on dependencies that can meet your uptime needs.  