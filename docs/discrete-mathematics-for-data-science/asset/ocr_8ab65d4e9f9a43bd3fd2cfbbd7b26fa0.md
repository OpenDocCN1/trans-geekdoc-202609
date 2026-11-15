using a modulo operation, often denoted as mod, to
compute a remainder.

For example, for a circular queue of eight elements, q0, q1,
..., q7, the computation of each element's index is:

```
index = (index + 1) MOD 8
```

where MOD 8 refers to the remainder when a given value is
divided by 8.

In postfix, the computation is:

```
index 1 + 8 MOD
```

Suppose the index for an element is currently 7.
Incrementing the index by 1 results in the index being
computed as 8. However, incrementing the index again by
1 results in the index being computed as 1. Therefore,
whenever the index is 8, the next index is reset to 1.

A hybrid queue may be implemented with the properties of
both a priority queue and a circular queue. In such a
queue, certain priority conditions lead to a re-indexing of
the circular queue. Examples of such queues are found in
operating systems where, for stability, system processes
must be prioritized for CPU time over less critical
processes, such as a user's programs. Figure 16.10 depicts
this kind of queue with indices q and priorities p.