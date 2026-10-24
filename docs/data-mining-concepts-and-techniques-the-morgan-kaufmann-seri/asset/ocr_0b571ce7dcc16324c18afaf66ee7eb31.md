| 10 | 50 | 30 | 70 | 20 |
|---|---|---|---|---|
| 20 | 100 | 50 | 1000 | 30 |
| 50 | 100 | 90 | 120 | 80 |
| 0 | 80 | 20 | 100 | 10 |

# FIGURE 9.10
Bicluster with coherent evolutions on rows.

example, Fig. 9.10 shows a bicluster with coherent evolutions on rows. Symmetrically, we can define biclusters with coherent evolutions on columns.

Next, we study how to mine biclusters.

# 9.3.3 Biclustering methods

The previous specification of the types of biclusters only considers ideal cases. In real data sets, such perfect biclusters rarely exist. When they do exist, they are usually very small. Instead, random noise can affect the readings of \(e_{ij}\) and thus prevent a bicluster in nature from appearing in a perfect shape.

There are two major types of methods for discovering biclusters in data that may come with noise. **Optimization-based methods** conduct an iterative search. At each iteration, the submatrix with the highest significance score is identified as a bicluster. The process terminates when a user-specified condition is met. Due to cost concerns in computation, greedy search is often employed to find local optimal biclusters. **Enumeration methods** use a tolerance threshold to specify the degree of noise allowed in the biclusters to be mined and then try to enumerate all submatrices of biclusters that satisfy the requirements. We use the \(\delta\)-Cluster and MaPle algorithms as examples to illustrate these ideas.

# Optimization using the \(\delta\)-cluster algorithm

For a submatrix, \(I \times J\), the mean of the \(i\)th row is

```
\(e_{iJ} = \frac{1}{|J|} \sum_{j \in J} e_{ij}.\) (9.18)
```

Symmetrically, the mean of the \(j\)th column is

```
\(e_{Ij} = \frac{1}{|I|} \sum_{i \in I} e_{ij}.\) (9.19)
```

The mean of all elements in the submatrix is

```
\(e_{IJ} = \frac{1}{|I||J|} \sum_{i \in I, j \in J} e_{ij} = \frac{1}{|I|} \sum_{i \in I} e_{iJ} = \frac{1}{|J|} \sum_{j \in J} e_{Ij}.\) (9.20)
```

The quality of the submatrix as a bicluster can be measured by the *mean-squared residue value* as

```
\(H(I \times J) = \frac{1}{|I||J|} \sum_{i \in I, j \in J} (e_{ij} - e_{iJ} - e_{Ij} + e_{IJ})^2.\) (9.21)
```