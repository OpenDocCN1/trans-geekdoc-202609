
![Figure 21-20: Playing a game of Flippers after 3,000 episodes of training with the L-table algorithm. Read the game left to right.](img/F21020.png)

The arrangement shown in Figure 21-20 shows rows of the `L`-table arranged as columns to better fit the page. Each column represents one board configuration (or state). The nine possible actions are shown in each row, highlighted in red. The thick black outline shows the action that the agent selected from that list, leading to the new board in the column to its right. The shaded cell shows the action taken. If the move causes a dot to appear, the move is shown as a solid red dot. If the move causes the dot to go away, it’s shown as an outlined red dot. The colored bar below each board shows its `L`-value from the table. Larger and greener bars correspond to larger `L`-values calculated with discounted future rewards.

Boards near the right have larger `L`-values than those near the left. That’s because those boards were sometimes the randomly chosen starting board for a game. If we picked a good move and won immediately, or in just a few moves, the final reward was large.

Returning to this game, starting from the position on the far left, the algorithm’s first move was to flip the cell in the lower left, introducing a new dot. From that result, it then flipped the square in the middle of the leftmost column, again introducing a dot. From that position it then flipped the upper-left square, removing the dot that was there. The game continued in this way until it found a solution.

We’d expect our algorithm to improve with more training, and it does. Figure 21-21 shows the same game as Figure 21-20 after doubling the length of the training run to 6,000 episodes.

![Figure 21-21: The same game as Figure 21-20 after 6,000 episodes of training](img/F21021.png)
