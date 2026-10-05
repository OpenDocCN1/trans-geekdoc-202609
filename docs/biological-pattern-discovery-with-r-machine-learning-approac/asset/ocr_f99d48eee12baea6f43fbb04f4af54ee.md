# Whole Genome Pattern Discovery

Table 7.8. The alignment for the cell (4, 2). The cells with bold number are completed alignments.

| | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|n| 1 | C | 0 | 0 | 1 | 0 |
| 2 | A | 1 | 0 | 0 | **1** |
| 3 | G | 0 | 1 | 0 | 0 |
| 4 | G | 0 | 3 | 2 | **1** | 0 |
| 5 | C | **1** | 1 | 1 | 2 | 0 |
| 6 | A | **1** | 0 | 0 | 1 |

Table 7.9 shows the final result of the forward propagation for aligning these two sequences using the Needleman-Wunsch algorithm.

$M_{4,2} = s_{4,2} + \max\{M_{5,3}, M_{6,4}M_{5,(3,4)}\} = 1 + \max\{1, 0, 2\} = 3$

Table 7.9. The forward propagation result for aligning CAGGCA over AGCTA.

| | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|n| | A | G | T | C | A |
| 1 | C | 3 | 2 | 2 | 0 |
| 2 | A | 4 | 2 | 2 | 1 |
| 3 | G | 3 | 3 | 2 | 1 |
| 4 | G | 2 | 3 | 2 | 1 |
| 5 | C | 1 | 1 | 1 | 2 | 0 |
| 6 | A | 1 | 0 | 0 | 0 | 1 |

# 7.2.3.3 The backward propagation stage

The backward propagation stage of the Needleman-Wunsch algorithm is used to find the best alignment between two sequences. The procedure starts from the top-left corner cell and ends at the bottom-right corner cell. The rule is that every residue in rows or columns cannot be visited more than once. Besides, whenever a residue is passed over, a gap is inserted.

First, the cell (2, 1) had the highest score in the whole table. For this cell, the alignment is shown below, where the first residue C of sequence $x$ was aligned with a gap while the second residue A of sequence $x$ was aligned with the first residue A of sequence $y$.