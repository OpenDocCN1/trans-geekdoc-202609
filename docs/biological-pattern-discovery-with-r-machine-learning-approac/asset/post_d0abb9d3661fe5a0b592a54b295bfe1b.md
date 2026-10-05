
# Whole Genome Pattern Discovery

However, the identity percentages dropped to 51.1% and 49.8% when comparing MT042778 (SARS-CoV-2) with QANK0102681 (Yersinia pastis) using the Needleman-Wunsch algorithm and the Smith-Waterman algorithm. Two groups of scores show a significant difference. Therefore, the alignment-based sequence comparison approach has the discrimination power to separate species based on the sequence homology alignment scores. This also demonstrates that the sequence structure differentiation determines the species differentiation.

Table 19. The alignment results of aligning MT042778 with AB889999 (SARS-CoV) and of aligning MT042778 with QANK0100268 (Yersinia pastis) using the alignment-based sequence comparison approach, i.e., the Needleman-Wunsch algorithm

| | Align with | Align with |
|---|---|---|------|
| | AB889999 | QANK0100268 |
| | Needleman | Smith | Needleman | Smith |
| Alignment length | 143 | 113 | 327 | 259 |
| Identical pairs | 109 | 109 | 167 | 129 |
| Identity percentage (%) | 76.2 | 96.5 | 51.1 | 49.8 |
| Gap percentage (%) | 21.7 | 0.9 | 42.8 | 20.5 |

## 7.4.1 The k-mers approach

Comparing sequences using homology alignment approaches, either global or local, is very costly as aforementioned. The alignment-free sequence comparison approach is therefore of great interest. Most alignment-free sequence comparison approach explore the pattern of the sequence statistics for sequence comparison and are still widely used in many applications [Lichtblau, 2019, Randhawa, et al., 2020; Rohling, et al., 2020].

One of the basic principles of the alignment-free sequence comparison approach is to use the pattern of the sequence statistics to represent sequences [Le and Huynh, 2019; Nguyen, et al., 2019; Guo, et al., 2020]. This process is called a feature extraction process. Suppose the $n^{th}$ sequence is denoted by $\mathbf{s}_n$. The mapping between $\mathbf{s}_n$ and a feature vector $\mathbf{x}_n$ is formulated by the following equation, where $\mathcal{C}$ is a set of the nucleic acids or a set of amino acids, $\ell_n$ stands for the length of the $n^{th}$ sequence and $d$ stands for the feature space dimension,

$$\mathbf{s}_n \in \mathcal{C}^{\ell_n} \Rightarrow \mathbf{x}_n \in \mathcal{R}^d \quad\quad\quad\quad\quad\quad\quad(7.14)$$

Suppose all sequences $S$ have been mapped to a feature space $X$. A machine learning model can be constructed based on the feature space as shown below, where $\Omega_k$ is a subspace to be generated using a cluster analysis model or a classification analysis model $f(X)$,

$$f(X) \Rightarrow U\Omega_k \quad\quad\quad\quad\quad\quad\quad(7.15)$$

It is understood that different species will represent different sequence statistics in their genomes. A nucleotide sequence or a protein sequence is therefore assumed to be a string of genetic recombination of the nucleic acids or the amino acids. Therefore they will form different distributions of sequence statistics. In natural language processing, a library of basic words constitutes the basis for the classification of articles or books. A nucleotide sequence or a protein sequence of base can be treated as an article or a book. It should contain some basic sequence statistics pattern about how short-sequences of the nucleic acids or the amino acids are distributed within a genome or a whole sequence. Therefore, extracting the sequence statistics to generate the frequency or library of sub-sequences from a sequence can be used to compare or classify sequences, hence species.

The sequence statistics mainly represent the distribution of words, which are consecutive sub-strings within a sequence string. These substrings or words are called k-mers in the application to sequence comparison. For instance, any nucleotide sequence is a chain or a string of four nucleic acids, $\mathbf{s}_n \in (A, C, G, T)^n$. In case when $k=1$ using the k-mers approach to represent sequence spaces, $\mathbf{x}_n \in \mathcal{R}^4$. There are 16-mer words such as AA, AC, AG, AT, CA, etc. Therefore, $\mathbf{s}_n \Rightarrow \mathbf{x}_n \in \mathcal{R}^{16}$ if 2-mers are used to represent nucleotide sequences. There are 64-mer words such as AAA, AAC, etc. in a nucleotide sequence. Therefore, $\mathbf{s}_n \in \mathcal{R}^{64}$ if 3-mers are used to represent nucleotide sequences.

The collection of all words for a specific size $k$ is called a word set. Counting the times each word occurs in a sequence thus builds up a sequence statistics library or the word library. Similar sequences are assumed to have similar sequence statistics patterns.

The above sequences were used again to examine whether this is true. Figure 7.8 shows the frequency pattern of three sequences (SARS-CoV, SARS-CoV-2 and Yersinia pastis) based on 3-mer words. The frequency of some 3-mer words demonstrated a significant difference between three sequences.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_361_0.png)

Fig. 7.8. 3-mer pattern for MT042778 (M), AB889999 (A) and QANK01002681 (Q).

Table 7.20 shows the correlation coefficients, it can be seen that the correlation coefficient between the 3-mer vector ($X_{SARS-CoV}$) of the SARS-CoV and the 3-mer vector ($X_{SARS-CoV-2}$) of the SARS-CoV-2 sequences was small, being 0.868. The correlation coefficient between $X_{SARS-CoV}$ and the 3-mer vector ($X_{Yersinia}$) of the Yersinia pastis was small, being 0.192. The correlation coefficient between $X_{SARS-CoV-2}$ and $X_{Yersinia}$ was small, being 0.079.

Table 7.20. Correlation coefficients for MT042778, AB889999 and QANK01002681.

| | SARS-CoV | SARS-CoV-2 | Yersinia |
|---|---|---|---|
| MT042778 | 1.0 | 0.868 | 0.079 |
| AB889999 | 0.868 | 1.0 | 0.192 |
| QANK0100268 | 0.079 | 0.192 | 1.0 |

The above sequences were used again to examine whether this is true. Figure 7.8 shows the frequency pattern of three sequences (SARS-CoV, SARS-CoV-2 and Yersinia pastis) based on 3-mer words. The frequency of some 3-mer words demonstrated a significant difference between three sequences.

![](img/c3caa39b5c0f40fb2a44f2ab6e940f78_361_0.png)

Fig. 7.8. 3-mer pattern for MT042778 (M), AB889999 (A) and QANK01002681 (Q).

Table 7.20 shows the correlation coefficients, it can be seen that the correlation coefficient between the 3-mer vector ($X_{SARS-CoV}$) of the SARS-CoV and the 3-mer vector ($X_{SARS-CoV-2}$) of the SARS-CoV-2 sequences was small, being 0.868. The correlation coefficient between $X_{SARS-CoV}$ and the 3-mer vector ($X_{Yersinia}$) of the Yersinia pastis was small, being 0.192. The correlation coefficient between $X_{SARS-CoV-2}$ and $X_{Yersinia}$ was small, being 0.079.
