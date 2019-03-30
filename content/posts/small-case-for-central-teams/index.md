---
title: "An economic case for central teams"
date: 2019-04-01T05:00:00-04:00
description: "Quantifying efficiency savings is possible if you understand the story behind how software teams work."
displayInMenu: false
featuredImage: "/posts/small-case-for-central-teams/dollars.jpg"
categories: ["leadership","agile"]
draft: true
---
Recently I saw someone on LinkedIn ask "When are central teams okay to have" and one of the responses from a very vocal agile coach was, "never."  This response bothered me, because intuitively I know that there is a time and place for central teams.  There's some very well known organizations that make heavy use of central teams, such as [Netflix](https://medium.com/netflix-techblog/full-cycle-developers-at-netflix-a08c31f83249).  

## Reference Table
| Item | Value |
|---|---|
| Annual Team Cost | $1,000,000.00 |
| Weekly Team Cost | $19,230.77 |
| Manual Service Startup Cost | $19,230.77 |
| Automated API Startup Cost | $3,846.15 |
| Automation Savings | $15,384.62 |
| Number of Teams | 25 |
| Number of Services | 100 |
| Total Potential Automation Savings | $1,538,461.54 |
| Total Service Investment | $1,923,076.92 |
| | |
| Cost for Product Team to create New API Automation Kit | $250,000.00 |
| Total Overhead for Teams to create APIs manually | $76,923.08 |
| Central Team Annual Headcount Cost | $300,000.00 |
| Central Team Automation Project Cost | $75,000.00 |

# An economic case for centralized teams
Suppose you have 25 teams that cost $1mm/year each to fund.  They are all embarking on a microservices re-architecture, so each team is going to end up creating 4 new services this year.  That's 100 new API's across the company.

Now suppose it takes one full week to get a new service started.  That's how long the team needs to decide how to structure the code, what framework to use, which database to use, where to host it, setup the build and deploy automation, create the Jira project, the documentation site, integrate all that automation with Slack or Teams, and setup the monitoring tools and alerting baselines.  In the beginning they take a couple weeks to do this, but by the end they've got it figured out and so it averages out to about one week per service.

That means that each new service has an overhead of $19,230.77.  For each team that total comes to $76,923.08 because they're building four services each.  If you could get all that done in one day, you'd reduce that overhead to $3,846.15.  That's a savings of $15,384.62 per service, or just over $60k total for the team.  

Now imagine that an engineer on one of those teams goes to her Product Owner and points out that the company is going to spend almost $2mm in manual overhead creating new API's ($19,230 * 100 services), but with an automation tool that does all that in one day we'd save the company over $1.5mm!  The PO would be excited, and then probably ask, "Ok, but what does the automation cost to build?"

Well, it's going to take three months to build it.  That's a hard cost of $250,000 for the business line.  Since that cost is greater than the $76k it will cost to create the services manually, how likely is it that one of those product lines is going to fund the automation tool?  I can tell you from experience, it's not likely at all.

# Org design drives optimization or sub-optimization
A central team of three engineers making $100k each would build that automation at a cost of around $75k.  The savings of that one project would fund the central team for over five years.

How you choose to setup your organization sends signals to every team member about what's important.  It can create helpful structures like the small central team in this example, who would deliver that automation tool and save the company a great deal of money.  Or your org structure can send a signal that federated decision making and pure capitalism is most important, and product teams will have no real choice but to continue to sub optimize for their individual needs.

# Some caveats
On a balance sheet, a public company just added three people as overhead and reduced their margins.  The impact to profitability and earnings is a trailing indicator of efficiency gains like this.  So I understand why a company would choose not to build out a small dedicated team even in the face of numbers like this.  What I'd advocate for instead in those cases is building a temporary team, sometimes called a Tiger team, to tackle a specific project.  Pick and choose a few good folks from across a few teams to minimize impact.  They will "inner source" the automation once it is working and let your community of engineers maintain it over time.  This approach has it's own drawbacks, but it's still far better than wasting millions in overhead.

Don't let idealism get in the way of being sensible and pragmatic.  If this example doesn't feel realistic to you, I'd love to hear from you on Twitter or in the comments.
