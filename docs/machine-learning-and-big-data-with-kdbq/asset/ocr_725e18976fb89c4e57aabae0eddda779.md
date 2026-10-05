# 574 MACHINE LEARNING

used to extract allExpandedMoves, a subset of moves which have been explored in the previous playouts.

This is used in the body of the function, where the evaluation can take place based on the validity of the following condition: (available Moves~allExpandedMoves). If the condition is true, then all possible moves have been already tried. If we have a game tree already explored every node of the tree spanning from the given node and can then use the UCT function to select which child node to follow. On the other hand, if the condition is not satisfied, there exists at least one child node which has not been explored by the existing game tree. In such a case, the node is chosen randomly out of all the set of nodes which has not explored yet.

Let us see how the function works. First, we reinitiate the bucket:

```
bucket(`moveStateisWinnernumberOfRunstree`)!(symbol($);0j;10j);
  flip(`gameTreeisWinner)!(long($);symbol($);long($))
  -;1.414214);
```

and update the bucket by adding three more variables into the dictionary:

```
bucket[`indexInTree`];0j;
bucket[`treeDepthCounter`];0j;
bucket[`isWinner`];0j;
```

We run the code repeatedly until we reach the situation with `isWinner being different from 0:

```
bucket::quantQ.moves.MCTSTurnRun[bucket]
bucket
```

The first two runs give:

```
`movesStateisWinnernumberOfRunstreeindexInTreereeDepthCounter
  !(list`a3;0j;10j);flip(`gameTreeisWinner)!(long($);
  -symbol($);long($);1.414214;0j;1j);
`movesStateisWinnernumberOfRunstreeindexInTreereeDepthCounter
  !(a3;b1;0j;10j);flip(`gameTreeisWinner)!(long($);symbol($
  -long($);long($);1.414214;0j;2j);
```

we see that `movesState` is populated and `treeDepthCounter` is increasing. After several repetitions of the code, we finally get:

```
`movesStateisWinnernumberOfRunstreeindexInTreereeDepthCounter
  !(a3`b1`a2`c3`b3`a1`b2;1j;10j);flip(`gameTreeisWinner)
  !(long($);symbol($);long($);1.414214;0;9j);
```

The game in the 9th play needed 1 trees. This concludes one of the MCTS algorithm. Since there is no game tree available during the game, the playout is merely a random game.

Thepropagation of the playout is done at this step. This is part of the runMCTS function, which wraps the oneMCTSTurnRun function and is responsible for building the game tree across iterations. The input of the function is the dictionary of variables. The three variables added for oneMCTSTurnRun are added locally within a function: