# Symbolic State Representation — ■ 105

exponentially with depth, almost all time is spent in the deepest level, even though shallower levels are generated arithmetically increasing number of times. The paradox can be explained using the arithmetic geometric sequence. A quantum iterative deepening search is equivalent to the iterative deepening search [108]. For each limit max, a quantum tree search is performed from the root, where max is the maximum depth of the search tree. The possible solutions are determined using a measurement. We gradually increase the limit of the search from one, to two, three and four and continue to search until the goal is found. For each limit $m$, a quantum tree search is performed from the root, with $m$ being the maximum depth of the search tree. The possible solutions are determined by a measurement. The time complexity of an iterative deepening search has the same order of magnitude as the quantum tree search. The total costs of $m$ iterations with $m$ measurements are

```
$O(1) + O(B) + O(B^2) + O(B^3) + \dots + O(B^m) = O(B^m); \quad\ (7.1)$
```

the equation is based on the geometric series [108].nA second constraint is represented by the constant branching factor. If the branching factor is not constant, the maximal branching factor $B_{max}$ must be used for the quantum tree search [107]. It turns out in the chapters 10 and 11 that this problem may be overcome elegantly.