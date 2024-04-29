---
title: "AI Use Cases"
date: 2023-10-23T11:00:00-04:00
description: "There are plenty of ways to leverage current AI tools for decision assistance"
displayInMenu: false
featuredImage: "/posts/2023/10/ai-use-cases/ai-components.png"
featuredImageDescription: ""
categories: ["ai"]
draft: false
---
Amidst the hype surrounding AI there are real, practical ways that these tools are providing value.  This is a high level look at the types of things I'm finding work well and where the challenge has been, as well as some links to books to go deeper.

# Data Analyzer is a game changer
The paid version of ChatGPT has a model called Data Analyzer and it exemplifies the near-term potential of AI. Data Analyzer allows you to upload files, like a PDF or spreadsheet, and then "talk" to the AI about it.

Behind the scenes ChatGPT is composing and running programming code to solve problems, but all that complexity stays hidden.  It feels like you are talking to a data scientist who reasons out what you want to learn, gains insights from the data, and then explains the results to you with words and charts.

I've given it census data and asked it to find relationships between things – it noticed the number of people sharing a household is related to poverty level, nicely demonstrated it with a chart, but was careful to point out that this was just a correlation and probably not causal.  I used it to help me predict how many requests per minute a web application was likely to get given some historical data about the pilot users and our plans for launching it to more people.  It also helped me understand some cost implications of network latency for remote contractors. 

It even helped me be petty with my HOA.  They have a rule the entire neighborhood hates about keeping beverages 4 feet away from the edge of the community pool.  I know, super lame, right?  When I asked why we have that rule, the explanation was that spilling beverages in the pool would hurt the pH balance.  I used Data Analyzer to prove that it would take 184,178 beers to alter the pH balance of that pool enough to matter.  I got a lot of high-fives from my neighbors for the Facebook post I made about it.

To be clear, I had no idea how to calculate that - I'm not a pool man!  I asked data analyzer what it would need to know in order to do it.  All it needed from me were the dimensions of the pool.  It looked up guidelines on public pool pH balance, as well as the average pH value of beer.  It figured out all the formulas and plugged in all the variables.  Therein lies the power: *AI can help you figure out what you don't know.*  It lowers the cost of deeper and more thorough analysis of problems, even petty ones.

The interesting thing about using Data Analyzer is that you get to watch the AI reason its way through a problem.  It often splits a task up into many steps, executing and checking the results one at a time.  It's fascinating to watch because it's so human-like and relatable, even/especially when it's doing something I don't know how to do very well. 

# Caveat: describing what you want is hard
I went in on a Carolina Hurricanes season ticket package this year with a few other families.  I can't possibly go to every game but the perks of buying a full season are nice, so this way we get to have our cake and eat it too.  I figured dividing up the tickets using an AI would be an easy way to fairly distribute the games.  Boy was I wrong.

It seems simple: just supply a list of all the games and dates to the AI, and tell it to divide the games evenly, right?  But then you want to make sure each family gets the same number of weekend games.  And you don't want one family to get the first two months of games, then the next gets the next two months – you want to evenly distribute the games throughout the season.  And you don't want one family to get more than one game in a weekend… 

As I kept refining the way I was presenting the task to the AI I realized that I could probably have done this in a spreadsheet by hand far faster than it was taking to get the AI to do it how I wanted.  My lesson learned on this situation was that not every task is made easier by AI because sometimes the hardest part is just figuring out what I actually want and how to describe it.

# What happens next
I think there are going to be two levels of change happening in the field of AI over the next few years.  On one side we'll see lots of normal people adopting AI based tools that save them time and improve how they make decisions.  Tools that capture conversations and accurately summarize them into notes will get better, privacy concerns will get worked out, and these types of things will become a normal part of our lives.  In a few years it will be as natural as the spell checker I'm using to write this article.

On the other, deeper side, the conversation around Artificial Super-Intelligence is going to heat up.  Imagine Data Analyzer, but instead of just data science code running behind the scenes, there are multitudes of specialized AIs that your ChatGPT can talk to, like healthcare or finance AIs.  Even more, imagine that if you ask it something it doesn't have an expert on already, it creates one in a few minutes while you wait.  What would that allow us to do?  And what happens when we allow something like that to run on its own and develop its own goals and aspirations?  If this sounds crazy or impossible, think again.  This is exactly what OpenAI is working on building right now.  Some experts believe this will happen in the next 5-7 years.   

# Books to read and go deeper
If you want to learn about what AI research is like and more about what the Artificial Super-Intelligence "event horizon" is, check out [Our Final Invention](https://amzn.to/407pr6l), by James Barrat.

For a fun and easy-to-read explanation about the fundamentals of neural networks and how they work to solve problems, I highly recommend [Blondie24: Playing at the Edge of AI](https://amzn.to/3S9p9Ke) by David Fogel.  It's a fun story of a couple of researchers who built a master level checkers playing neural network and some of the challenges they had in testing it against human players in the 90s.

Finally, if you're into philosophy, I highly recommend [Gödel, Escher, Bach: an Eternal Golden Braid by Douglas Hofstadter](https://amzn.to/3Mes3K9).  You'll learn that formal systems, such as consciousness, are inherently self-referential and what the implications of that could be for a true AI.