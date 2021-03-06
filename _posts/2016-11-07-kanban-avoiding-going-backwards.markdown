---
layout:	post
title:	"Kanban: Avoiding going backwards"
date:	2016-11-07
---

Tickets on a Kanban board should ideally move left-to-right in a smooth progression. Sometimes, however, a ticket will fail to pass a given stage. Probably the most common reason for this is a tester identifying a problem with a feature during your QA phase. Let’s call these sorts of problems “stage failures”.

So, what should happen when we have a stage failure? It can be tempting to move the ticket backwards into your “in development” column for the original developer to continue work.

However, this often has the effect of hiding the fact that there was problem. A casual observer of the board would not know whether or not that item had been moved backwards, so the amount of effort being expended on the ticket is hidden. Many teams try to get around this issue by marking such tickets in some way — a red blob each time it moves back is typical. This may seem to resolve the problem, but it actually removes the usefulness of one of Kanban’s best features.

By moving tickets backwards, potentially several times, a troublesome ticket may never get the attention it deserves. It would eventually be possible to enter a state where _every_ ticket on the board is simply moving backwards and forwards, without anything really being produced. Tickets in this state are stuck in a loop that they may never exit, and red blobs will really only act as a sort of “permission slip” to excuse the team from considering this to be a problem.

For this reason, I would always suggest that QA failures, poor code review results or any other reason one might give for a ticket failing a stage should be considered a first-class blocker and treated as such. The ticket should remain in its position on the board until it is resolved, and resolving it should be the whole team’s priority. That way, if you end up with too many failed tickets in progress, you will hit your column limits and be forced, as a team, to address the underlying issues causing the blocks.

Some stage failures are of course inevitable, but that doesn’t mean that we have to like them. Treating them as problematic and outside of normal working helps to socialise the idea that they are something to be avoided at all costs, and helps the whole team to improve.
