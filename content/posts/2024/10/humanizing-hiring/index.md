---
title: "Humanizing Hiring"
date: 2024-10-17T11:00:00-04:00
description: "What is it like to search for a job or hire someone today, and why on earth are we tolerating this mess?  Why is it so hard to fix the job seeking and hiring process?  Plus you get to play with another fun calculator."
displayInMenu: false
featuredImage: "/posts/2024/10/humanizing-hiring/application-process.png"
featuredImageDescription: ""
categories: ["leadership","pandemic lessons","philosophy"]
draft: false
---
The current state of job seeking and hiring is terribly painful.  There is a huge imbalance in the time and emotional investment of a job seeker VS the system involved in hiring them.  From my vantage point this has gotten progressively worse over the last ten years, but the explosion of fully remote roles has rapidly accelerated the problem.  Frankly I think we are overdue for a disruption.

This post is not about whether remote roles are better, although personally I think firms that can make that model work have a competitive advantage when it comes to talent acquisition and retention.  That said, in a world where [fully remote jobs get 50% of all applications despite only comprising 20% of the available jobs](https://www.itpro.com/business-strategy/flexible-working/369452/linkedin-remote-job-demand-increases-opportunities-waning), we can't ignore the impact that shift is having on how we hire people.

A typical corporate job gets [100-250 applications per role posted](https://teamstage.io/job-interview-statistics/).  Remote roles will get 2-3x that many applicants.  It can take anywhere from 5 minutes to an hour to apply for a job, depending on how much time you spend customizing your resume, writing a cover letter, and dealing with duplicative forms during the application process.  Only 2-5% of those applicants will talk to a human being at the company they are applying to.  When you are submitting hundreds of applications before you talk to a person, the process can be incredibly dehumanizing and demoralizing.

![image](/posts/2024/10/humanizing-hiring/job-search-chart.png)
_source: https://www.reddit.com/r/dataisbeautiful/comments/b5sfbh/my_12month_job_search_as_a_recent_graduate_in/_

The /r/dataisbeautiful/ subreddit is [full of charts like that one](https://www.reddit.com/r/dataisbeautiful/search/?q=job&cId=50d98c60-6deb-4c04-b55e-9e4da391695a&iId=4d0940e1-956e-47d6-96f0-5434a56ce5bd).  Qualified people with more than adequate skills spending inordinate amounts of time submitting the same information over and over again.  And for every one they submit a little question hangs in their mind - will they contact me?  Only to hear nothing 73% of the time in that person's case.  It's mind boggling when I think about the scale of that considering there are almost 200,000 engineering related job openings each year according to the [US Bureau of Labor Statics](https://www.bls.gov/ooh/Architecture-and-Engineering/).

Yes, improved transparency to job applicants would help.  It's unforgivable in my mind that you don't at least send an automated email letting them know they didn't get selected for an interview.  But I think real disruption will go much farther than that.

# What would good look like?
We need a ground up rethinking with a human centered approach.  Embrace de-localization and the higher scale of the applicant pool.  Substantially lower time and effort to become an applicant.  Much better filtering criteria for hiring leaders.  Reset expectations for job seekers and provide better transparency about the entire process.  Start with the things that both sides actually filter opportunities on: compensation, benefits, purpose, and expectations.

For example, a job seeker might indicate things such as:
 - I want to make at least $90k per year.
 - I am okay trading some base compensation for RSUs.
 - 401k match is very important to me.
 - I am happy to work 35-50 hours per week.
 - I want to be challenged to learn new skills as part of my work.
 - I want to write code and I have proven proficiency in React, Python, and C#.
 - I do not aspire to be a people leader, I want to build things.
 - I like working on a team more than working solo on things.
 - I want to make healthcare better.
 - I want to work in an established, profitable company, rather than a startup.
 - I am legally qualified to work in the US.

You can see how a hiring leader might describe their ideal candidate similarly.  Like a credit card pre-approval, now I don't have to apply for a role - I just pick the ones from a list I want to raise my hand for that are already bi-directional matches.  I can become an eligible applicant to hundreds of jobs in the five minutes it used to take me to apply to one.

I don't have to wonder if I'm qualified, or if something inconsequential about my resume caused me to get filtered out by an applicant tracking system.  I can see which companies have had a human actually review my profile or project portfolio.  If they decline, I can see that.  When one of the companies I "applied" to starts interviewing people, I can see that too and the system can call out what parts of my profile differed from theirs.  Same as when they actually hire someone.  Companies that poorly describe what they are actually looking for are penalized with lower rankings and candidates will be less inclined to give them a chance.  Candidates who misrepresent themselves would likewise be penalized, a la Uber.

The system could also obfuscate elements of the applicant's information that could lead to unconscious bias such as their name and location information until it's relevant, such as during the interview itself.

Compare that experience and filtering effectiveness to the status quo of keyword matching in a resume.

# Why hasn't something like this been built?
A system like this could lower the time to fill a role dramatically.  Even for firms that require a background check, the system could allow applicants to complete that step once and have a validated check ready for all roles that need it.  One would think that lowering time to fill from 60 days to 15 would be really valuable, right?

There have been attempts to make things like Tender for hiring, but they haven't caught on.  Partly, I think, because the companies trying to build them just don't have the clout or resources to get enough critical mass in applicants and companies to get traction.  There's also complexity in the types of requirements a company has in regulated industries.  But I think the bigger obstacle is a bit more insidious and simple.  As always, it's about money.

Consider [POSIWID](https://en.wikipedia.org/wiki/The_purpose_of_a_system_is_what_it_does): the current system ruthlessly culls applicants and drags out the hiring process.  Why?  Because that is in the financial interest of the companies doing the hiring.

## Lag time in hiring impacts the bottom line positively
When it takes 60 days to fill an empty role, that is two months salary and benefits the company doesn't have to pay someone.  The total cost of an employee can be as high as 1.4x their salary thanks to taxes, benefits, etc.  Hiring managers complain about hiring lag time frequently, and yet their firms do very little to decrease it.  Because saving 16% of a full time person's cost is one way to recoup the cost they incur in backfilling them, especially when corporate culture pushes the team dealing with that empty seat to work extra to make up the slack.  Ultimately that lag time doesn't end up costing the company a lot of productivity.

Want to know just how much money this might be for your company?  Use the calculator below to see for yourself.  The bigger your company, the bigger the annual savings.

{{< raw >}}
    <div>
        <label for="averageSalary">Average Salary:</label>
        <input type="number" class="calc" id="averageSalary" value="145000" min="0" step="1000">
    </div>
    <div>
        <label for="daysToFill">Days to Fill:</label>
        <input type="number" class="calc" id="daysToFill" value="60" min="0" step="5">
    </div>
    <div>
        <label for="orgSize">Size of Technology Organization:</label>
        <input type="number" class="calc" id="orgSize" value="3000" min="0" step="500">
    </div>
    <div>
        <label for="turnoverRate">Turnover Rate (%):</label>
        <input type="number" class="calc" id="turnoverRate" value="13.2" min="0" max="100" step="0.1">
    </div>
    <div id="result"></div>
    <style>
        label {
            display: block;
            margin-top: 10px;
        }
        input.calc {
            width: 100%;
            padding: 5px;
            margin-top: 5px;
        }
        #result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
    
    <script>
        function calculateSavings() {
            const averageSalary = parseFloat(document.getElementById('averageSalary').value) || 0;
            const daysToFill = parseFloat(document.getElementById('daysToFill').value) || 0;
            const orgSize = parseFloat(document.getElementById('orgSize').value) || 0;
            const turnoverRate = parseFloat(document.getElementById('turnoverRate').value) || 0;

            const openPositions = orgSize * (turnoverRate / 100);
            const dailyCost = (averageSalary * 1.3) / 365;
            const annualSavings = openPositions * daysToFill * dailyCost;

            const roundedSavings = Math.round(annualSavings / 100) * 100;
            const formattedSavings = roundedSavings.toLocaleString('en-US', {
                style: 'currency',
                currency: 'USD',
                maximumFractionDigits: 0
            });

            document.getElementById('result').textContent = `Estimated Annual Savings: ${formattedSavings}`;
        }

        document.querySelectorAll('input').forEach(input => {
            input.addEventListener('input', calculateSavings);
        });

        calculateSavings();
    </script>
{{< /raw >}}

## Power dynamics of compensation
Another key issue is that the current system puts most of the power in compensation negotiation in the hands of the hiring company.  Because they defer that detail until the very end of the process, the candidate feels hard pressed to decline an offer at the low end of their acceptable range.  After all, at that point they've applied to hundreds of jobs, spent countless hours agonizing over their situation and prospects, finally got a call and made it through the interviews - am I really going to start all over just because the offer is $5k under what I wanted?  If a system _started_ with establishing an agreement about what compensation and benefits would be it takes away the hiring company's leverage to squeeze a bit and minimize what they have to pay someone.

And lest we think _that_ issue is not a big deal, consider that annual raises are not based on how equitably someone is paid to do their work - it's a percentage based on current salary.  That smaller start at the beginning leads to smaller raises and bonuses year over year.  Starting someone at $130k instead of $135k easily ends up saving the company almost $80k over ten years on that person.  If you can skim that across thousands of employees, it starts adding up to real money.  This is why people who stay at one company a long time are paid less than people who change jobs every few years - the big jumps happen between companies rather than by staying with the same one.

## Dead on arrival
Who is the buyer of a system like this?  Job seekers likely don't have an income stream and are going to be reluctant to pay for access to a system, plus that feels a bit predatory.  Historically, companies who are hiring have paid for services.  They pay firms like LinkedIn, Indeed, etc, to allow them to post their job openings and use their tools to review candidate info.  But these services don't cost all that much and they allow the firm to maintain their power dynamic and play the float like we've shown.  More than likely a platform like I'm describing would have to cost at least the same as what they already pay to existing platforms, and then it would end up raising operating costs by filling open roles faster.  I don't imagine that pitch going very well.  I can absolutely imagine a CFO working behind the scenes to quietly kill a deal with a firm trying to pitch this.

Now... I've never heard a CFO say anything to support that theory and the point of this thought exercise is not to demonize executives.  It's highly likely that the startups that have tried this so far just haven't executed well.  I simply want to offer up some thoughts I have not seen discussed much to explore the odd situation we are in.  It's not often that there is so much clear pain, seemingly obvious value to so many businesses, and so much time passing with no real improvement or change.  I'm a bit baffled.

# Who is actually getting disrupted?
We've established that if the customer for a new hiring model is the company doing the hiring, they likely won't buy since this would end up costing them more than the current system.  But the industry that would get disrupted the most are the recruiting firms.  After all, the kind of filtering and matching I'm describing is exactly what they do, just less efficiently and accurately, and using methods that are rife with bias.  Staffing and recruiting firms comprise a [$218 _billion_ dollar industry in the US alone](https://www.statista.com/statistics/873648/us-staffing-industry-market-size/).  They don't want a solution like the one I described to exist either.

# Change is happening, but it won't make things better
I am already seeing posts on social media claiming that they were subjected to a screening call by an AI based voice system.  There are AI tools that help [applicants speed up the application process](https://github.com/feder-cr/Auto_Jobs_Applier_AIHawk), creating customized versions of their resume's and writing cover letters for each job it applies to.  Applicant Tracking Systems are going to continue to adopt better and better AI models to hopefully improve how they filter candidates, but those are still based on a resume and cover letter that do not capture the key filtering points that matter most.  

None of those changes are innovative.  They don't speed up time to hire, and none of them humanize the process.  They are just incremental tweaks to a fundamentally broken system.  We need a ground up rewrite, folks.  For something to truly disrupt this space and make it better for job seekers and hiring managers, someone will have to declare open war on resumes and recruiting firms and figure out how to apply so much pressure that not even a CFO can resist it.

If any of you know of a company trying to revolutionize hiring, I'd really appreciate you letting me know.  I'm not on the job market but it would be something I'd love to keep a close eye on.  Plus I have so many friends who are currently getting brutalized by this process I'd love to suggest a different approach to them.  Their experiences are what inspired to me write all this up in the first place.