# Protease Cleavage Pattern Discovery

easily. On the other hand, a non-cleaved peptide ($x_n \in \Omega^-$) will show a small homology score (similarity) with the bio-basis peptides. The non-cleaved peptides will not maintain any amino acid composition pattern or trend, but a random distribution. In other words, each of 20 amino acids has the same probability to appear at each residue of a non-cleaved peptide. Therefore, it is expected that the homology scores of cleaved peptides and the homology scores of non-cleaved peptides should show different densities in theory.

Based on the above analysis, BBFNN is designed in the following ways. Suppose there are $K$ bio-bases. A non-numerical peptide is mapped to a $K$-dimensional space, i.e., $\mathcal{B}(x_n, s_1), \mathcal{B}(x_n, s_2), \dots,$ and $\mathcal{B}(x_n, s_K)$. A linear function is generated for combining K bio-basis functions through the weighting parameters $w_k$.

```
$$\sum_{k=1}^K w_k \mathcal{B}(x_n, s_k) \quad (3.42)$
```

It is expected that this linear combination of the bio-basis functions will have a bimodal distribution if weights $(w_k)$ have been well-estimated. Such a bimodal distribution is expected to fit the classification of peptides in terms of peptide status $(y_n)$. A linear classifier can then be built in the $K$-dimensional bio-basis function space,

```
$y_n = \sum_{k=1}^K w_k \mathcal{B}(x_n, s_k) \quad (3.43)$
```

Suppose **X** is a collection of peptides and **S** is a matrix of all peptides mapped to this $K$-dimensional bio-basis function space. The matrix **S** has $N$ rows for $N$ peptides and $K$ columns for $K$ bio-bases. A target vector of classification labels is denoted by **y**,

```
$**y** = (y_1, y_2, \dots, y_N)^T \quad (3.44)$
```

Finally, a weight vector is represented by **w**.

```
$**w** = (w_1, w_2, \dots, w_K)^T \quad (3.45)$
```