
# Game of Go and Monte Carlo Tree Search

## Weaknesses of heuristic alpha–beta tree search

The game of Go illustrates two major weaknesses of heuristic `alpha–beta` tree search: First, Go has a branching factor that starts at 361, which means `alpha–beta` search would be limited to only 4 or 5 ply. Second, it is difficult to define a good evaluation function for Go because material value is not a strong indicator and most positions are in flux until the endgame. In response to these two challenges, modern Go programs have abandoned `alpha–beta` search and instead use a strategy called Monte Carlo tree search (`MCTS`).[3](#Chapter06-09.xhtml#sup06-3)

## Monte Carlo tree search (MCTS)

The basic `MCTS` strategy does not use a heuristic evaluation function. Instead, the value of a state is estimated as the average utility over a number of simulations of complete games starting from the state. A simulation (also called a playout or rollout) chooses moves first for one player, then for the other, repeating until a terminal position is reached. At that point the rules of the game (not fallible heuristics) determine who has won or lost, and by what score. For games in which the only outcomes are a win or a loss, “average utility” is the same as “win percentage.”

### Simulation / Playout / Rollout

How do we choose what moves to make during the playout? If we just choose randomly, then after multiple simulations we get an answer to the question “what is the best move if both players play randomly?” For some simple games, that happens to be the same answer as “what is the best move if both players play well?,” but for most games it is not. To get useful information from the playout we need a playout policy that biases the moves towards good ones. For Go and other games, playout policies have been successfully learned from self-play by using neural networks. Sometimes game-specific heuristics are used, such as “consider capture moves” in chess or “take the corner square” in Othello.

### Playout policy

Given a playout policy, we next need to decide two things: from what positions do we start the playouts, and how many playouts do we allocate to each position? The simplest answer, called `pure Monte Carlo search`, is to do `N` simulations starting from the current state of the game, and track which of the possible moves from the current position has the highest win percentage.

### Pure Monte Carlo search

For some stochastic games this converges to optimal play as `N` increases, but for most games it is not sufficient—we need a selection policy that selectively focuses the computational resources on the important parts of the game tree. It balances two factors: exploration of states that have had few playouts, and exploitation of states that have done well in past playouts, to get a more accurate estimate of their value. (See [Section 16.3](#Chapter16-03.xhtml#sec16-3) for more on the exploration/exploitation tradeoff.) Monte Carlo tree search does that by maintaining a search tree and growing it on each iteration of the following four steps, as shown in [Figure 6.10](#Chapter06-04.xhtml#fig6-10):

Description

The graph consists of six nodes labeled W "A", N T, Q, N S W, V, and T. Node W "A" is connected to node N T on the upper right. Node N T is connected to node Q on the lower right. Node Q is connected to node N S W below. Node N S W is connected to node V on the lower left. The node at the bottom is labeled T and is not connected to any node.

×![](images/Fig-94.jpg)

Figure 6.10One iteration of the process of choosing a move with Monte Carlo tree search (`MCTS`) using the upper confidence bounds applied to trees (`UCT`) selection metric, shown after 100 iterations have already been done. In (a) we select moves, all the way down the tree, ending at the leaf node marked 27/35 (for 27 wins for black out of 35 playouts). In (b) we expand the selected node and do a simulation (playout), which ends in a win for black. In (c), the results of the simulation are back-propagated up the tree.

## Selection policy / Exploration / Exploitation

•Selection: Starting at the root of the search tree, we choose a move (guided by the selection policy), leading to a successor node, and repeat that process, moving down the tree to a leaf. [Figure 6.10(a)](#Chapter06-04.xhtml#fig6-10) shows a search tree with the root representing a state where white has just moved, and white has won 37 out of the 100 playouts done so far. The thick arrow shows the selection of a move by black that leads to a node where black has won 60/79 playouts. This is the best win percentage among the three moves, so selecting it is an example of exploitation. But it would also have been reasonable to select the 2/11 node for the sake of exploration—with only 11 playouts, the node still has high uncertainty in its valuation, and might end up being best if we gain more information about it. Selection continues on to the leaf node marked 27/35.

•Expansion: We grow the search tree by generating a new child of the selected node; [Figure 6.10(b)](#Chapter06-04.xhtml#fig6-10) shows the new node marked with `0/0`. (Some versions generate more than one child in this step.)

•Simulation: We perform a playout from the newly generated child node, choosing moves for both players according to the playout policy. These moves are not recorded in the search tree. In the figure, the simulation results in a win for black.

•Back-propagation: We now use the result of the simulation to update all the search tree nodes going up to the root. Since black won the playout, black nodes are incremented in both the number of wins and the number of playouts, so 27/35 becomes 28/36 and 60/79 becomes 61/80. Since white lost, the white nodes are incremented in the number of playouts only, so 16/53 becomes 16/54 and the root 37/100 becomes 37/101.

We repeat these four steps either for a set number of iterations, or until the allotted time has expired, and then return the move with the highest number of playouts.

## UCT and UCB1

One very effective selection policy is called “upper confidence bounds applied to trees” or `UCT`. The policy ranks each possible move based on an upper confidence bound formula called `UCB1`. (See [Section 16.3.3](#Chapter16-03.xhtml#sec16-3-3) for more details.) For a node `n`, the formula is:

$UCBI = \\,\\frac{U(n)}{N(n)} + C \\times \\sqrt{\\frac{\\log N\\text{(PARENT(}n\\text{))}}{N\\text{(}n\\text{)}}}$

where `U(n)` is the total utility of all playouts that went through node `n`, `N(n)` is the number of playouts through node `n`, and `PARENT(n)` is the parent node of `n` in the tree. Thus $\frac{U(n)}{N(n)}$ is the exploitation term: the average utility of `n`. The term with the square root is the exploration term: it has the count `N(n)` in the denominator, which means the term will be high for nodes that have only been explored a few times. In the numerator it has the log of the number of times we have explored the parent of `n`. This means that if we are selecting `n` some nonzero percentage of the time, the exploration term goes to zero as the counts increase, and eventually the playouts are given to the node with highest average utility.

`C` is a constant that balances exploitation and exploration. There is a theoretical argument that `C` should be $\sqrt{2}$, but in practice, game programmers try multiple values for `C` and choose the one that performs best. (Some programs use slightly different formulas; for example, `ALPHAZERO` adds in a term for move probability, which is calculated by a neural network trained from past self-play.) With `C = 1.4`, the 60/79 node in [Figure 6.10](#Chapter06-04.xhtml#fig6-10) has the highest `UCB1` score, but with `C = 1.5`, it would be the 2/11 node.
