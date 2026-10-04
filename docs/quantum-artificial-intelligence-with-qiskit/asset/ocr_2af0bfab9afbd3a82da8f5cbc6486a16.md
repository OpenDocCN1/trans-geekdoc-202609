# 10 Quantum Artificial Intelligence with Qiskit

is connected by an edge. Each parent $v$ has $B_v$ children. The depth of a node $v$ is the number of edges to the root node. Nodes with the same depth $k$ define the level $k$. For a tree with a constant branching factor $B$, each node has $B$ children, and at level $k$, there are $B^k$ nodes [73], [60], [87]. Breadth-first search performs a level-wise search. All nodes at a level have been visited before visiting a node at the next. Depth-first search expands the deepest node in the search tree until a goal is reached or all nodes are impasse states.

# 1.2.5 Informed Search

Heuristic search is based on a heuristic function $h(v)$ that estimates the cheapest cost from the node $v$ to the goal.

We will demonstrate the principles of heuristic $h(v)$ on the 8-puzzle example, and the "city-block distance" [73, 78, 61]. The first heuristic counts the number of misplaced tiles in each state compared to the desired goal. While this heuristic fails to take into account all available information such as the distance tiles must be, "city-block distance" sums all the distances by which the tiles are out of place, with one count for each square a tile must move to reach a position of the desired state. The "city-block distance," also called the "Manhattan distance," is often better than the "number of misplaced tiles"

Greedy-first search expands the node that is closest to the goal according to a heuristic function $h(v)$. Of the $B$ children node $v$ is chosen

> $$\min(h(v_i))$, 1\leq i\leq B$

Like depth-first search follows a single path to the goal. It always expands the deepest node in the search according to $h(v)$ until a goal is reached or all nodes are impasse states. The $A$ search evaluates the nodes through a function $f(v)$ that is composed of the heuristic function $h(v)$ and the function $g(v)$ that estimates the cost of reaching the node $v$ from the root node representing the initial state. Finally the $A^*$ is equivalent to the $A$ search with the constraint that the function $h(v)$ is an admissible heuristic, it never overestimates the cost to reach the goal. General invention of heuristic functions is difficult.

# 1.3 MACHINE LEARNING

Many of the ML techniques are derived from the efforts of psychologists and biologists to make more sense of human learning through computational models [7], [121]. There are some parallels between humans and ML. During learning, humans attempt to gain some knowledge, which involves modification of behavioral tendencies by experience. In ML, we can distinguish between supervised learning and unsupervised learning. In supervised learning, the algorithm is presented with examples of inputs and their desired outputs. The goal is to learn a general rule that maps inputs to outputs. Supervised learning is frequently referred to as learning with a teacher