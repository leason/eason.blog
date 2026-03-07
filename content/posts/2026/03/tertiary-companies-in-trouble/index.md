---
title: "Economics of Tertiary Service Providers"
date: 2026-03-07T08:00:00-05:00
description: "SaaS companies that profit by providing services that were slightly too annoying or expensive to build are in real trouble.  This has major implications for Private Equity."
displayInMenu: false
featuredImage: "/posts/2026/03/tertiary-companies-in-trouble/private-equity-pyramid.png"
featuredImageDescription: "A pyramid representation of how private equity holds up many technology SaaS companies"
categories: ["ai"]
draft: false
---
For decades the debate over "Buy vs Build" has raged.  C-level leaders have constantly pushed to make sure their company is only building technology that truly differentiates their firm and adds unique value.  Don't build a capability you can buy unless you really have to.

That has made good sense, because the cost of building and maintaining a technical system has, historically, not been small. You should be focusing your investments on things that give you an edge. This idea was founded on a simple economic model based on these variables:

**Build Variables**
- Initial development cost
- Maintenance cost
- Opportunity cost (what could we be doing with these development cycles instead?)
- Hidden costs (security compliance, scope creep, etc)

**Buy Variables**
- License fees
- Integration costs
- Consulting fees

You would take these variables, model it out over 5 years, and compare them to understand your Total Cost of Ownership (TCO).  Often, Buy would win because the opportunity cost was huge.  But opportunity cost is directly tied to initial development cost, and AI changes both dramatically.

## Anecdotal case study
I've been building an app to help my wife plan and manage the Yoga classes she teaches.  Don't fret, I'll share a lot more about that soon.  I have some pilot users, and getting feedback from them is vital.  Usually I'd look to a provider like Pendo, UserVoice, or WalkMe to see if they had a free tier I could mooch off of.  But in a world where I have a brilliant coder who can produce a week's worth of code in an evening, why bother?

I wrote up a quick description of what I wanted and in about 20 minutes I had an integrated user feedback panel.  It works incredibly well.  It automatically grabs a screenshot, lets the user mark it up with a virtual pen or highlighter, add comments, and submit.  It takes seconds to leave visually supported feedback.

In my admin panel I now see a list of all un-reviewed feedback.  I can leave my own comments, then set it to "Accepted" or "Rejected."  Accepted feedback then gets analyzed by an AI agent.  It checks to see if it's a duplicate.  If yes, it links it to the existing github issue.  If not it creates the issue then links it.

Soon, and with minimal additional effort, I'll have a completely automated process that implements those suggests, writes release notes, and even lets users know when their feedback got used.

Again, I built all that in *a couple of hours.*  It takes little to no additional effort to maintain that system.  There is almost no opportunity cost.

## The implications
There are many companies offering services similar to what I built.  I could mimic the rest of their functionality in an hour or two.

Pendo currently has a free tier for up to 500 monthly users, which would have been fine for me.  They don't publish pricing after that.  The internet says they start around $16k/year once you go beyond free, which would very much have *not* been fine for me.

UserVoice starts at $16,000/year.

WalkMe doesn't publish pricing.  The internet says they start at $9k/year.

UserPilot starts at $300/month.

AppCues starts at $750/month.

Whatfix starts at $25,000/year.

Gainsight doesn't publish pricing, but the internet says they start at $500/month.

**I cannot imagine why any reasonable company who can deploy agentic coding would pay for these types of services in the near future.**

There are thousands of similar, tertiary services companies.  They were profitable because of the old Build vs Buy math said you should pay them, but that is changing rapidly.  These companies will start to struggle with renewals, forcing them to lower prices.  Many of them won't survive at all.  These conditions will force them to downsize.  This scenario is played out in the fun [2028 Global Intelligence Crisis](https://www.citriniresearch.com/p/2028gic) thought experiment.  

## Private Equity
Pendo, UserVoice, WalkMe, Appcues, Whatfix, and Gainsight all have something else in common.  They are funded and owned by private investors, like the vast majority of similar SaaS services companies.  Big firms like Blackrock pool these types of investments into a fund, and people can buy-in.  This is one of several types of "alternative investments" which are just ways to invest your money other than the stock market.  Private Equity (PE) funds were worth over $4.4 trillion way back in 2021.[^1] 

A PE fund is made up of a group of similar companies.  Investors get to buy in to these funds based on what they want to be exposed to. There might be a fund for automotive services (car washes, etc), or a fund for technology SaaS companies like the one we've been talking about.  When market conditions change, and enough of the companies that make up a fund start to struggle, the fund can lose money, because the investors can't recover the money they put in to help those companies grow and get them ready to get bought by another investor or go public.

So when Blackrock, one of the largest PE players, [announced this week they were freezing withdrawals from their PE funds](https://www.reuters.com/business/blackrock-limits-withdrawals-private-credit-fund-redemptions-mount-2026-03-06/), it rightfully raised eyebrows.  This means that investors were trying to exercise their right to withdraw their money from funds they bought into enough that it put the underlying companies relying on those funds at risk.  Those companies need that money to make payroll, pay their bills, and market their services to get new customers.

You see, unlike the regular stock market where an investor can sell the stock they own and get their money back out whenever they want, alternative investments like PE have a lot of fine print.  That fine print restricts how much of your money you can take back out and how often you can do that, and it gives the fund manager (like Blackrock) a lot of control to make arbitrary decisions like they just did.  I've heard stories of real estate oriented investments that take years to liquidate.

The thing is, I'd be surprised if the bankruptcy rate of the underlying assets in these PE firms was actually higher yet.  We haven't had time to see the effect I'm describing take place.  After all, most of these SaaS companies make their money off of contracts that renew annually. I think what Blackrock is seeing is mostly speculative at this point.  Nobody wants to be left holding the PE bag like many firms were when the mortgage industry crashed.

## The bottom line
The ripple effects of AI are just beginning. People worry about big firms laying off software engineers, but my hunch is that most of what we've seen so far is just companies cutting back and labelling it as AI related because it's convenient. Even this move by Blackrock to slow PE liquidation feels too early to be based on actually collapsing sales numbers. The real impacts to the economy haven't really started yet.


[^1]: https://www.aft.org/sites/default/files/media/2021/private-equity-report-2021.pdf