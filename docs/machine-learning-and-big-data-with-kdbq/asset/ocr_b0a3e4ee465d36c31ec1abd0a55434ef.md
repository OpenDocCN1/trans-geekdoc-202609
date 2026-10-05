and exploration – the second term. The value of C is a meta-parameter in the algorithm;
t popular choice is $\sqrt{2}$.

The child node with the highest $UCT_j$ is chosen in the selection step. If more than
one node reaches the highest number, the node is chosen randomly with equal probability.
The decision based on the formula in fact reflects the minimax algorithm.
of $w_i$, at a given point is recorded from the perspective of the player making a
move. Thus, the formula makes the optimal decision for every player and thus player 1
isoptim her decision given player 2 is the same.

At the end of the selection step, the simulated game is a node with at least one
child node which has not been explored.

# 28.2.2 Expansion Step

The process of expansion is to extend the existing tree and include new nodes.
The iteration process reaches at the end of the selection step node which has at least
one child which has not been selected before. Such a child does not have an
assigned pair $(w_i, n_i)$. The iteration progresses from the node to

+   * Among the child nodes which have not been visited, randomly choose one and
extend the selection tree.

The new node is chosen uniformly as there is no preference among the unvisited
nodes or we assume a uniform prior. The new node is included in the selection tree.
Using programming, the decision tree $(w_i, n_i)$ is initialised with 0. This node will get
assigned in last its values $(w_i, n_i)$.

The mechanism of the step is such that it explores new options and extends the
knowledge structure – the mechanism aims to expand every node fully. Namely, at a given node, there cannot be	here are unvisited nodes. If a specific node is promising – it is repeatedly chosen by the
selection step – all the options from the node are to be explored.

The full expansion of every node can have a disadvantage. In particular, if there
a large branching ratio, the tree will aim to grow too slowly. The selection tree
row will be explored by moves which are deeply inferior and such a tree can
c costly to grow. This is apparent for a game of go, for instance, where some moves
wasting of computational time. The reasonable component would be here
of “value” function which use heuristic rules and rule out some moves.
Such approach is in AlphaGo implementation of the MCTS using deep neural
networks. We omit this at this stage and follow the expansion step outlined.

We can expand by more than one node and provide faster building up of the game
tree. Even though this is possible, we have to keep in mind that our objective is
to fill the full/deep selection tree. The aim is to build a knowledge about the nearest
neighbourhood of the game node we want to move from. The process of building a
would also carry a considerable storage cost; let recall the dimensionality of the
game tree for go. It is feasible to stay at expansion by one node only.

Once the new node is added to the tree and the pair $(w_i, n_i)$ is initialised, the game
is played.