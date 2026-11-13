# Example no. 5 (Python): Clustering fire resistance of RC columns.

I will be continuing the same example we covered in our discussion on clustering. This would be a good time to review that particular example.82

We will apply the explainable trees approach to understand the reasoning behind such clustering analysis. Table 7.3 shows the first and second splits taken in each algorithm, along with the number of splits and leaves.

I will now go over two explainable trees obtained from the K-Means and Hierarchical clustering models (plotted in Figures 7.15 and 7.16).83 Overall, we can also see that the entropy reduces with each split (as reflected by the higher intensity in color). The first split from the K-Means model takes place at the compressive strength of 71 MPa. From there, columns of fc > 71 MPa are moved into cluster no. 1, and the rest are further analyzed. The next split occurs in columns with a length (L) longer than 4.3 m joining cluster no. 4, and the remaining columns continue the analysis. The third split occurs at the concrete cover (C) with columns of a smaller cover thickness (less than 36.5 mm) joining cluster no. 2. Columns with pin-pined conditions are examined against the level of applied loading, and columns with higher rigidity (K ≤ 0.85) are examined against the steel reinforcement ratio.

# Table 7.3 Splits of algorithms.

| Split | K-Means | Hierarchical | Fuzzy-C-Means | DBSCAN |
|---|---|---|---|---|
| First Split | $f_c$ | C | $f_c$ | L |
| Second Split | L | C, $f_c$ | K, P | $f_o$ ex |
| Number of split node | 7 | 11 | 9 | 12 |
| Number of leaf node | 8 | 12 | 10 | 13 |

![](bbox=[0.103, 0.445, 0.615, 0.83])

# Figure 7.15 Explainable tree for K-Means.

82 Let me recap what we did. We have used four clustering algorithms to cluster over 140 RC columns. Our multi-algorithm analysis has noted that the examined RC columns fall under four clusters.

83 . And will leave the other two trees for you to try and compare your analysis to that shown at the end of this example. You have seen such trees earlier, but we did not discuss them then. I promised we will. Here we go!