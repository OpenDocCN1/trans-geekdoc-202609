# Whole Genome Pattern Discovery

However, the identity percentages dropped to 51.1% and 49.8% when comparing MT042778 (SARS-CoV-2) with QANK0102681 (Yersinia pastis) using the Needleman-Wunsch algorithm and the Smith-Waterman algorithm. Two groups of scores show a significant difference. Therefore, the alignment-based sequence comparison approach has the discrimination power to separate species based on the sequence homology alignment scores. This also demonstrates that the sequence structure differentiation determines the species differentiation.

Table 19. The alignment results of aligning MT042778 with AB889999 (SARS-CoV) and of aligning MT042778 with QANK0100268 (Yersinia pastis) using the alignment-based sequence comparison approach, i.e., the Needleman-Wunsch algorithm

| | Align with | Align with |
|---|---|---|---||
| | AB889999 | QANK0100268 |
| | Needleman | Smith | Needleman | Smith |
| Alignment length | 143 | 113 | 327 | 259 |
| Identical pairs | 109 | 109 | 167 | 129 |
| Identity percentage (%) | 76.2 | 96.5 | 51.1 | 49.8 |
| Gap percentage (%) | 21.7 | 0.9 | 42.8 | 20.5 |

# 7.4.1 The k-mers approach

Comparing sequences using homology alignment approaches, either global or local, is very costly as aforementioned. The alignment-free sequence comparison approach is therefore of great interest. Most alignment-free sequence comparison approach explore the pattern of the sequence statistics for sequence comparison and are still widely used in many applications [Lichtblau, 2019, Randhawa, et al., 2020; Rohling, et al., 2020].

One of the basic principles of the alignment-free sequence comparison approach is to use the pattern of the sequence statistics to represent sequences [Le and Huynh, 2019; Nguyen, et al., 2019; Guo, et al., 2020]. This process is called a feature extraction process. Suppose the $n^{th}$ sequence is denoted by $\mathbf{s}_n$. The mapping between $\mathbf{s}_n$ and a feature vector $\mathbf{x}_n$ is formulated by the following equation, where $\mathcal{C}$ is a set of the nucleic acids or a set of amino acids, $\ell_n$ stands for the length of the $n^{th}$ sequence and $d$ stands for the feature space dimension,