Artificial Intelligence ■ 9

| 5 | 8 | | 7 | 5 | 8 | | 7 | 5 | 8 |
| 7 | 6 | 3 | | 6 | 3 | | 4 | 6 | 3 |
| 4 | 1 | 2 | | 4 | 1 | 2 | | 1 | 2 |

| 5 | 8 | | 7 | 5 | 8 | | 7 | 5 | 8 |
| 4 | 6 | 3 | | 4 | 6 | 3 | | 4 | 6 | |
| 1 | | 2 | | 1 | | 2 | | 1 | 2 | 3 |

| 5 | 8 | | 7 | | 8 | | 7 | | 8 |
| 4 | | 6 | | 4 | 5 | 6 | | 4 | 5 | 6 |
| 1 | 2 | 3 | | 1 | 2 | 3 | | 1 | 2 | 3 |

Figure 1.4 The first pattern (upper left) represents the initial configuration and the last (low right) the goal configuration. The series of moves describe the solution to the problem.

The control strategy for the search would be:

+   - Halt when goal is in the working memory.
- Chose a random production.
- Do not allow loops.

In Figure 1.4, we see an example representing a sequence of states that lead the initial configuration to the goal configuration.
Production systems implement a search algorithm that defines a problem space and can be represented as a tree.

# 1.2.4 Tree Search

The search by a search tree is performed from an initial state through the following states until a goal state is reached. A search tree is represented by nodes and edges. Each node represents a state, and each edge represents a transition from one state to the following. The initial state defines the root of the tree. From each state $
u$, $B_
u$ states can be reached or the state is a leaf. $B_
u$ represents the branching factor of the node v. A leaf represents either the goal of the computation or an impasse when no valid state exists. In contrast to a real tree in computer science, the root of a tree structure is at the top of the tree and the leaves are at the bottom. Every node beside the root has a unique node from which it was reached, called the parent. The parent is the node above it and