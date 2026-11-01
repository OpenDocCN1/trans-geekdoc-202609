
Some machine learning techniques work better when supplied with features of a state that are relevant to predicting the state’s heuristic value, rather than with just the raw state description. For example, the feature “number of misplaced tiles” might be helpful in predicting the actual distance of an 8-puzzle state from the goal. Let’s call this feature `x1(n)`. We could take 100 randomly generated 8-puzzle configurations and gather statistics on their actual solution costs. We might find that when `x1(n)` is 5, the average solution cost is around 14, and so on. Of course, we can use multiple features. A second feature `x2(n)` might be “number of pairs of adjacent tiles that are not adjacent in the goal state.” How should `x1(n)` and `x2(n)` be combined to predict `h(n)`? A common approach is to use a linear combination:

`h(n) = c[1]x[1](n) + c[2]x[2](n)`.

### Feature

The constants `c1` and `c2` are adjusted to give the best fit to the actual data across the randomly generated configurations. One expects both `c1` and `c2` to be positive because misplaced tiles and incorrect adjacent pairs make the problem harder to solve. Notice that this heuristic satisfies the condition `h(n) = 0` for goal states, but it is not necessarily admissible or consistent.

## Summary

This chapter has introduced search algorithms that an agent can use to select action sequences in a wide variety of environments—as long as they are episodic, single-agent, fully observable, deterministic, static, discrete, and completely known. There are tradeoffs to be made between the amount of time the search takes, the amount of memory available, and the quality of the solution. We can be more efficient if we have domain-dependent knowledge in the form of a heuristic function that estimates how far a given state is from the goal, or if we precompute partial solutions involving patterns or landmarks.

- Before an agent can start searching, a well-defined problem must be formulated.
- A problem consists of five parts: the initial state, a set of actions, a transition model describing the results of those actions, a set of goal states, and an action cost function.
- The environment of the problem is represented by a state space graph. A path through the state space (a sequence of actions) from the initial state to a goal state is a solution.
- Search algorithms generally treat states and actions as atomic, without any internal structure (although we introduced features of states when it came time to do learning).
- Search algorithms are judged on the basis of completeness, cost optimality, time complexity, and space complexity.
- Uninformed search methods have access only to the problem definition. Algorithms build a search tree in an attempt to find a solution. Algorithms differ based on which node they expand first:
  - Best-first search selects nodes for expansion using an evaluation function.
  - Breadth-first search expands the shallowest nodes first; it is complete, optimal for unit action costs, but has exponential space complexity.
  - Uniform-cost search expands the node with lowest path cost, `g(n)`, and is optimal for general action costs.
  - Depth-first search expands the deepest unexpanded node first. It is neither complete nor optimal, but has linear space complexity. Depth-limited search adds a depth bound.
  - Iterative deepening search calls depth-first search with increasing depth limits until a goal is found. It is complete when full cycle checking is done, optimal for unit action costs, has time complexity comparable to breadth-first search, and has linear space complexity.
  - Bidirectional search expands two frontiers, one around the initial state and one around the goal, stopping when the two frontiers meet.
- Informed search methods have access to a heuristic function `h(n)` that estimates the cost of a solution from n. They may have access to additional information such as pattern databases with solution costs.
  - Greedy best-first search expands nodes with minimal `h(n)`. It is not optimal but is often efficient.
  - `A*` search expands nodes with minimal `f(n) = g(n) + h(n)`. `A*` is complete and optimal, provided that `h(n)` is admissible. The space complexity of `A*` is still an issue for many problems.
  - Bidirectional `A*` search is sometimes more efficient than `A*` itself.
  - `IDA*` (iterative deepening `A*` search) is an iterative deepening version of `A*`, and thus adresses the space complexity issue.
  - `RBFS` (recursive best-first search) and `SMA*` (simplified memory-bounded `A*`) are robust, optimal search algorithms that use limited amounts of memory; given enough time, they can solve problems for which `A*` runs out of memory.
  - Beam search puts a limit on the size of the frontier; that makes it incomplete and suboptimal, but it often finds reasonably good solutions and runs faster than complete searches.
  - Weighted `A*` search focuses the search towards a goal, expanding fewer nodes, but sacrificing optimality.
- The performance of heuristic search algorithms depends on the quality of the heuristic function. One can sometimes construct good heuristics by relaxing the problem definition, by storing precomputed solution costs for subproblems in a pattern database, by defining landmarks, or by learning from experience with the problem class.

## Bibliographical and Historical Notes

The topic of state-space search originated in the early years of AI. Newell and Simon’s work on the Logic Theorist (1957) and GPS (1961) led to the establishment of search algorithms as the primary tool for 1960s AI researchers and to the establishment of problem solving as the canonical AI task. Work in operations research by Richard Bellman (1957) showed the importance of additive path costs in simplifying optimization algorithms. The text by Nils Nilsson (1971) established the area on a solid theoretical footing.

The 8-puzzle is a smaller cousin of the 15-puzzle, whose history is recounted at length by Slocum and Sonneveld (2006). In 1880, the 15-puzzle attracted broad attention from the public and mathematicians (Johnson and Story, 1879; Tait, 1880). The editors of the American Journal of Mathematics stated, “The ‘15’ puzzle for the last few weeks has been prominently before the American public, and may safely be said to have engaged the attention of nine out of ten persons of both sexes and all ages and conditions of the community,” while the Weekly News-Democrat of Emporia, Kansas wrote on March 12, 1880 that “It has become literally an epidemic all over the country.”

The famous American game designer Sam Loyd falsely claimed to have invented the 15 puzzle (Loyd, 1959); actually it was invented by Noyes Chapman, a postmaster in Canastota, New York, in the mid-1870s (although a generic patent covering sliding blocks was granted to Ernest Kinsey in 1878). Ratner and Warmuth (1986) showed that the general n × n version of the 15-puzzle belongs to the class of NP-complete problems.

Rubik’s Cube was of course invented in 1974 by Ernő Rubik, who also discovered an algorithm for finding good, but not optimal solutions. Korf (1997) found optimal solutions for some random problem instances using pattern databases and `IDA*` search. Rokicki et al. (2014) proved that any instance can be solved in 26 moves (if you consider a 180° twist to be two moves; 20 if it counts as one). The proof consumed 35 CPU years of computation; it does not lead immediately to an efficient algorithm. Agostinelli et al. (2019) used reinforcement learning, deep learning networks, and Monte Carlo tree search to learn a much more efficient solver for Rubik’s cube. It is not guaranteed to find a cost-optimal solution, but does so about 60% of the time, and typical solutions times are less than a second.
