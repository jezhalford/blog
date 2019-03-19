---
layout:	post
title:	"Patchy Thinking: Software is a series of changes"
date:	2016-11-14
---

Before git came along and revolutionised version control, the leading choice for organising code was SVN. Plenty of people still use it today, although many of them probably find it endlessly frustrating. I know I did.

I’d never suggest anyone stick around with SVN when git is available. But it does has one useful aspect that I’m not sure I’m ready to forget. Internally, git considers every revision to be a complete snapshot of the code. These snapshots are linked together and that forms our revision history. A series of still pictures, stretching backwards.

SVN, however, was built on the understanding that each revision was simply a set of changes against the previous revision. To return to a previous state, therefore, one must work backwards though time and undo each change. To move forward again, one needs to replay each revision in turn in order to build up a picture. SVN is a reel-to-reel tape. Git is perhaps more akin to iTunes, allowing infinite skipping and jumping around history. This is not at all an ideal metaphor, but it will do for now.

![](/img/1*SrmSR5_9bT1X-BxVZi-Quw.jpeg)Git’s skip-ability is really helpful for making branching easy, and for doing all the clever stuff that git does. But I wonder if it’s caused us to forget something useful about software development.

We are never building isolated snapshots, we are always moving from one state to the next.

How often have you experienced a change that was made to your codebase, worked fine in testing, and then blew up spectacularly once it reached production? Often this kind of problem can be attributed to a lack of understanding of the state of the system in production.

The most common area where developers may have to confront this is database migrations. These by their nature are always _revisions_ rather than snapshots. Drop that column, create this table; our migrations are instructions for moving us from one state to the next. I find it helpful, though, to think of every aspect of every change in the same way. It’s the developers job not simply to write how the code should be, but to consider exactly how to get it there.

I try to think of each change as a patch: a set of changes that will take us from one situation to another. Do we need to clear a cache? Are we installing new packages? Is it necessary to restart some services? How will this affect our users at the moment it is released? It can be tempting to dismiss these problems as the domain of our release process, either automated away or frustratingly worked-through by the unlucky sole who must perform a manual release.

Once we embrace this kind of patchy thinking, though, we start to get better at it. Maybe we don’t need to flush a cache every time we release? Wouldn’t our users have a better experience if we could do at least _some_ of our releases without downtime? It’s this kind of wider-world view among developers that is part of the essence of DevOps — awareness from everyone on the team of how our systems _really_ work, and what it takes to keep them going while we change them.
