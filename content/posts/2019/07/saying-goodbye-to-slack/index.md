---
title: "Saying goodbye to Slack"
date: 2019-07-09T05:00:00-04:00
description: "My takeaways after migrating from Slack to Microsoft Teams after four years of Slacking"
displayInMenu: false
featuredImage: "/posts/2019/07/saying-goodbye-to-slack/Slack_RGB.png"
categories: ["devops"]
draft: false
---
After four years of Slacking, we have just migrated 2k people to Microsoft Teams.  At our peak with Slack, [as seen below](#usage), we were sending over 60k messages a day, thousands of files, and we had hundreds of integrations.

I first started using Teams last Fall, so I've had a good bit of time with it.  The only reason for the migration is because our company was acquired by a larger company who was firmly established on Microsoft's stack.  For the record I have no issue with that strategy and fully agree having our company on one communications platform is far better than splitting them up.

My goal with this post is to share some observations around the two tools and tell you why I think Slack is going to be just fine even though they lost in our particular case.

# People love Slack because Slack loves people
{{<smallimg src="/posts/2019/07/saying-goodbye-to-slack/heart-slack.png" alt="Slack heart logo" smartfloat="left" width="125px">}}
I don't say that figuratively.  A large majority of our users were emotionally distressed about losing access to Slack.  They felt strongly that Slack had brought them together as remote teams in a way other tools, including Teams, have not.

That's not an accident.  Slack is a design driven product.  Most users of both Teams and Slack will tell you they vastly prefer the chatting experience on Slack, even though they sometimes can't tell you why.  Here's some key UX differences:

1. Channel membership in Slack is simple and leans towards being open.  Teams can't do granular channels yet; a Team can contain many channels, but being part of that Team gives you access to all its channels.  In practice that forces you to create more Teams than you really need, and disperses information more than you want because...
1. Slack search is simple, fast, and very good, but difficult, slow, and clunky in Teams.  This is likely because Teams is actually a melding of several products like Sharepoint, Onedrive, and Skype.
1. There are tiny delays and lags when clicking on elements in Teams you won't find in Slack.  
1. Sharing large snippets of text, like source code, works really well in Slack and is not good on Teams.  
1. Images expand in visually pleasant ways in Slack that have ugly borders and ratios in Teams.  
1. Whitespace and padding are balanced and meaningful in Slack, but feel chaotic in Teams.

<a name="usage"></a>
![our usage over time](/posts/2019/07/saying-goodbye-to-slack/slack-all-messages.png)
### The effect of good design
This all drives people to _want_ to use Slack, which creates that sense of bonding our folks talked about.  Casual chatting on Teams is dramatically less.  Our "play" channels are nowhere near as active in Teams.  Look at the activity growth over time in that chart above - that far outpaced our employee growth.  That was just people using Slack more and more, and email less and less.

Will MSFT make UI improvements?  Of course.  But that underlying tendency to produce something clunky you intend to clean up later will not go away and that means Teams will [always lag behind in user experience](https://microsoftteams.uservoice.com/forums/555103-public/suggestions/17408641-compact-mode).

# Slack is a verb #
I can't tell you how awkward it's been to get used to saying "I'll Teams it to you."  Seriously.  "Slack me that file, please" is so easy on the palette.

# Integrations really matter
Business users don't just chat with each other.  That communication medium has become a hub of information exchange from many different sources.  

MSFT's first party integrations in Teams work well.  For me the most valuable thing about Teams is the ability to click on a person's name, and then click their "organization" tab.  Because Teams is integrated with Active Directory, I see an org chart showing that person's directs and who they report up through, including everyone's titles.  When you have 16k people in your organization and you're trying to learn it, that a huge time saver.

The video conferencing is also very good in Teams.  Slack was late to the game with that feature, and security concerns with it kept us from really trying it out, so I can't really compare the two.

## Slack integrations set a new bar
Third party integrations in Teams feel like an afterthought whereas in Slack they've been a core part of the experience from the start.  Setting up an integration in Teams is clumsy and they way integrations can interact with users is limited and use space very poorly.  Slack is a master course on how to create a good experience here.  No matter how many features MSFT builds into Teams, Slack's healthy marketplace for integrations and the UX around them will be very hard to beat.

### The InfoSec Caveat
Slack customers must be careful to read and understand the terms of use for those third party integrations that are so easy to enable.  Third parties often ask for a lot of data access, many times full access to public and private messages, as well as employee data such as email addresses.  That constitutes PII and you have an obligation to protect that information.  Don't enable blanket integration permissions - make your users request access to new integrations and review them before enabling them.

# Why Slack's future is bright #
Slack is a tough sell right now to a large enterprise already paying licenses for Azure AD and Office 365.  For them, Teams is a bundled cost and to be honest with that stack already in place it works pretty well.  So while entrenched enterprises who buy up smaller companies may drive some business from Slack to MSFT, they don't go happily and I don't see MSFT winning business away on anything other than pure commercial merit.

Let's not forget there's plenty of business to go around. Slack is [smart to partner with companies like Atlassian](https://www.atlassian.com/blog/announcements/new-atlassian-slack-partnership), who also compete directly with MSFT.  They are showing that they can take advantage of the ancient proverbe: "the enemy of my enemy is my friend."  Any customer of GitLab, Jira, Rally, Basecamp, Google Suite, or any of the hundreds of other Azure DevOps and Office 365 alternatives are prime customers for Slack.

With their continued focus on the end user experience and a great open marketplace experience, my money is still on Slack continuing to grow in value.


_Important reminder: the thoughts and opinions here are mine and mine alone and do not represent my employer in any way_
