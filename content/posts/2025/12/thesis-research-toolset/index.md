---
title: "Research Project Toolset"
date: 2025-12-06T15:00:00-04:00
description: "I cover the tools and process I used to do my masters thesis research project.  Includes tips and tricks for using LLMs as a research assistant."
displayInMenu: false
featuredImage: "/posts/2025/12/thesis-research-toolset/ideasflowing.png"
featuredImageDescription: ""
categories: ["ai"]
draft: true
---
One of the most exciting, practical applications for LLMs came into focus for me during my graduate thesis project.  For context, I started working on a masters degree in Technology Management through ECU in the Fall of 2024.  I opted for the thesis track because I want to learn how to do proper research.  After learning about the high level methods involved, I chose a research question and started on my project in the Spring of 2025.  I'm planning to graduate Fall of 2026.

I wanted to write this up for two reasons.  First, I want to come back to this in a couple of years and contrast the state of research tools against where I started.  Second, if anyone is out there trying to do a research project right now, this might help them get started faster and avoid some of the same pitfalls I ran into.

If you've never done a thesis, the process looks something like this:
1. Develop primary research question or hypothesis
1. Form thesis committee by asking professors to volunteer
1. Write formal thesis proposal
1. Get IRB approval
1. Defend thesis proposal formally with committee 
1. Perform research
1. Write formal thesis documenting the findings
1. Get feedback from committee (<-- I'm current here)
1. Defend thesis formally in front of committee and all invited staff and students

My hypotheses all related to the impact that turnover has on software teams.  I'll write up another entry to describe my findings after the formal defense (hopefully Spring of 2026).  The goal of this essay is to describe the nuts and bolts of what tools I used to perform the research itself.

I had a few problems with my research right from the start.  The database I was studying had 98 million rows it in.  You can't use excel to study that.  I tried using SPSS but I needed to do a lot of transformations on the data and SPSS isn't really well suited for that kind of thing.  Loading the data into a local MySQL instance revealed some severe performance issues: it was taking 5-6 minutes to do exploratory queries.  Transformations could take hours.  I started wasting a lot of time creating indexes and views to try and speed it up, which was a lot of time being spent that wasn't helping me with my research questions.  I felt like I was fighting against my technology way too much, and this was despite using an M4 macbook pro with 36 GB of RAM!

## Final Tech Stack
To make a long story very short, I ended up changing tactics several times before figuring out a tech stack that worked.  Here is where that landed:
 - [DuckDB](https://duckdb.org/) for the data layer
 - Python for any big data transformations
 - R for data analysis
 - Scrivener for compiling the rough draft
 - Bookends for citation management
 - Word for final formatting
 - Claude and ChatGPT for script writing assistance and editorial feedback
 
## DuckDb
DuckDb is a column store database that trades off multi-threading and multi-tenant capabilities for incredible speed.  Unlike databases that serve web applications with thousands of concurrent users, DuckDb can only talk to one connection at a time.  But queries that took MySQL 5 minutes to do complete in 200 milliseconds with DuckDb.  I only had to create indexes a few times for the gnarliest of queries (think 200+ lines joining across a dozen tables and sub-selects).  On disk the database is 13GB, but it loads almost instantly.  DuckDb was absolutely crucial in my work.  It allows for very fast exploratory analysis and even comes with a convenient local browser based interactive dashboard you can use to build notebooks of queries and keep a history of all the work you've done on the database.  Since it uses the same SQL syntax as other databases (for the most part), the AI tools can use it very effectively.

## Python
While Python has expansive data analysis capabilities, I used it mostly for transforming my data.  This is because Python allowed me to set those transform jobs up such that if I hit an error or had to stop it I could start back from where it left off.  This ended up saving me a ton of time because I didn't have to completely start over when I ran into an issue because of some edge case in the data.  I could also have my Python scripts output status updates and estimates for completion which is harder to do with R.  A bonus is that AI tools are very good at writing Python.

## R
Hands down there is no more powerful data analysis language than the R framework.  It is extendable thanks to a huge community of contributors writing new libraries all the time.  Again, AI tools like Claude and ChatGPT are great at writing R.  It's not a hard language to read if you've got any experience with scripting.  There are free online lessons that will help you get up to speed, plus an easy to follow hands on learning path helps you get started quickly.

## Scrivener
I used this for my non-fiction writing already.  I love the workflow of Scrivener.  If you do any kind of long form writing I highly recommend you check it out.  It's not a formatting tool, it's a writing tool.  So you get the bulk of the writing work done with Scrivener, then compile to Word and finish editing and formatting there.

## Bookends
My paper ended up with 55 references.  Word has a built-in reference tracker, but Bookends improves on that workflow quite a bit.  Instead of copy/pasting references and keeping them sorted, Bookends lets you natively search research journals from within the app.  It has lots of capabilities to help you keep your references organized.  Moving references around your document, catching situations where you no longer reference a source, etc - there's far more situations where the extra functionality helped than I expected.

# Claude and ChatGPT
I ended up producing over 25,000 lines of R code and another 2k lines of Python for my research.  Fred Brooks estimated a good developer could write about 10 lines of good code a day, but that was in the 70's.  Reading perspectives from several data scientists online I see estimates that anywhere from 100-500 lines of R code per day is very productive.  That means that, at best, it would have taken 50 days for a human to write all that code if that's all they did.  Realistically we're probably talking more like 200 days of pure research and analysis work.

Using Claude I was writing and revising thousands of lines of R per day during my heavy research phases.  I was able to rapidly and thoroughly explore questions in an afternoon that would have taken weeks to do traditionally.  **The innovation is that the cost of exploring a research question dropped effectively to zero.**  There were many questions I would not have bothered to explore if I'd have had to spend several days writing the R code myself, but when the "cost" is 15 minutes with Claude suddenly those questions are much more interesting and worth asking.

## Workflow and tips
This is what worked for me.  I know there are ways to improve on this, but this worked plenty well enough for me to stay in a flow state.

### Create Documentation for Context
LLMs need to know what you're trying to do and how you want to do it.  The more specific you can be, the better.  I created a few documents I supplied to the LLMs via Project Knowledge that made a huge difference.  First, document your database thoroughly.  Here's some elements to include:

 - Table/View names, column names, and a summary of what the table and each column means
 - How many rows are in each table.  This helps the LLM make better decisions about how to work with it.
 - How the data across tables and columns relates to each other.
 - Where is the database physically located

Second, you should write up a style/guidelines document as well.  Tell the LLM:

 - What kind of visuals or tables to produce by default
 - Output status updates when doing lots of analysis at once  
 - Which directory it should use for outputs like charts and graphs and how to name them  
 - How much documentation and commenting should it include; I had mine include comments to explain each statistical test it was doing and why so that I could double check the thought processes and make sure the R was doing what the LLM intended.  
 - What level of rigor and thoroughness to follow.  It made a big difference when I specified this was graduate level research - the LLM was more thorough with testing and corrections. 

Finally, it helped tremendously when I was clear about the goals of the project.  I included the thesis proposal document itself so that the LLM could see the exact hypotheses we were studying.  Because the proposal included a literature review, the LLM also knew what theoretical frameworks I was leveraging and could help design tests that reinforced that perspective.

### Use Project Spaces
Claude.ai emerged as being slightly better at producing the kind of R code I wanted.  I set up a dedicated project space in Claude and added all the documentation to it.  Each project chat became an exploration of a given research question.  There's 33 conversations in that project now.  I could just tell Claude what I wanted to explore and it would generate an R script.  It was like having a conversation with a research assistant who was moderately good at critical thinking and incredible at spewing out tons of code.  

I would then copy that R script into RStudio so I could review and run it.  If I got an error (which happened regularly) I'd copy/paste the error back to Claude so it could fix the script.  Once it completed I'd copy the results back into Claude.  When we got to a clear answer on the original intent of the chat, I'd ask Claude to summarize the entire conversation, what we learned, and a description of all the tests we did as well as the detailed results.  This created a set of artifacts in the project space that incrementally built up all my research findings.

During the course of my work, Anthropic and OpenAI released updates to their tools, so it was interesting to see how responses improved over the few months of my work.  Regardless, there is a point during a conversation with an LLM where you start getting worse and worse responses.  I quickly developed a sense of that, which is good because it's critical you catch it early.  As soon as you see the conversation start to degrade it's vital you perform a summarization and then start over in a new chat.

The reason for this is because every time you send text to the LLM, the entirety of the conversation plus all project documentation also gets sent.  Eventually that exceeds the practical limit of the LLMs context window and it begins struggling to give good answers.  That also means your token usage rate increases as your conversations get longer.

Which brings me to another tip: rename your chats to indicate whether they were successful or not.  There were several lines of questions I tried to go down that ultimately didn't work.  Either the LLM got overwhelmed, or the findings ended up being inconclusive.  For those I would rename the chat to indicate it was a failure.  If a chat ended up finding something significant I'd do the opposite.  This made it much easier to go back to prior conversations and find the ones that I needed to review or build on.

### Use Models Against Each Other
A great trick to use to make sure you're not missing something is to leverage different models.  Once I started honing in on the key tests and results for my hypotheses, I started feeding those summaries into ChatGPT and asking for critical feedback.  What tests was I forgetting to perform?  What would make the results more reliable or publishable?  This helped me expand my knowledge of statistical best practices (how I learned about False Discovery Rate detection).  I think half the reason this trick works is because you bring a different mindset when asking for feedback and using a different model forces you to do that.  The other half is because I think these models genuinely do different things better than others.

### Caveat Emptor 
I want to end with a couple warnings.  Aside from the fuzzy context window limits, I also had to be vigilant to make sure I remained the head researcher and the LLMs were my assistants.

There were times I needed to transform the data to get it into a better state for study, but the LLM didn't know to suggest that, so answering some questions was very difficult or even impossible.  I had to figure out how to spot these situations.  I think I could have tweaked my prompt to improve on this.

There were also times when the LLM would help me find an answer to a question that was flawed from the start. Again, the LLM in this flow is not going to tell me if a given question is a distraction or based on a flawed assumption.  There are probably adjustments I could make to the documentation that would ask it to do this but I don't want to give up my role as the researcher.

I'm very aware that I could have connected Claude directly to my local R environment that would have allowed it to run Python and R scripts instead of needing me to copy/paste them.  Again, I didn't do that because I wanted to remain in the middle of the process so that I could review the scripts before we ran them.  Several times early on Claude was mis-using a variable and I had to go clear up the documentation.  

Finally, you must always remember the LLM is incentivized around making you feel good and happy with its responses.  When it tells you that you're a genius, that you've made a monumental discovery, that you've changed the course of history, remember it's all B.S.  I had to explicitly ask the LLM to stop editorializing on the findings because it was so distracting.

# Impact and Conclusion
Business Intelligence platforms are surely going to integrate directly with LLMs that will empower business leaders to directly explore complex questions.  This will likely displace some number of data scientists who will pivot to working on different parts of the problem area rather than just translate business questions into R and SQL.  The democratization of intelligence feels incredibly exciting.

What impact will this actually have on our economy?  I suspect very little.  My gut tells me most small/medium businesses get stuck because of poor go-to-market and sales strategy and execution, not because it is too hard to figure out how to get answers to these kinds of questions.  Large businesses could see more value, but changing how a large business works already takes longer than figuring out what to do, so this is optimizing the wrong part of that problem as well.

For academia I think this could be huge.  Reducing the time/cost of large scale research projects could make previously prohibitive research projects within reach.  Casual researchers like myself can improve the quality of our work drastically.  

Technical innovation is about changing the cost model of a capability, or making something previously impossible possible.  LLMs definitely do that when it comes to doing this type of research.  How that ultimately plays out is something I'm very excited to watch.