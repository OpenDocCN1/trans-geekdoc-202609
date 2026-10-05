# 560

# MACHINE LEARNING

child nodes of the root node, which contain all the possible moves by player 1. At the second level, the tree consists of all the moves of player 2 conditioned on the previous move of player 1. The third level, consecutively, captures the move of player 1 conditioned on the two previous moves. Switching the moves continue further down the tree by exploiting all combinations. The leaf node of such a game is a game where the game terminates and one of the players, or the game ends in a draw. In the go of game, the game ends when both players pass the move. Then, the player with the higher score wins, where the score is calculated based on the size of territory belonging to each player.

For a go of game, the root has 19-19 child nodes. At the second level, every node has 19-1 child nodes. This gives altogether at the second level (19 - 19) · (19 - 19) options. The branching ratio of the game is huge and suggests the in-numerical sense - dimension of all the possible states of the game. The tree is asymmetric as the difference in a number of moves between the longest and the shortest game can be huge.

When the game tree is not so huge, we can explore the full tree as we explained in the minimax algorithm in the preceding paragraphs. Given the knowledge of the full tree, the tree at every stage of the game can be optimised such that the chance to win is highest. This is not possible for games like go.

If we want to avoid the apparent cause of dimensionality, we have to abandon methods which rely on exploring the entire tree. The Monte Carlo method comes at this point as an alternative method to full exploration. The idea is to start at the current state of the game and play many games out of the current point. Then, we choose the best option from those explored. In order to build the tree, we face the problem which is in nature similar to the multi-armed bandit problem. The arms of the bandit are possible moves – stones to be played at a given state – and the payoff is a likelihood when a given choice has been taken.

A naive approach would be to play a number of randomly simulated playouts. In every playout, the game would start at the current state. The progress of the game would be simulated by playing random playouts by player, starting with the player whose best turn we aim to find. Among the set of allowed moves at a given turn, one move or there is a draw if allowed by rules. After the set of random playouts is finished, the next move is determined. The way to do it is to group the randomly simulatedouts then then for each group, the ratio of won games to all games played is calculated and with the highest ratio chosen.

Playing random games is a highly inefficient approach as we have seen with the multi-armed bandit problem. Thus, the MCTS algorithm uses a more elaborate approach to find the optimal move. The MCTS is based on the iteration of the following steps:

+   * Selection
* Expansion
* Simulation
* Back propagation