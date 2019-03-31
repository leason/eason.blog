---
title: "An economic case for central teams"
date: 2019-04-01T05:00:00-04:00
description: "Quantifying efficiency savings is possible if you understand the story behind how software teams work."
displayInMenu: false
featuredImage: "/posts/2019/04/small-case-for-central-teams/dollars.jpg"
categories: ["leadership","agile"]
draft: false
---
Recently I saw someone on LinkedIn ask "When are central teams okay to have" and one of the responses from a very vocal agile coach was, "never."  This response bothered me, because intuitively I know that there is a time and place for central teams.  There's some very well known organizations that make heavy use of central teams, such as [Netflix](https://medium.com/netflix-techblog/full-cycle-developers-at-netflix-a08c31f83249).  I decided to explore a hypothetical case through math to try and demonstrate when a central team is worth the organizational friction, and show why they don't get created more often.

# An economic case for centralized teams
Suppose you have 25 teams that cost $1mm/year each to fund.  They are all embarking on a microservices re-architecture, so each team is going to end up creating 4 new services this year.  That's 100 new API's across the company.

Now suppose it takes one full week to get a new service started.  That's how long the team needs to decide how to structure the code, what framework to use, which database to use, where to host it, set up the build and deploy automation, create the Jira project, the documentation site, integrate all that automation with Slack or Teams, and set up the monitoring tools and alerting baselines.  In the beginning they take a couple weeks to do this, but by the end they've got it figured out and so it averages out to about one week per service.

That means that each new service has an overhead of $19,230.77.  For each team that total comes to $76,923.08 because they're building four services each.  If you could get all that done in one day, you'd reduce that overhead to $3,846.15.  That's a savings of $15,384.62 per service, or just over $60k total for the team.  

Now imagine that an engineer on one of those teams goes to her Product Owner and points out that the company is going to spend almost $2mm in manual overhead creating new API's ($19,230 * 100 services), but with an automation tool that does all that in one day we'd save the company over $1.5mm!  The PO would be excited, and then probably ask, "Ok, but what does the automation tool cost to build?"

Well, it's going to take three months to build it.  That's a hard cost of $250,000 for the business line.  Since that cost is greater than the $76k it will cost to create the services manually, how likely is it that one of those product lines is going to fund the automation tool?  I can tell you from experience, it's not likely at all.

# Organizational design drives optimization... or sub-optimization
A central team of three engineers making $100k each would build that automation at a cost of around $75k.  The savings of that one project would fund the central team for over five years.

Organizational design sends signals to every team member about what's important.  It can create helpful structures like the small central team in this example, who would deliver that automation tool and save the company a great deal of money.  Or your org structure can send a signal that federated decision making and pure capitalism is most important, and product teams will have no real choice but to continue to sub optimize for their individual needs.

# Some caveats
On a balance sheet, a public company just added three people as overhead and reduced their margins.  The impact to profitability and earnings is a trailing indicator of efficiency gains like this.  So I understand why a company would choose not to build out a small dedicated team even in the face of numbers like this.  What I'd advocate for instead in those cases is building a temporary team, sometimes called a Tiger team, to tackle a specific project.  Pick and choose a few good folks from across a few teams to minimize impact.  They will "inner source" the automation once it is working and let your community of engineers maintain it over time.  They may also prove the ongoing value of a small team like this and leadership ends up deciding to fund it long term.  I see a lot of big, centrally funded ideas die on the vine because the creator can't figure out a low risk way to prove the value - stay nimble and don't be afraid to take some time to prove your idea at a small scale first.

So when it comes to central teams, don't let idealism get in the way of being sensible and pragmatic.  If this example doesn't feel realistic to you, I'd love to hear from you on Twitter or in the comments.


## Reference Table
Here's some of the facts and figures broken out in table format in case you wanted to follow along with the math

    | Item                | Value         | Notes                                                             |
    | Annual Team Cost    | $1,000,000    | What my agile leadership friends usually agree                    |
                                            on as a loose estimate for a cross functional team                |
    | Weekly Team Cost    | $19,230.77    | Divide row 1 by 52                                                |
    | Manual Service      | $19,230.77    | One week of work for the team                                     |
      Startup Cost        
    | Automated API       | $3,846.15     | One day of work for the team                                      |
      Startup Cost
    | Automation Savings  | $15,384.62    | Difference in one day vs one week of work                         |
    | Number of Teams     | 25            |                                                                   |
    | Number of Services  | 100           | Each team will create four services                               |
    | Total Potential     | $1,538,461.54 | Automation savings multiplied by number of services being created |
      Automation Savings
    | Total Service       | $1,923,076.92 | What you'll spend to create all 100 services without automation   |
      Investment
    | Cost for Product    | $250,000.00   | Three months of work for the cross functional team                |
      Team to create New
      API Automation Kit
    | Total Overhead for  | $76,923.08    | Manual service startup cost X 4 services                          |
      Teams to create APIs
      manually
    | Central Team Annual | $300,000      | Three engineers at 100k each                                      |
      Headcount Cost
    | Central Team        | $75,000       | Three months of work for the central team                         |
      Automation Project
      Cost
