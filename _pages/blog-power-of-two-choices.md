---
layout: single
permalink: /blog/power-of-two-choices/
title: "The Power of Two Choices"
author_profile: true
excerpt: "A short note on randomized load balancing. Under construction."
---

**Under construction.** I am working on a fuller example and simulation.

Suppose a new request must join one of many queues. Picking one queue at random is cheap, but it can land on a busy one. The **power of two choices** samples two queues and sends the request to the shorter one. That single extra comparison can reduce the chance of a bad placement: if a fraction *p* of queues are busy and the samples are independent, the chance that *both* samples are busy is *p*², rather than *p* for one random sample. Real queueing behavior needs more careful analysis; [Michael Mitzenmacher's paper](https://www.eecs.harvard.edu/~michaelm/postscripts/tpds2001.pdf) studies that theory.

I first noticed the idea in a post online, then recognized it in a paper assigned for CIS 7000-007. In [*blk-switch* (OSDI 2021)](https://www.usenix.org/conference/osdi21/presentation/hwang), an overloaded local core randomly considers two other cores with egress queues leading to the same destination and steers the request toward the less loaded one. The paper chooses two to keep the decision cheap while reducing contention. [*The Tail at Scale*](https://dl.acm.org/doi/10.1145/2408776.2408794), another assigned reading, cites the power-of-two-choices literature, but *blk-switch* is the paper whose mechanism explicitly uses it.
