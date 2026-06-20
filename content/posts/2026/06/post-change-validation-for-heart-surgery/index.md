---
title: "Post change validation... for heart surgery?"
date: 2026-06-19T09:00:00-04:00
description: "Honestly, y'all have zero excuses after reading this for why you can't test changes in production safely."
displayInMenu: false
displayInList: true
featuredImage: "/posts/2026/06/post-change-validation-for-heart-surgery/heart-testing.png" 
featuredImageDescription: "A cartoon of a heart doctor working on a heart."
categories: ["devops"]
draft: false
---
A doctor did post-deploy validation in production on me recently and it kind of blew my mind. Bear with me. I need to give you some backstory before the payoff will be worth it.

## Backstory
At the end of May I had a cardiac ablation done to address chronic arhythmia I've been dealing with for a while. There's a whole long story about my heart issues that goes back 17 years, but I'll spare you from all that for now. Left unchecked, Atrial Fibrillation (afib) can cause permament structural damage to your heart and even total heart failure, so getting it under control is important. The good news for me is that I don't have any structural issues yet, and I'm recovering well from the procedure. In fact I'm heading out for a run when I'm done writing this.

Afib is a complex condition - there's multiple issues happening and it's hard to say which underlying issue is the root problem. Even worse, nobody knows what triggers it to start happening in the first place. Diet, exercise, and alcohol are all known to contribute. Fun trivia for you: one of the first large scale cardiac studies in history was finding a correlation between heavy alcohol intake and arhythmia (look up "holiday heart syndrome"[^1]).

Basically it is an electrical problem: cells in your heart are emitting a signal telling the muscle to contract that are not supposed to do that, or are repeating the signal too quickly, or both. The symptoms suck. Because your heart is fluttering, recovering from any kind of cardio exercise is really difficult. It can feel like you are skipping beats, which is an unsettling, empty feeling in your chest where you wonder for a split second whether your heart will ever beat again, then suddenly it does and you feel relief that you're not dead, and then it happens again a few seconds later. During my last bad episode this was happening every 10-20 seconds all day long for a month. Not fun.

Cardiac Ablation is a procedure where the doctor uses two catheters to go up inside your heart, probe around to find the cells that are electrically active that are not supposed to be, and kill them in a targeted way. Methods have improved over the years, from using extreme cold or heat, to the current best practice of Pulsed Field Ablation which uses high energy electricity to kill the tissue in a more focused way. PFA has fewer side effects and risks than the older methods, and that's what they used on me back in May. The first week after the procedure sucked, but it's gotten much better since then.

Ok, all that was backstory to get to the good stuff. I promise the payoff will be worth it.

## Organic testing
I saw a line in my post-op notes that gave me serious pause:
> Post RFA, no inducible arrhythmias induced, despite aggressive burst pacing with adenosine infusion.

Digging into the notes further revealed a detailed explanation. After performing the ablation, the doc used a variety of methods to try and _induce_ afib. They monitored whether errant electrical signals could enter _or exit_ my atrium. They used chemicals to try and make the conditions for afib as easy as possible to occur and made sure it didn't. Check it out:

> After ablation the Octaray was advanced to the LA and a post-ablation voltage map was created showing electrical isolation of the PVs and posterior wall. Entrance block and exit block were confirmed around each pulmonary vein using pacing from the mapping catheter. Adenosine was infused with stimulation and pacing during the diagnostic portion of the procedure in order to induce or attempt to induce arrhythmia.

As a software developer, this was so mind blowing to me. At the start of the procedure they did detailed electrical mapping (root cause analysis), then they corrected the issues (code changes), then they verified with a new electrical map, then they did production testing to make sure the defect was resolved. Inside my body. While I was unconcious.

Y'all, if doctors can figure out how to do post deploy validation on a human being safely, I don't want to hear a single excuse about why you can't do it on a website.

Now... if only my docs could do this with no downtime...

[^1]: Tonelo D, Providência R, Gonçalves L. Holiday heart syndrome revisited after 34 years. Arq Bras Cardiol. 2013 Aug;101(2):183-9. doi: 10.5935/abc.20130153. PMID: 24030078; PMCID: PMC3998158.