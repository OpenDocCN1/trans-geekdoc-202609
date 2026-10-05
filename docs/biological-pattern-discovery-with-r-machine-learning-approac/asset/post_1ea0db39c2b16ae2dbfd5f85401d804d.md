
# Whole Genome Pattern Discovery 333

has been already aligned with a previous residue of sequence x. This is called the vertical move, i.e., moving from the cell (i-1, j), a downward cell to the cell (i, j). More than one cell is allowed meaning more one gap is allowed to be inserted for the cell (i, j). For instance, both the $i^{th}$ and $i-1^{th}$ residues of sequence x are aligned with gaps, a vertical move is from cell (i-2, j) to cell (i, j).

To align the $i^{th}$ residue of sequence y with a gap, no residue from sequence x is picked up. This means that the $i^{th}$ residue of sequence x is aligned with other residue of sequence y in previous alignment. This is the horizontal move, i.e., moving from the cell (i, j-1) on the left side to the cell (i, j). Similar to the vertical move mentioned above, the horizontal move can be done more than one cell. For instance, both the $j^{th}$ and $j-1^{th}$ residues of sequence y are aligned with gaps, a horizontal move is from the cell (i, j-2) to cell (i, j).

Table 7.12. The initialisation of the dynamic programming table for using the Smith-Waterman algorithm. The left panel is used for calculating alignment scores by cell and the right panel is used for recording moving directions for cells.

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | |
| 1 | G | 0 | | | | | |
| 2 | C | 0 | | | | | |
| 3 | A | 0 | | | | | |
| 4 | U | 0 | | | | | |
| 5 | U | 0 | | | | | |
| 6 | G | 0 | | | | | |
| 7 | A | 0 | | | | | |

| | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| A | A | C | U | C | C | C |

## 7.2.4.2 The initialisation algorithm

The Smith-Waterman algorithm also needs an initialisation stage. Suppose the Smith-Waterman algorithm is used to align two sequences, $x=GCAUGAA$ and $y=AACACC$. Table 7.12 shows a dynamic programming table for the Smith-Waterman algorithm and how the initialisation was done in this table for aligning these two sequences. In the initialisation stage, a gap penalty was filled in for the cells in the initial row and initial column. This is similar to the Sellers algorithm. Because a gap penalty used by the Smith-Waterman algorithm was negative, it was capped to 334 Biological Pattern Discovery with R zero. It can be seen that all the cells which align a residue against a gap were assigned a score zero in the table.

## 7.2.4.3 The forward propagation

The update rule of the Smith-Waterman algorithm for the forward propagation is shown below, where D stands for the diagonal move, V is for the vertical move and H represents the horizontal move:

```
$M_{ij} = \max \left\{0, \begin{matrix} M_{i-1,j-1} + S_{ij} & D \ \max\{M_{i-x,j} + G_x\} & V \ \max\{M_{i,j-x} + G_x\} & H \end{matrix}\right\ (7.13)$
```

No residue from sequence y matched the first residue move: Therefore all the cells of this row were filled with zeros. Their moving directions were not of interest. The cell (2, 3) was for the second residue C of sequence x and the third residue C of sequence y. This was the first pair of identical residues from two sequences from the top-left corner cell. The alignment score for this cell was calculated as below,

```
$M_{2,3} = \max \left\{0, \begin{matrix} \max\{0 + (-1 - L/3)\} & V \ \max\{0 + (-1 - L/3)\} & H \end{matrix}\right\ = 1$
```

The diagonal move led to a score one shown below,

```
$M_{1,2} + s_{2,3} = 0 + 1 = 1$
```

Both the horizontal move and the vertical move ended up with a zero score. For instance, the score of the horizontal move from the cell (2, 2) and the cell (2, 1) was calculated as below,

```
$\max\{0 + (-1 - 1/3), 0 + (-1 - 2/3)\} = -4/3$
```

Here -4/3 was capped to zero. Maximising three scores resulted in the selection of the diagonal move for this cell, shown in Table 7.13.

Table 7.13. The alignment for the cell (2, 3).

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | A | A | C | U | C | C | | A | A | U | C | C |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | | | | |
| 1 | G | 0 | 0 | 0 | 0 | 0 | | | | | | |
| 2 | C | 0 | | 0 | 1 | | | | | | |
| 3 | A | 0 | 1 | 0 | 0.67 | | | | | | |
| 4 | U | 0 | | | | | | | | | | |
| 5 | U | 0 | | | | | | | | | | |
| 6 | G | 0 | | | | | | | | | | |
| 7 | A | 0 | | | | | | | | | | |

For the cell (3, 4), the alignment score of the diagonal move was 0.67, which was calculated as,

```
$M_{2,3} + s_{3,4} = -0.33 + 1 = 0.67$
```

Both the horizontal move and the vertical move had a score zero. Therefore, the diagonal move was selected for this cell with an alignment score 0.67. Table 7.14 shows this result.

```
$M_{3,4} = \max \left\{0, \begin{matrix} max[0 + (-1 - L/3)] & V \ max[0 + (-1 - L/3)] & H \end{matrix}\right\} = 0.67$
```

Table 7.14. The alignment for the cell (3, 4).

| | 0 | 1 | 2 | 3 | 4 | 5 | 6 | | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | A | A | C | U | C | C | | A | A | C | U | C |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | | | | | |
| 1 | G | 0 | 0 | 0 | 0 | 0 | | | | | | | |
| 2 | C | 0 | | 0 | 1 | 1 | | | | | D | D |
| 3 | A | 0 | 1 | 0 | 0.67 | | | | | | D | |
| 4 | U | 0 | | | | | | | | | | |
| 5 | U | 0 | | | | | | | | | | |
| 6 | G | 0 | | | | | | | | | | |
| 7 | A | 0 | | | | | | | | | | |

The final result of the forward propagation stage is shown in Table 7.15.

Table 7.15. The forward propagation result.

| | 0 | 1 | 2 | 3 | 4 | 5 | C | 6 | | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | A | A | | | U | C | | | A | A | U | C | C |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | | | | | | | |
| | G | 0 | 0 | 0 | 0 | 1 | 1 | 0 | | | | | D | D |
| | 2 | C | 0 | 0 | 0 | 1 | 1 | 0 | | | | | | | |
| | 3 | A | 0 | 1 | 0 | 0.67 | | 0.33 | | D | D | | D | | |
| | 4 | U | 0 | 0 | 0.67 | 0.67 | | 0.33 | | | D | D | | D | H |
| | 5 | U | 0 | 0 | 0 | 0.33 | 1.33 | 1 | | | | | | D | H |
| | 6 | G | 0 | 0 | 0 | 0 | 1.33 | 1 | | | | | | D | D |
| | 7 | A | 0 | 1 | 0 | 0 | 1 | 1 | | D | D | | | V |

## 7.2.4.4 The backward propagation stage

The Smith-Waterman algorithm does not necessarily start from the bottom-right corner when searching for the best alignment in the backward propagation stage. Instead, it starts from a cell with the maximum alignment score and moves towards the top-left corner cell. The propagation stops at a cell with a zero alignment score.

Table 7.16. The backward propagation result.

| | 0 | 2 | 3 | 4 | U | C | 2 | 3 | 4 |
|---|---|---|---|---|---|---|---|---|
| | 0 |  | |  | | | | | | |
| | 3 | A | 0 | 1 | 0 | 0.67 | | | | | |
| | 4 | U | 0 | 0 | 0.67 | 0.67 | | 0.33 | | | | |
| | 5 | U | 0 | 0 | 0 | 0.33 | 1.33 | 1 | | | | |
| | 6 | G | 0 | 0 | 0 | 0 | 1.33 | 1 | | | | |
| | 7 | A | 0 | 1 | 0 | 0 | 1 | 1 | | D | D | | | |

For the cell (3, 4), the alignment score of the diagonal move was 0.67. Both the horizontal move and the vertical move had a score zero. Therefore, the diagonal move was selected for this cell with an alignment score 0.67. Table 7.14 shows this result.

```
$M_{3,4} = \max \left\{0, \begin{matrix} max[0 + (-1 - L/3)] & V \ max[0 + (-1 - L/3)] & H \end{matrix}\right\} = 0.67$
```

Whole Genome Pattern Discovery 335

## 7.2.4.5 The R library for the Smith-Waterman algorithm

The pairwiseAlignment function of the Biostrings can also be used for employing the Smith-Waterman algorithm for a local pair-wise homology alignment depending on the design of a properly designed substitution matrix, a gap opening penalty and a gap extension penalty. Aligning the above two sequences using the Smith-Waterman algorithm is shown below. First the RNAString function was called to define two sequences

```
s1=RNAString('GCAUUGA')
s2=RNAString('ACUCU')
```

Next a substitution matrix was defined. All the diagonal entries of this substitution matrix were filled by one and all off-diagonal entries were filled by -0.3. To do this, the following code was used. Table 7.17 shows this substitution matrix used by the Smith-Waterman algorithm.

```
subs=matrix(-0.3,nrow=4,ncol=4)
diag (subs)=1
rownames (subs)=colnames (subs)=RNA_ALPHABET[1:4]
```

Table 7.17. Forward propagation result.

| | A | C | G | U |
|---|---|---|---|---|
| A | 1 | -0.3 | -0.3 | -0.3 |
| C | -0.3 | 1 | -0.3 | -0.3 |
| G | -0.3 | -0.3 | 1 | -0.3 |
| U | -0.3 | -0.3 | -0.3 | 1 |

The pairwiseAlignment function was then called. The definition of two parameters (gapOpening and gapExtension) were assigned -1.3 and -0.3.

```
align-pairwiseAlignment(s1,s2,type='local',
substitutionMatrix=subs,gapOpening=-1.3,
gapExtension=-0.3)
```
