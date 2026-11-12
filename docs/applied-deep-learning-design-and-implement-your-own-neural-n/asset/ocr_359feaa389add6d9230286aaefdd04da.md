Table 1.16 represents the new distance matrix after building cluster C₁.

| | C₁ (Tarun + Medha) | Bhavik | Anushka | Devam | Farhan | Gouri | Himanshu |
|---|---|---|---|---|---|---|---|
| C₁ (Tarun + Medha) | 0 | | | | | | |
| Bhavik | 49.5 | 0 | | | | | |
| Anushka | 26.5 | 13.96 | 0 | | | | |
| Devam | 42.5 | 36.40 | 27.67 | 0 | | | |
| Farhan | 26.5 | 25.19 | 23.83 | 33.01 | 0 | | |
| Gouri | 54.5 | 16.58 | 20.97 | 27.38 | 47.02 | 0 | |
| Himanshu | 37.5 | 42.37 | 32.66 | 34.42 | 19.05 | 49.10 | 0 |

Table 1.16: Distance after merging “Turun” and “Medha” into cluster “C₁”

Repeat the same procedure for further iterations. We get the following Dendrogram output as shown in figure 1.36:

# Cluster Dendrogram

![](bbox=[0.13, 0.49, 0.82, 0.75])

m hclust (*, "complete")

Figure 1.36: Dendrogram in agglomerative hierarchical clustering for Example 7.