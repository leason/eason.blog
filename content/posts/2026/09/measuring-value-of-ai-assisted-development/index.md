---
title: "Measuring the Value of AI Assisted Software Development"
date: 2026-09-24T08:24:27-04:00
description: ""
displayInMenu: false
displayInList: true
featuredImage: ""
featuredImageDescription: ""
categories: []
draft: true
---
I want to share an approach I've been working on as I think it has value for some of my colleagues.  I also think it's relatively simple to implement and I'm hopeful some of you can try it out and give me some feedback on it so we can improve together.  I see many companies trying to measure how much faster AI is making our software development efforts, but I feel like that's a bit misguided.  Instead, I think we should be measuring how much more value it allows us to deliver.

# ROI as an increase in Value Delivery
The core idea is this: the business value of AI assisted development is that it will allow my business to create more incremental value than it costs in token spend.  Sounds simple enough, right?

If we were to express this idea mathmatically, it would look like this:

$$\frac{\Delta\ \text{Value Delivered}}{\Delta\ \text{AI Token Spend}} > 1$$

If we were to measure the change in token spend over some time period and then compare that against the change in how much value was delivered, we could easily compare these terms and see if our spend on tokens was justified.

Let's say we look at a single quarter.  We spent 60,000 dollars more on tokens than we did the quarter before, and the work we shipped in that window drove 480,000 dollars more in value:

$$\frac{\Delta\ \text{Value Delivered}}{\Delta\ \text{AI Token Spend}} = \frac{480{,}000}{60{,}000} = 8 > 1$$

Every additional dollar we put into tokens came back as eight.  That's an easy yes, and it's the kind of result that should make us want to spend more, not less.

Now the other direction.  Same 60,000 dollar increase in token spend, but this time the additional value delivered only came to 45,000 dollars:

$$\frac{\Delta\ \text{Value Delivered}}{\Delta\ \text{AI Token Spend}} = \frac{45{,}000}{60{,}000} = 0.75 < 1$$

Notice that value still went up.  If all we tracked was whether the number was growing, this would look like a win.  It isn't — we paid 60,000 dollars to generate 45,000 dollars, leaving us 15,000 dollars in the red.  Measuring velocity alone misses this.

# Measuring Value
The tricky thing about measuring the value of software is that it's often prohibitively difficult to do.  Many of us are building systems used by internal teams that are really difficult to connect to revenue dollars like the above examples.  It's often _theoretically_ possible to measure value, but we rarely do it consistently.  

Instead, we trust our product owners to use their judgement and direct teams towards the highest value work available each sprint.  Large initiatives might have adoption and value tied to them with metrics, but they are made up of dozens of sprints worth of individual releases, and those are where we see acceleration.  The result we associate with value lags.  What are we to do, then?

## The siren call of business value
I think there's a couple of options, and the right answer will differ for each company.  You could mature your process and require each Epic/Feature/Story to have a defined business value.  I've seen many companies talk about doing this and very few follow through.  It's a lot of work, and most of the time the numbers are fabricated.  

After all, things like efficiency improvement don't show up in the bottom line.  If I save 60k users with an average salary of $90k a year 30 minutes a day you could say the business value is $337.5 _million dollars_ a year, but that number will not show up on our quarterly filing anywhere.  I can't use that to buy anything.  If I give a bonus to the team that built that feature, the increased bonus payout shows up as an increase in variable compensation, compressing overall margin, but the gains they claimed are not there to offset it.  We assume those 30 minutes saved will be directed towards an activity that drives business benefit, or improves employee retention and satisfaction, but rarely prove it or track it.

## Features as a proxy
Instead of playing that game I propose we bifurcate what your software organiztion produces and what business outcomes that results in.  I know, I know.  This is a reversal of everything we've been trying to do the past 30 years.  Bear with me.  This has to do with aligning incentives.

Technology organization leaders are paid to make the machine that produces software as effective and efficient as possible.  There is a vast problems space they have to be deep experts on in order to do that.  My argument is that there is _also_ a vast problem space involved in connecting _what we build_ with _what that does to the business_ and trying to make those same technical leaders do both is asking too much.

So instead, constrain the problem space.  Simplify it.  Your head of software engineering needs to prove that the machine they run is getting better thanks to AI.  What we feed into that machine is not usually up to them.  They don't decide what enterprise efforts to take on.  They don't control budget allocations for transformation efforts.  So asking them to be responsible for measuring the value of those things is asking too much.

This is why I propose that we substitue Value for Features.  Assume that the Features we produce with the machine of software engineering represent Value.  Engineering leaders just focus on ensuring their machine produces more Features, in less time, with adequate quality, thanks to AI.  This changes our equation:

$$\frac{\Delta\ \text{Features Delivered}}{\Delta\ \text{AI Token Spend}} > 1$$

You could use Epics instead of Features, or any other unit of work for that matter.  While I think we all agree that Value matters more, the difficulty in measuring it consistently means trying to use it at this level of detail is too hard.  The advantage of this approach is that it is vastly simpler.

# The SDLC and what we should measure
The Software Delivery Life-Cycle (SDLC) contains all the activities from start to finish that it takes to deliver Features and Value to your users.  Most people outside of the industry, including the folks who sit on most company boards, imagine it looks like this:
<Chart1>

Most of the well-intentioned people I talk to who fear short term mass layoffs in software engineering see it this way.  In reality, the SDLC is much more complex.  The simplest version I'd feel comfortable with looks more like this:
<Chart 2>

Notice we are spending roughly the same proportion of time planning, executing, validating, deploying, and monitoring.  I'm not going to go into detail on all the things we do in these phases, but suffice to say they are very different acitivities with different experts involved at each step.  Where I think a lot of companies are today looks like this:
<Chart 3>

Note that planning and execution have compressed some, but validation is larger than before.  Reviewing pull requests, manual testing, revising specs, etc, are all consuming more time than they did before.  Overall we're not really going much faster, so our equation would likely yield < 0.  When we are successful at improving the SDLC across all constraints and our equation starts showing > 1, it will look like this:
<Chart 4>

## Output Metrics
Your primary output metrics will be Feature Throughput and Feature Cycle Time.  These tell you how many units of value are being produced and how long it typically takes to produce one of them.  Again, if you are going to use some other unit of work that's fine, but I think it should be fairly high level (ie, bigger than a Story).  Our goal is to improve how effeciently we produce these Features.

## Leading Indicators
I don't think there's some new set of things we should start measuring thanks to AI.  The same flow metrics we've been learning how to track for years apply here.  Your goal in what to measure should be to be able to visualize where the constraints in your process are moving as your teams adopt and mature their use of AI.  

That means that your adoption curve will end up looking like:
<Stacked Chart>

# Who is responsible for Value?
Now we can hold engineering leadership accountable for the things they can control.  Their individual performance is measurable and we can now budget for AI spend responsibly.  But this exposes a problem our organizations have wrestled with for a long time.  How do we know we are making good choices about what work to feed into the machine of software development?

Again, your organizations will likely solve this a bit differently.  Ultimately your CIO or CTO is accountable for this.