# Whole Genome Pattern Discovery

Suppose two sequences were prepared for the homology alignment. They were x=CTAG and y=ACTA. Figure 7.1 shows a dynamic programming table for this alignment task. Sequence x was placed on the left side of this table vertically. Suppose sequence y was placed on the top of this table horizontally. Suppose previous alignments had done for three cells (C, A), (C, C), and (T, A). For the alignment of the cell (T, C), which was for the second residue T of sequence x and the second residue C of sequence y, there were three alignment (move)poss. They were the moves from each aligned cells, i.e., the cells (C, A), (C, C) and (T, A). The diagonal move was A from the cell (C, A) to the current cell (T, C). In this situation, it was assumed that the first residue C of sequence x and the first residue A of sequence y had been already aligned. The current alignment led to the alignment of CT versus AC. The horizontal move was from the left cell (T, A) to the current cell (T, C). In this situation, it was assumed that the previous alignment was the alignment of CT versus A—. Because the residue T of sequence x was used in the previous alignment, the current residue C of sequence y had to be aligned with a gap. The current alignment led to the alignment of CT– versus A–C. The vertical move was from the top cell (C, C) to the current cell (T, C). In this, it was assumed that the previous alignment was the alignment of C– versus AC and the current alignment resulted in C–T versus AC—. This is because the residue C of sequence y was used in the previous alignment and a gap had to be inserted in sequence y to align the residue T of sequence x.

| A | C | T | A |
|---|---|---|---|n| C | | | |
| T | | | |
| A | | | |
| G | | | | |

Fig. 7.1. The illustration of three incremental alignments used in the Sellers algorithm.

Given three possible actions for continuing a homology alignment between remaining residues from two sequences, it is required to know