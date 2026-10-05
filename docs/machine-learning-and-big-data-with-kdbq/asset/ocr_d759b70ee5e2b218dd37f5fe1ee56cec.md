# Towards AI - Monte Carlo Tree Search

while the second run makes Player 2 to be a winner achieving the stones to be placed
on diagonal:

```
`movesState`isWinner`(`a1``b2``c1``b3``a3`;2j)`
```

and, finally, the last game ends up as:

```
`movesState`isWinner`(`a2``c2``b1``b3``c2``b1``a3`;1j)`
```

We leave it to the reader to interpret the result.
In addition, we can start with the board being pre-filled by stones. This
is achieved by assigning moves into `movesState` variable. The game continues
from the starting point. Let us test it:

```
(.quantQ.mcts.oneTurn())/[`ox=x=`isWinner`];(`movesState`isWinner`)!(`a1``a2
`;0])`
```

```
`movesState`isWinner`!(`a1``a2``b2``c1``b3``c3``a3`;2j)`
```

Let us use the functions to assess the probability of a win for two players.
In particular, we run 100,000 random games, starting with an empty board. After each
playout, we record the `isWinner` variable. In the end, we report the statistics.
Let us start with payouts:

```
isWinnerTS:[tmp;quantQ.mcts.oneTurn())/[`ox=x=`isWinner`];(`movesState
isWinner`)!(`$`);0`); tmp[`isWinner`] til 100000;
```

and count the cases by the type of the game end:

```
select count isWinnerTS from ( ) isWinnerTS
```

| isWinnerTS | isWinnerTS |
|---|---|
| 1 | 58605 |
| 2 | 28739 |
| 3 | 12656 |

In the random playouts, the probability to win for Player 1 is more than twice
much as for Player 2. Placing the first stone brings a considerable advantage in ran-\dom games. The probability of a draw is approximately 13%, which underestimates the
outcome of the statistical analysis.

Finally, it is convenient to provide some form of graphic interface to the game, at
least to output, and visualise the game as we are used to. The visualisation function
aims to provide a convenient view of the game from the console:

```
.quantQ.mcts.visualBoard:[{bucket]}
// bucket -- information about the game
// player 1 moves
player1: bucket[`movesState`{x where=mod[x;2]] til count bucket[`
→ movesState];`
```