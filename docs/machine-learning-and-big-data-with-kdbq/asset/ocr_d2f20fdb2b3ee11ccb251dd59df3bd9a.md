# Towards AI – Monte Carlo Tree Search

The state of the game is determined by the position of stones on the board, which is visible to both players. We can, construct a game tree with all possible moves. Leaves of the tree are then the different ends of the game. Every node of the tree can be assigned a value which reflects the likelihood of ending up in a leaf node. The straightforward strategy to solve such a game is the minimax algorithm.

The minimax algorithm is a strategy for decision-making which is based on selecting an option which minimises the possible loss in a maximum loss scenario. The maximin is an analogous formulation for games. Since its development in the game theory for zero-sum games, it was extended to the situation with uncertainty and complex game rules. Mathematically, the minimax problem is formulated as:

```
$$$V_i^* = \max_{A_i} \min_{A_{-i}} V_i(A_i, A_{-i}) \quad (28.15)$$
```

$v_i$ is a value for a player $i$, and $A_{-i}$ denotes the action of player $i$ and the other player, respectively. In plain language, the player $i$ wants to play the best action given the other player is doing. To be precise, the player $-i$, i.e. not i, wants to minimise the value of the game for player $i$.

The minimax algorithm is frequently used backwards from the end of the game. In each iterative step, player i wants to win while player -i is the opposite. The backward iteration can be, and thus it is frequently accompanied by some heuristics. The heuristic rules assign a value to every state of the game. The minimax algorithm does not have to run iteratively but rather serves as a decision how to evolve from one state of the game to another.

The vanilla minimax algorithm as briefly outlined fails when:

+   - The number of different states in the game is huge. In the case of it, go is ~ $3^{19-19}$
- The game has high branching ratio, where at every given state of the game, there is a large number of possible actions.

The MCTS addresses the shortcomings of the minimax algorithm. Namely:

+   - MCTS does not need complex heuristics, i.e. to estimate the value of any given state of the game. This can be difficult to achieve in complex games like goto.
- MCTS is very good for games with a large branching factor. The nature of the algorithm is asymmetric; it explores the more promising branches. The search mechanism does not need to devote time to branches which are likely to lose in a loss
- MCTS has a flexible running time. The heuristic-based algorithms need to go through the full tree with all the game options. This may take large amount of time. On the other hand, MCTS can be run in a flexible way and stopped at any time. The bigger the time budget to run can accrue the results of MCTS.

In order to introduce the MCTS algorithm, we need to elaborate more on the decision tree for a game. We consider a two-player game. The decision tree, or game tree, starts at the root node, which is a plain board. The next level of the tree is composed of