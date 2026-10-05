# Whole Genome Pattern Discovery

Table 7.4. The alignment result for the cell (1, 3).

| | 0 | 1 | 2 | 3 | 4 | | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|---|---|---|---||
| | | T | G | C | T | | T | G | C | T |
| 0 | | 0 | 1 | 2 | 3 | 4 | | | | | |
| 1 | T | | 0 | 1 | 2 | | | D | H | H | |
| 2 | | G | 2 | | | | | | | | | |
| 3 | | G | 3 | | | | | | | | |
| 4 | | C | 4 | | | | | | | | |
| 5 | | T | | | | | | | | |

Table 7.5 shows the full forward propagation alignment results for all cells using the Sellers algorithm. After all cells were filled by the alignment distances, discovering the best alignment was implemented in a backward propagation process in this table.

Table 7.5. The alignment result for all cells. V stands for vertical movement.

| | 0 | 1 | 2 | 3 | 4 | | 1 | 2 | 3 | 4 |
|---|---|---|---|---|---|---|---|---|---||
| | | T | G | C | T | | T | G | C | T |
| 0 | | 0 | 1 | 2 | 3 | 4 | | | | | |
| 1 | T | | 0 | 1 | 2 | | D | H | H | H |
| 2 | | G | 2 | | 0 | 1 | | V | D | H | H |
| 3 | | G | 3 | 2 | | 1 | | V | D | D | H |
| 4 | | C | 4 | 3 | 1 | 2 | | V | V | D | H |
| 5 | | T | 5 | 4 | 3 | 2 | | D | V | V | D |

# 7.2.2.2 The backward propagation stage

The search in the backward propagation stage starts from the most-right corner cell with the minimum alignment distance. If the alignment distance of the most-bottom-right cell is not the least, a search of the least distance is backwards to the left cells or upwards to the upper cells. In this case, gaps are inserted at the end of one sequence.

Based on Table 7.5, the best route for the cell (5, 4) was the diagonal move from the cell (4, 3). The alignment distance of the cell (5, 4) was one. Because the move for the cell (5, 4) was diagonal, the distance decomposition is shown below, where the distance in the cell (4, 3) was one, i.e., d(GCCT, GCT)=1 and the current alignment in the cell (5, 4) was 0, i.e., δ(T, T)=0.