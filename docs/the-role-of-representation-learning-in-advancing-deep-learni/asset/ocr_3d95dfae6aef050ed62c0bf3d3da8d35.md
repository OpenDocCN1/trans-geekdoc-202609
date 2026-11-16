# # A Scaling Analysis of Reasoning Effort
and Problem Complexity in LLMs

# ## F.1 Full Prompt

The full prompt used in the experiments is the following, on the example of a 4x4 puzzle:

```
1 You are a logic puzzle expert. You will be given a logic puzzle to
2 solve. Here is a description of the puzzle:
3 You have a grid of squares, some of which contain trees. Your aim is to
4 place tents in some of the remaining squares, in such a way that the
5 following conditions are met:
6 There are exactly as many tents as trees.
7 The tents and trees can be matched up in such a way that each tent is
8 directly adjacent (horizontally or vertically, but not diagonally) to
9 its own tree. However, a tent may be adjacent to other trees as well as
10 its own.
11 No two tents are adjacent horizontally, vertically or diagonally.
12 The number of tents in each row, and in each column, matches the
13 numbers given in the row or column constraints.
14 Grass indicates that there cannot be a tent in that position.
```