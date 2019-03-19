---
layout:	post
title:	"Issue 5: You know why they call it a Royale With Cheese?"
date:	2017-08-14
---

  Hello!

This week I’ve been thinking about metrics. I love a good metric. A metric is simply a thing we use to measure how well a team is doing. If I’m going to help a team to improve then metrics are a great way of demonstrating what areas need to be worked on, and then demonstrating an improvement.

Here’s a collection of metrics to consider -

**Production defects per day**  
Basically, how often does stuff that doesn’t work make it to your live environment? Ideally this number should be much less than 1.

**Production outage frequency**  
Similar to the above, but different. This is how often your live environment stops working in a significant way. Something like a downed website or a broken checkout process.

**Defects caught in quality assurance per feature**  
This is often a fascinating number, but I rarely see it being tracked. If you have dedicated testers or QA engineers, they should be able to work this out. If your number is high (something over 1) then you know something might be wrong, but it’s hard to know what. It could be that your developers are just sloppy, but that’s unlikely. I find it’s generally an indication that there’s a difference in understanding between different team members of what a feature is supposed to do. It may also be a sign that your QA people are defining correct behaviour, rather than your product people. Tread carefully — where this number is high you generally need detailed further investigation.

**Feature lead time**  
Very simply, how long is it from the time you decide to do something to the time that thing is in front of customers. The average is useful here, but the 85th percentile is even more useful. Say, for example, you deliver 85% of features within 10 days of starting them. That means you have an 85% chance of finishing any given feature within 10 days. That’s a pretty useful thing to know when you’re looking at planning a schedule or roadmap. If something has a very hard deadline, maybe start work on it at your 95th percentile figure.

**Minutes spent in meetings**  
Controversial, perhaps, but interesting. Especially considered alongside your feature lead time.

**Static code analysis**  
On the more technical side of things, tools like <https://codeclimate.com/> can give you loads of insight into how your code base is doing. Of particular interest are things like *churn* (how often a given file or set of files is changed, indicating poor architecture or a problematic feature), *cyclomatic complexity *(how complex your code is — branching logic, nested loops etc — and therefore how hard it might be for developers to work with) and *test coverage* (how good a job your tests are doing of testing all your features)

**Deployment frequency**  
How often your code reaches your live environment. I’ve seen this range from approximately twice an hour to approximately twice a year. Being able to deploy as often as you like opens up possibilities for better business agility, faster fixes and easier experimentation. Deploying often should always be one of your goals.

### Conference News

This week I’ve confirmed I’ll be [speaking ](https://www.codetalks.de/en/2017/programm/software-s-seven-deadly-wastes)on ways to go faster at [code.talks](https://www.codetalks.de/en/) in Hamburg in September. Get thee to Hamburg, why not?

### Bathroom Windows

Finally for this week, I want to draw your attention to an article on dev.to — <https://dev.to/atyborska93/what-my-bathroom-window-taught-me-about-code-quality>. This site is full of loads of great writing by software developers, but this particular article stood out to me this week. I think it’s the most concise argument for *just getting stuff done* that I’ve seen.

Thanks for reading!

Jez

  