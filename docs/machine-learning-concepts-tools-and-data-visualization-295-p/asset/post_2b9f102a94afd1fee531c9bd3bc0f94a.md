
matches. The emergence of artificial intelligence, which does not require the learning of big data, is meaningful in that it offers solutions to areas in which it is difficult to utilize artificial intelligence because of the difficulty of obtaining big data (unlike the case of Go).

- Alpha Zero

AlphaZero is a generalized artificial intelligence program that can be applied to board games such as Go, chess, and others as an algorithm. It took two hours for Alpha Zero to beat Elmo, the 2017 CSA world champion, and Shogi; for hours to beat Stockfish, the 2016 champion, at Chess; and 30 hours to beat AlphaGo Zero at Go.

On December 14, 2017 (U.S. time), Dr. Aja Huang (Staff Research Scientist at DeepMind, DeepMind Technologies Limited) announced that she would end her journey with AlphaGo and shift over all AlphaGo’s resources to other artificial intelligence development projects.

## 4.1.2 Algorithm Implementation

Until AlphaGo appeared, Go was believed to be the only analog game that a computer could not approach from the perspective of a human being. Artificial intelligence-based Go, which had been developed up until that point, was far different from that played by professional Go players. Therefore, what kind of method did AlphaGo use to distance itself from previously existing algorithms and to beat the world’s top professional players?

Let’s take a closer look at the structure of the game of Go.

### AI Approach Strategy

Let’s look at how AI approaches problems in a 1-on-1 board game. Suppose we have been asked to create artificial intelligence that wins boards without considering the game’s time limit, when a game could potentially take an infinite amount of time.

As there would be no time limit, an ideal method would be to look as far ahead as possible and take the ideal course of action in the present state.

In the end, one would have to predict what the other person will do in relation to one’s move. Among the algorithms that could be used to solve this problem, the Minimax Algorithm is one of the most representative. Figure 4-3 shows a tree to explain the Minimax Algorithm.

The circles represent the moves of the player running the algorithm, while the squares represent the moves of the opponent. When it considers all the possible moves of the opponent and the player running the algorithm, the scores that the latter could obtain after four moves are marked on the 4 layers. The highest

![](img/3c3c87d78136583581b0cf0620f5ae66_68_0.png)

Figure 4-3 Minimax algorithm

score attainable by the player running the algorithm is + infinity, which would clearly be the most desirable outcome for that player.

However, of course, if the opponent is a reasonable player, he will act in a way that minimizes the points player running the algorithm can earn. Therefore, the player running the algorithm will be acting to get a smaller +10 score of +10 or + infinity. Also, in their turn, the player running the algorithm and the opponent will choose to maximize their score.

With this mind, when one moves from level 1 to level 0, one should neither choose to get the highest score of +10 or infinity points as shown on the left-hand side, but when considering the moves of the opponent, the best course of action would be to go for the score of -7 on the far right-hand side.

In a one-on-one game like Go, this behavior is known as the ideal choice, and the minimax algorithm is applied in the sense that you must choose the best of the worst numbers your opponent provides, minimizing possible loss. In the end, creating a powerful AI requires an algorithm that efficiently navigates these search spaces, looking for behaviors that use less time and perform better than the minimax algorithm.

Various algorithms such as alpha-beta pruning and principal variation search have been suggested to find this method. The following method is the Monte Carlo Tree Search (MCTS), which is the most widely used AI for board games and based on AlphaGo.

- Monte Carlo Tree Search (MCTS)

In computer science, the Monte Carlo tree search (MCTS) is a heuristic algorithm for some kinds of decision processes, most notably employed in game play. This is a generic term for "probable ways of solving problems." This approach uses randomness to approximate the elaborate formulas that are hard to find, rather than huge search spaces that are hard to see. For example, suppose you

![](img/3c3c87d78136583581b0cf0620f5ae66_69_0.png)

**Figure 4-4** Monte Carlo Tree search diagram

draw a circle with a radius of 1 inscribed on a 2 x 2 square, and then randomly draw a point in this square to calculate the most of points in the circle / the total number of points taken. After that, if you draw many points, the value will eventually converge on the value of $\pi/4$.

This is an example of a typical Monte Carlo method, using Monte Carlo to calculate the value of the circumference. Monte Carlo Tree Search is an algorithm designed to select a good course of action without needlessly searching for all possible states by applying the Monte Carlo technique to the behavior tree search using the aforementioned minimax algorithm.

Let’s look at the most basic form of MCTS, and how MCTS uses randomness to construct a tree.

The Monte Carlo Tree Search Diagram is shown in Figure 4-4. There are four basic steps in MCTS.

- Selection: From the root to the Leaf Node by picking the most successful child node among the other nodes. In general, to avoid searching on only one side, MCTS is calibrated in such a way as give options randomly.
- Expansion: If a leaf node is reached, and it is not the final node at the end of the game, create a child node for the next step, choose one of the child nodes among them, and move.
- Simulation: Proceed with playing the game by performing random simulations in the current state. This is called playout, and one progresses through the game until the outcome of the game is decided (for example, whether you win or lose).
- Backpropagation: It updates the weights on the nodes of the paths based on the results of the current simulation.

MCTS repeats this step as many times as possible to simulate information regarding the winning rate of each action that I might take

When doing a degree of searching and then finally selecting an action, one should choose the action that has been simulated with the largest number of possible actions on the route. Surprisingly, it has been proven that if the MCTS is repeated indefinitely, the result converges to the value of minimax.

However, in general, the convergence speed of basic MCTS is very slow, so there is a need for a method that reduces search space and finds results more efficiently.

The final result MCTS wishes to obtain from converging is the probability of winning on each node (game status). There is a theoretical function v * that calculates the degree of probability that I can win the game in this state when the current state “s” of the game is given. Of course, we do not know what these functions look and how they work, but we can assume the existence of these functions. When the MCTS proceeds indefinitely, the values of each node the MCTS converge to value v*.

Conversely, if we have a function v(s) that can approximate v*, because we can first get the approximate results we want from MCTS, we may be able to calculate our ideal move, even without proceeding with MCTS too deeply. In others, creating function v(s) that calculates the win rate from the current state “s” of the game is important.

Previous researchers utilized MCTs and v(s) as methodological approaches, and used them to go AI, such as Pachi and Fuego.

However, because function v(s) is too difficult to create powerful v(s) functions, which has led to a weakening of AI performance. At this point in time, however, Google's DeepMind team has greatly improved performance by transplanting deep learning into the process of creating v(s).

The focus of MCTS is on the analysis of the most promising moves, expanding the search tree based on random sampling of the search space. The application of Monte Carlo tree in games is based on many plays, also called rollouts. In each playout, the game is played out to the very end by selecting moves at random. The final result of each playout is then used to weight the nodes in the game tree so that better nodes are more likely to be chosen in future plays.

- AlphaGo Pipeline Structure

So far, we have learned that AlphaGo expertly navigates the state-action tree using the MCTS technique and the state evaluation function v (s) learned using
