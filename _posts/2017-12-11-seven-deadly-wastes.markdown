---
layout:	post
title:	"Seven Deadly Wastes: Bugs"
date:	2017-12-11
---

## Going Faster: Issue 17

![](/img/0*n8ef0p41RCyAixJY.jpg)The Seven Wastes are an idea from _[lean manufacturing](https://en.wikipedia.org/wiki/Muda_%28Japanese_term%29#Seven_wastes)_, and I’m exploring how they relate to software development. Last time was _[over production](https://medium.com/going-faster/seven-deadly-wastes-over-production-e21731f44358)_, and this week I’m looking at the last one: **defects**.

It’s no great revelation to say that bugs slow us down, but they might slow us down more than you realise.

Say we catch a major defect during the final testing of a new feature, just before it’s due to be released. We all pat each other on the back — thank goodness we caught that! Good job everybody!

But now we have to rework the feature to remove the bug. Effectively, we’re back at the start. We need to go back and modify our code, test our feature (more effectively this time), run through any acceptance tests and whatever else we might do. If we’re unlucky we’ve also pushed our schedule back a bit too.

The point here is that as soon as a defect leaves a developer’s laptop and finds its way into our usual code pipeline, it is slowing us down. And the later in that pipeline we find it, the more delay it has the potential to cause.

This is the reason we have things like test driven development — to ensure we catch the bug before pushing code. Then we might have a CI server that runs a more thorough test suit — another layer of safety net to catch the more tricky problems. Then we might have a more involved QA process, or some other phases or processes that try to reduce defects.

What these things don’t address, though, is the worst kind of bug. The kind that the programmer doesn’t realise is a bug. The kind that arises from a difference of understanding. I interpret a requirement one way, someone else interprets it another. Now we have, in one persons opinion at least, a defect.

These bugs have the biggest potential to slow us down, because they can make it all the way through even the most thorough testing.

Avoiding this kind of defect should be the whole team’s priority. And the best way to avoid them is to talk! Build shared understanding, try pair programming, use techniques like BDD and [OOPSI](https://jennyjmar.com/2016/04/16/bdd-discovery-and-oopsi/) to get everyone on the same page.

Layers of testing can go a long way, but talking it through as a team is often the most effective way of building in quality.
