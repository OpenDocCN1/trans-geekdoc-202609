# Machine Learning: Concepts, Tools and Data Visualization

+   Backpropagation: It updates the weights on the nodes of the paths based on the results of the current simulation.

MCTS repeats this step as many times as possible to simulate information regarding the winning rate of each action that I might take

When doing a degree of searching and then finally selecting an action, one should choose the action that has been simulated with the largest number of possible actions on the route. Surprisingly, it has been proven that if the MCTS is repeated indefinitely, the result converges to the value of minimax.

However, in general, the convergence speed of basic MCTS is very slow, so there is a need for a method that reduces search space and finds results more efficiently.

The final result MCTS wishes to obtain from converging is the probability of winning on each node (game status) in the tree. There is a theoretical function v * that calculates the degree of probability that I can win the game in this state when the current state “s” of the game is given. Of course, we do not know what these functions look and how they work, but we can assume the existence of these functions. When the MCTS proceeds indefinitely, the values of each node the MCTS converge to value function v* — each state.

Conversely, if we have a function v(s) that can approximate v*, because we can first get the approximate results we want from MCTS, we may be able to calculate our ideal move, even without proceeding with MCTS too deeply. In others, creating function v(s) that calculates the win rate from the current state “s” of the game is important.

Previous researchers utilized MCTs and v(s) as methodological approaches, and used them to go AI, such as Pachi and Fuego.

However, because function v(s) is too difficult to create powerful v(s) functions, which has led to a weakening of AI performance. At this point in time, however, Google's DeepMind team has greatly improved performance by transplanting deep learning into the process of creating v(s).

The focus of MCTS is on the analysis of the most promising moves, expanding the search tree based on random sampling of the search space. The application of Monte Carlo tree in games is based on many plays, also called rollouts. In each playout, the game is played out to the very end by selecting moves at random. The final result of each playout is then used to weight the nodes in the game tree so that better nodes are more likely to be chosen in future plays.

+   AlphaGo Pipeline Structure

So far, we have learned that AlphaGo expertly navigates the state-action tree using the MCTS technique and the state evaluation function v (s) learned using