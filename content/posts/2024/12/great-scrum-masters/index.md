---
title: "What makes a great Scrum Master?"
date: 2024-12-17T11:00:00-04:00
description: "I've heard more variation in opinion on how to qualify a great scrum master than any other role.  It's time to get my thoughts on this role down on paper."
displayInMenu: false
featuredImage: "/posts/2024/12/averages-for-average-people/averages-suck.png"
featuredImageDescription: ""
categories: ["leadership","agile"]
draft: false
---
If you never hear complaints about your scrum masters, if teams are not changing up their process, and if you see mostly static numbers (or no numbers) related to quality and throughput.. then your scrum masters may not be doing their jobs well.

While I still maintain that the [Product Owner is the most challenging role](https://eason.blog/posts/role-of-the-po/) in modern software teams, the Scrum Master may be the most commonly misunderstood.  I can't count how often I've heard people from every level of an organization completely miss the point of the scrum master.  The role is commonly squeezed out of budgets and its absence justified by saying that the team is mature enough to do without.

There are a million articles about the tactical functions of the role.  I want to instead focus on the things that separate an excellent scrum master from one that simply checks those tactical boxes.  **The key point in all of this is going to be on _how_ the scrum master pushes the team to continuously improve even as they do their work.**

# Facilitating improvement
Consider two levels of how to help a team improve: "In the moment" VS higher level process evolution.  In either case, we want to stay focused on measurable improvement such as predictability, reduced carry-over work, improved quality, or better engagement.  While we could spend an entire post talking about metrics, here we're going to think deeply about the human behaviors often involved in realizing improvement.

## In the moment
<!-- Scrum masters shoulder the administrative burden of scheduling meetings, making sure they start and end on time, and, ideally, remain productive uses of time.  That means they're primarily responsible for ensuring everyone attending the meeting knows why they are there, and what the goal is.  I've had engineers complain to me that they didn't know what the point of the daily standup was.  My response was, "then don't go until your scrum master can explain that to you."  Having someone there with the wrong idea of the purpose is often worse than them not being there at all, and it is the scrum master's job to both recognize and resolve that problem. -->

Inside each of the ceremonies a team goes through, including standup meetings, backlog refinements, sprint demos, and retrospectives, the scrum master should be actively finding opportunities to help the team improve.  Let's digress into a little story to illustrate this idea.

### Susan the scrum master
Susan has always loved helping people.  Her dream of becoming a nurse got cut short thanks to a little shortfall in funding.  And, if she's being honest, the classes on anatomy were hard and the sight of blood still makes her queasy.  But after pivoting to a business degree she found a job in a technology company and ended up discovering the role of scrum master, and she's loved every minute of it.

She just got assigned to a newish team that's been together for about six months.  They're working on some tricky new features that have to tie together some of the company's old technology with new screens to help us land a big contract.  Honestly Susan has never understood the details of the technology all that well, but she can tell when someone is a good engineer and this team has a bunch of them, and they're all pretty stressed.

Today is the end of the sprint, and they're in her favorite ceremony: the retrospective.  This is where the team shares what they are learning and makes a plan for how to improve.  Susan's job is to tease all that out of them.  Engineers can be a moody, introverted bunch...

She's been watching videos on different techniques for running a retro and decided to try out a new icebreaker today.  The team seemed to enjoy it and it looks like it got them to loosen up a bit - the team is putting post-it notes on the white board under headings like "what went well" and "what should we try?"  

After everyone is done Susan helps encourage some conversation about the themes, and then the team votes for the one thing they want to work on improving next sprint.  She's pretty pleased that they decided to try and improve their predictability - this is something her broader group of scrum masters at the company have been getting encouraged to help their teams improve anyway.

#### Putting that into action
After a good weekend the team comes back to the office on Monday and plans out the next sprint.  Right away Susan has to step in.  The team is once again trying to commit to too many things.

"Guys, remember what we agreed to work on: predictability.  Every sprint for the past two months we've had some unexpected event come up that caused us to miss our commitment.  This is making it hard for the other teams to plan effectively.  Can we just put that last story as a stretch goal so that they know we may not get to it?"

The team reluctantly agrees to her suggestion.  Susan really admires their dedication, but sometimes their eyes are bigger than their stomachs when it comes to planning these sprints out and they need to get more realistic about what they can do.

The next day brings a refinement meeting.  The team has to continually look ahead at the work they'll do next sprint.  Making sure they have a couple of sprints worth of work broken down into enough detail helps make sure the way they do the work this sprint will transition smoothly into next sprint.  It also makes sure they can pull stories in quickly if they need to replan, and gives them enough time to do additional research if required.  Today the PO is talking about a new workflow that will have to touch some of that older technology the team hates dealing with.

"Okay team," the PO says, "anybody need more detail on the goal of this one?  No?  Okay, what do we think the estimate here needs to be?"  Engineers raise cards that Susan handed out at the start of the meeting to indicate how hard they think the work will be.  Most people have raised a 5, but one of the senior engineers has raised an 8.  The PO then says, "alright, looks like most people have voted 5 on this one, any objection to just going with that?  No?  Okay cool, let's move on then."

Susan interjects, "Hey hang on just a sec.  We all agreed we wanted to improve predictability, and one way we've gotten burned a few times is when a story turns out to be more complex than we thought - that starts right here when we're refining.  So before we move on, can we hear from the 8 and from one of the 5's to make sure we're considering this story fully before we commit to an estimate?"  The team then has a discussion, which turns into an argument.  

Turns out the lower estimates were trying to avoid doing any improvement to the old code, while the one higher vote was going to do some refactoring.  The engineers have been getting pushed by their leaders to leave that older code in a better state than they found it when the opportunity arises.  Ultimately Susan has to prod them back on topic a couple of times, but the team ends up settling on the higher estimate.

The following week, just five days before the sprint is going to end, the engineers are feeling some pressure.  Once again, a story they are working is turning out to be pretty hard.  One of the engineers working on it gives their update: "Okay well yesterday I working on this task to fix the database abstraction and I wasn't able to get it done. So this morning I'm going to wrap that up and then move on to the task I had for today which is to fix the frontend library that calls our API layer and make sure it passes the auth token correctly."  The team all nods in approval and looks at the next person up to give their update.  Once again, Susan has to intercede..

"Hang on folks - again, we all committed to improving predictability.  We have a situation here where a task was supposed to take one day, but it slipped.  Can we pull out some more detail here?  Was the task just harder than we thought it would be?  Did you get pulled into other work?  Is there some way for us to help get that unblocked?"  Turns out the engineer got a call from their manager who needed them to look into a production issue that affected an important customer.  The problem is that we have a whole team who is supposed to do that, but the manager just doesn't like dealing with them and going straight to an engineer on his team is easier.  Susan makes a note to talk to that manager today.  In the meantime, another engineer on the team actually finished a task faster than planned and can take on the frontend task this morning, helping the team stay on track.

## In the moment matters
Susan is a great scrum master.  She understands the struggles the team is having, and most importantly she recognizes how the little behaviors they have fallen into are leading to those struggles.  She is courageous enough to speak up, empathetic enough to not make herself an outsider, and focused enough on the shared goals and objectives to be trusted.  This is incredibly hard to do well.

I'd also argue that it is unrealistic to expect one of the engineers on the team to be able to fill that role.  Could they make sure meetings start on time?  Yes.  Would they provide that level of coaching and drive that kind of improvement?  Highly unlikely.

# Bigger picture improvement
A great scrum master studies more than just scrum process.  They are not afraid to think outside the boundaries of SAFe or scrum or kanban.  They recognize that these are all guidelines and ideas about how to solve the problem of delivering and improving consistently.  They don't just memorize process, they break down principles.  Let's go back to Susan for another example.

## No golden idols
Susan has picked up another team to help after her successes with the last one.  This team is a platform team: they are responsible for the framework that everyone else uses to build APIs as well as the shared infrastructure those APIs run on.  The team has been struggling to deliver consistently every two weeks.  They had tried making their sprints four weeks instead of two before Susan came over to help, but that didn't work.

After watching the team struggle through a couple of sprints, Susan sees a consistent pattern of the team getting interrupted during their sprints by high priority requests from their consumers.  It's either a critical bug in the framework, or some problem with the infrastructure that can't wait.  The team is working crazy hours to try and stay on track with their sprint plan, but it is clearly not sustainable.  Susan decides to talk to the team leader about some ideas.

"Has the team ever thought about trying to switch to a kanban process?"

"Well, one person brought it up and explained it and it sounded interesting, but we got shot down when we tried to do it because we're not allowed to skip the broader planning events."

"Let me dig into that and see what the details were," Susan replies.

After talking to her leader and fellow scrum masters, it turns out that there are ways to compromise and make sure the broader org gets what they need while still allowing the API team to adopt a kanban process.  Kanban will allow the team to work on tasks based on priority and smoothly intake high priority requests.  For interrupt driven teams, it is much better than scrum.

Over the next two weeks Susan teaches her team about kanban, works with the Jira group to get a new project set up for them, and then works with the broader planning group to make sure that milestones are tracked correctly from the new project.  She helps them create different lanes of work that reflect the size and priority of the types of tasks they do.  Finally, she helped create a new request form that was easier for their consumers to use to keep track of requests to the API team and monitor status.

## Determination, grit, and shared accountability
Once again Susan demonstrates what makes a great scrum master by showing us how her commitment to learning, her sense of responsibility to help her team, and her courage in confronting hard problems all come together.  I've seen so many scrum masters stay silent in situations like this because it's easier than dealing with the root issues.  The truth is, those are the people in these roles that lower the perceived value of scrum masters in our industry.

Many times it is a sense of self-imposed helplessness that stops the otherwise capable scrum master from being effective.  "They never listen to me," "We're too busy to try anything new," "I'm just a contractor - if I annoy them they'll just replace me!"

# Boiling it down
Let's face facts.  It is trivial to manage a calender, call a meeting to order, send out notes afterwards, etc.  These are things that an AI either does now or could easily do in the near future.  But human nature will have to change a lot before we'd accept an AI replacing Susan.  And those are examples of attributes that have always separated truly great scrum masters from those that are either just starting out or are phoning it in.

Here's another tough truth, and something core to my philosophy.  It doesn't matter how much you say you want to be this kind of scrum master.  It doesn't matter what your intention is.  If the outcomes aren't there, if your team doesn't trust you or include you, if they are not open to your input, then this is your problem to solve.  You can self select out, go put your talent to work someplace else.  Not every team can be coached by every scrum master, no matter how great they are.  However, I would challenge you to look in the mirror first.  Has this happened to you before?  Is this a trend?  If your last few teams all result in the same feeling, where you're an outsider and nobody wants to listen to your really good advice, then maybe you need to evolve.  Ask for feedback, and really listen.  The world needs great scrum masters - we want you to be successful.

I've had great scrum masters like this when I was coding on teams.  I've experienced the joy that comes from having someone push on us and see us get objectively better.  Yes, it takes a shared commitment to improvement, but a final quality I'll call out in a great scrum master is that they inspire that in everyone around them.  What methods do you use to inspire people?  Are they working?

_P.S. To all the amazing scrum masters I've had the pleasure of working with in the past, thank you.  I know I wasn't always good at expressing my gratitude back then, but you made a huge positive difference in my life and career._