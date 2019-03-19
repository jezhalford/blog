---
layout:	post
title:	"Seven Deadly Wastes: Inventory"
date:	2017-10-23
---

## Going Faster: Issue 12

![](/img/0*pYF69d1HtrV3Gzoq.jpg)The Seven Wastes are an idea from [lean manufacturing](https://en.wikipedia.org/wiki/Muda_%28Japanese_term%29#Seven_wastes), and I’m exploring how they relate to software development. Last week was [transport](https://medium.com/going-faster/seven-deadly-wastes-transport-822117500697), and this week is *inventory*.

Inventory is any product that hasn’t yet been delivered, so in manufacturing that’s components, materials, and unfinished products.

In software the closest match to inventory of that kind is *work in progress*. Put simply, that’s work that we’ve started but haven’t yet finished.

Work in progress is considered waste because it has no value. Until a feature is shipped and in front of customers, it might as well not exist. It isn’t doing us any good. So, lean manufacturing tells us, we should work to reduce our work in progress as much as possible. Practically speaking this means that, ideally, each person on a team should be working on only one thing at a time. That maximises our productivity while minimising our waste.

But why does it matter?

Unfinished software is far more harmful than it might at first seem. How often have you encountered one of these situations —

* You can’t release urgent feature X, because half-finished feature Y is already merged in, and you haven’t shipped that yet.
* You know that important thing is in your git stash somewhere but can’t remember where.
* Someone asks you to release features in a different sequence to the one they were developed in, and you end up in merge-hell.
* You can’t ever seem to focus on a single problem for more than an hour before something else urgent comes along.
These are all examples of work in progress slowing us down.

The simple answer to this is to simply not start anything new until you’ve finished what you’re currently doing. Life is of course, rarely that easy.

It might be helpful to use a physical Kanban board to visualise your work in progress. Seeing the volume of tickets a team is working on can really help hammer home the complexity for managers.

![](/img/0*kPM5yysjIOmDPHS7.jpg)Kanban can help us in other ways, too. In short, you represent your process as columns on the board — to do, in dev, in QA, etc — and move cards between them for each work item. You then set limits for how much work each column is allowed to hold at any given time. By sticking to those limits, we can force ourselves to move stuff out of the way before we pull more things in. If you get really good at it, you can fine-tune those limits to maximise your flow efficiency and deliver *really* quickly.

It’s also important to try to ship things as often as you can, and in the smallest increments possible. It’s far easier to make one small change to production than it is to make a huge raft of changes all at once. Yet so many of us still go weeks, even months, between releases. It always seems harder, but once you get to grips with changing things little and often, it’s always far less work.

In my experience, inventory is one of the most common wastes encountered by organisations of all sizes. It’s easy to overlook, and it can have a huge impact on your productivity. But fortunately it is also quite easy to reduce, once you recognise it.

Remember: stop starting and start finishing!
