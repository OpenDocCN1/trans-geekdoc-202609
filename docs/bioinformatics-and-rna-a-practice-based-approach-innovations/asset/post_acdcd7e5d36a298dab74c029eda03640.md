
| C | ↖-6 | ↖-4 | ↖-2 | ↖-1 | ↖ 1 |
|---|---|---|---|---|---|
| A | ↖-5 | ↖-3 | ↑-1 | → 0 | ↖ 1 |
| T | ↑-4 | →-2 | ↖ 0 | → 1 | → 0 |
| C | ↖-3 | ↖-1 | ↑ 1 | → 0 | → 0 |
| A | ↑-2 | ↖ 0 | ↖ 0 | ↖-1 | →-1 |
| G | ↑-1 | → 0 | ↖-1 | ↖-1 | →-2 |
| ⌐ | ↓ 0 | →-1 | →-2 | →-3 | →-4 |
| | ⌐ | A | C | G | C |

Step 11. The next step is to trace back. Find out the highest value in the matrix. In our example, the highest value is 1. Generally, the highest value lies in the last column.
Step 12. Now trace back to the box from where this value came from. In our example, the value of cell (C6, R1) came from cell (C5, R2), as shown in Figure 2.5. The further value from cell (C5, R2) came from cell (C4, R3). Similarly, trace back to cell (C2, R6). The trace-back is shown in Figure 2.6.
Step 13. After tracing back, the next step is alignment of sequences. The rules for alignment are as follows:

- For diagonal arrows in tracing back, put letters during alignment.
- For horizontal arrows, put a gap during alignment.

Step 14. The arrow from cell (C6, R1) to cell (C5, R2) is diagonal, so the corresponding letters of cells (C1, R1) and (C6, R8), respectively, are aligned and lead to matching letters.
Step 15. The next arrow from (C5, R2) to cell (C4, R3) is again a diagonal, so corresponding letters of cells (C1, R2) and (C5, R8), respectively, are aligned and lead to a mismatch.
Step 16. On the contrary, the next arrow from (C4, R3) to cell (C4, R4) is a vertical arrow, so the gap is written as shown below:

| C1 | C2 | C3 | C4 | C5 | C6 | |
|---|---|---|---|---|---|---|
| C | -6 | -4 | -2 | -1 | 1 | R1 |
| A | -5 | -3 | -1 | 0 | 1 | R2 |
| T | -4 | -2 | 0 | 1 | 0 | R3 |
| C | -3 | -1 | 1 | 0 | 0 | R4 |
| A | -2 | 0 | 0 | -1 | -1 | R5 |
| G | -1 | 0 | -1 | -1 | -2 | R6 |
| ⌐ | 0 | -1 | -2 | -3 | -4 | R7 |
| | ⌐ | A | C | G | C | R8 |

| G | A | C | T | A | C |
|---|---|---|---|
| - | A | C | - | G | C |

Step 17. The alignment is completed.

## 2.3 LOCAL SEQUENCE ALIGNMENT

Contrary to global sequence alignment, local sequence alignment refers to the alignment of a segment of the sequences and not the complete sequences.

Similarity in sequences is often correlated to homology. Homologous sequences are the ones that belong to the same ancestor. Thus, structure or function can be inferred from sequence alignments. It may not be necessary to align the complete sequences; rather, we may need to align only parts of sequences. In that case, local sequences alignment is a better choice.

The local alignment method was proposed by Smith, T. F. and Waterman, M. S. in 1981. The algorithm is popularly known as the Smith-Waterman algorithm.

The difference between the Needleman-Wunsch algorithm and Smith-Waterman algorithm lies in the filling matrix. The scoring function as well as rules for filling the matrix remain the same. The only difference lies in the values of a matrix. Negative numbers are written as zero and positive numbers are written as is. Another slight difference is in the trace-back step. Here, we will start with the highest number and trace it diagonally until we reach a cell with a zero value, as shown in Figure 2.7.

The resultant alignment is as follows:

| A | T | C |
|---|---|---|
| C | G | C |

Local sequence alignment is important when:

- We need to align two partially overlapping sequences
- One sequence is a subset of another sequence

| C | 0 | 0 | 0 | 0 | 1 |
|---|---|---|---|---|---|
| A | 0 | 0 | 0 | 0 | 1 |
| T | 0 | 0 | 0 | 1 | 0 |
| C | 0 | 0 | 1 | 0 | 0 |
| A | 0 | 0 | 0 | 0 | 0 |
| G | 0 | 0 | 0 | 0 | 0 |
| ✓ | 0 | 0 | 0 | 0 | 0 |
| ✓ | ✓ | A | C | G | C |

## 2.4 MULTIPLE SEQUENCE ALIGNMENT

Local sequence alignment as well as global sequence alignment is collectively known as pairwise alignment. Sometimes we require alignment of more than two sequences; for instance, the number of sequences may be 10, 20 or maybe 60. As the number of sequences to be aligned increases, the complexity of the alignment algorithm increases.

An application of multiple sequence alignment may be construction of a phylogenetic tree. A phylogenetic tree is the one that shows how closely or distantly organisms are related. For constructing such a tree, conserved regions need to be found. Conserved regions may be located with the help of the multiple sequence alignment. Pairwise alignment may not guarantee an ancestral relationship between sequences of two species, but ancestral relationships may be significantly analyzed with the multiple sequence alignment.

Pairwise sequence alignment requires a two-dimensional matrix. Similarly, sequence alignment of three sequences will require a three-dimensional matrix. Further, a four-dimensional sequence will be used to align four sequences, and so on.

For example, we take three sequences – AGCT, GGT and CGCT – as shown in Figure 2.8.

The vertices to be plotted on a three-dimensional matrix are (1,0,0), (1,0,1), (2,1,2), (2,2,2), (3,2,3) and (4,3,4).

Further, the values in cells of a two-dimensional matrix used to come from three directions, diagonally, horizontally and vertically. But, in the case of an n-dimensional matrix, values will come from various directions into cells of the score matrix, as shown in Figure 2.9.

A multiple sequence alignment can be achieved using alignment tools such as ClustalX, ShadyBox, PrettyBox etc. Following are the steps to conduct a multiple sequence alignment:

| I | 1 | 1 | 2 | 2 | 3 | 4 |
|---|---|---|---|---|---|---|
| | A | - | G | - | C | T |

| J | 0 | 0 | 1 | 2 | 2 | 3 |
|---|---|---|---|---|---|---|
| | - | - | G | G | - | T |

| k | 0 | 1 | 2 | 2 | 3 | 4 |
|---|---|---|---|---|---|---|
| | - | C | G | - | C | T |

![](img/4cb83489753bba67a16c119dae990237_34_0.png)

## FIGURE 2.9 n-Dimensional Matrix for Multiple Sequence Alignment

![](img/4cb83489753bba67a16c119dae990237_34_1.png)

## FIGURE 2.10 NCBI – Multiple Sequence Alignment

Step 1. Open NCBI (https://www.ncbi.nlm.nih.gov/) and obtain protein sequences, as shown in Figure 2.10.
Step 2. After obtaining the protein sequences, run Blast to find similar sequences, as shown in Figures 2.11–2.14.
Step 3. Select taxonomy reports to generate organism reports. Randomly select the accession numbers of generated sequences, as shown in Figure 2.15.
Step 4. Now search the selected sequences on NCBI (Figure 2.16) home page, as used in step 1.
Step 5. The resultant sequences are shown in Figure 2.17.
Step 6. Sequences can be saved in FASTA format or FASTA (text) format by clicking “Summary”, as shown in Figures 2.18 and 2.19.
Step 7. Now copy the FASTA format of all the sequences in a multiple alignment tool, such as Clustal Omega (http://www.ebi.ac.uk/Tools/msa/clustalo/) and run multiple sequence alignments. The result is shown in Figures 2.20 and 2.21.

![](img/4cb83489753bba67a16c119dae990237_35_0.png)

## FIGURE 2.11 NCBI – Multiple Sequence Alignment

![](img/4cb83489753bba67a16c119dae990237_35_1.png)

## FIGURE 2.12 BLAST – Multiple Sequence Alignment (Step 1)

![](img/4cb83489753bba67a16c119dae990237_36_0.png)

## FIGURE 2.13 BLAST – Multiple Sequence Alignment (Step 2)

![](img/4cb83489753bba67a16c119dae990237_36_1.png)

## FIGURE 2.14 Similar Sequences – Multiple Sequence Alignment (Page 1)

![](img/4cb83489753bba67a16c119dae990237_37_0.png)

## FIGURE 2.15 Similar Sequence – Multiple Sequence Alignment (Page 2)

![](img/4cb83489753bba67a16c119dae990237_37_1.png)

## FIGURE 2.16 NCBI – Multiple Sequence Alignment (Step 1)

![](img/4cb83489753bba67a16c119dae990237_38_0.png)

## FIGURE 2.17 NCBI – Multiple Sequence Alignment (Step 2)

![](img/4cb83489753bba67a16c119dae990237_38_1.png)

## FIGURE 2.18 NCBI – Multiple Sequence Alignment (Step 3)
