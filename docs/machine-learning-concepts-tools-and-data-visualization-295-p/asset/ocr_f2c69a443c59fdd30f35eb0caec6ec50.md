# 52 Machine Learning: Concepts, Tools and Data Visualization

![](bbox=[0.208, 0.086, 0.755, 0.276])

Figure 4-3 Minimax algorithm

score attainable by the player running the algorithm is + infinity, which would clearly be the most desirable outcome for that player.

However, of course, if the opponent is a reasonable player, he will act in a way that minimizes the points player running the algorithm can earn. Therefore, the player running the algorithm will be acting to get a smaller +10 score of +10 or + infinity. Also, in their turn, the player running the algorithm and the opponent will choose to maximize their score.

With this mind, when one moves from level 1 to level 0, one should neither choose to get the highest score of +10 or infinity points as shown on the left-hand side, but when considering the moves of the opponent, the best course of action would be to go for the score of -7 on the far right-hand side.

In a one-on-one game like Go, this behavior is known as the ideal choice, and the minimax algorithm is applied in the sense that you must choose the best of the worst numbers your opponent provides, minimizing possible loss. In the end, creating a powerful AI requires an algorithm that efficiently navigates these search spaces, looking for behaviors that use less time and perform better than the minimax algorithm.

Various algorithms such as alpha-beta pruning and principal variation search have been suggested to find this method. The following method is the Monte Carlo Tree Search (MCTS), which is the most widely used AI for board games and based on AlphaGo.

+   - Monte Carlo Tree Search (MCTS)

In computer science, the Monte Carlo tree search (MCTS) is a heuristic algorithm for some kinds of decision processes, most notably employed in game play. This is a generic term for "probable ways of solving problems." This approach uses randomness to approximate the elaborate formulas that are hard to find, rather than huge search spaces that are hard to see. For example, suppose you