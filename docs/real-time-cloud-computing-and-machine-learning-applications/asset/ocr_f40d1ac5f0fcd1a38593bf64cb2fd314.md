# Machine Learning Algorithms 139

labelled $C_{BE}$. The distance matrix can then be updated with the new clusters. Distances with clusters having more than one element, as $C_{BE}$, are calculated using the distance between the closest clusters elements (single linkage method). For example, the distance between clusters $C_{BE}$ and $C_A$ is calculated as follows:

```
$d(C_{BE}, C_A) = \min(d(C_B, C_A), d(C_E, C_A)) = \min(1735.0, 1669.0) = 1669$
```

The updated distance matrix is as follows:

| Distance | $C_A$ | $C_{BE}$ | $C_C$ | $C_D$ | $C_F$ |
|---|---|---|---|---|--|
| $C_A$ | 0 | 1669.0 | 0 | 1251.1 | 135.1 |
| $C_{BE}$ | 1669.0 | 0 | 1132.0 | 418.0 | 1534.0 |
| $C_C$ | 537.0 | 1132.0 | 0 | 714.1 | 402.1 |
| $C_D$ | 1251.1 | 418.0 | 714.1 | 0 | 1116.1 |
| $C_F$ | 135.1 | 1534.0 | 402.1 | 0 | 0 |

From the above distance matrix, it is observed that $C_{CC}$ and $C_{CF}$ can be merged into a single cluster labelled $C_{CF}$ because they are the closest ones. The distance matrix is again updated with new distances calculated using the single linkage method:

| Distance | $C_A$ | $C_{BE}$ | $C_{CF}$ | $C_D$ |
|---|---|---|---|--|
| $C_A$ | 0 | 1669.0 | 135.1 | 1251.1 |
| $C_A$ | 1669.0 | 0 | 1132.0 | 418.0 |
| $C_A$ | 135.1 | 1132.0 | 0 | 714.1 |
| $C_A$ | 1251.1 | 418.0 | 714.1 | 0 |

The closest clusters are now clusters $C_A$ and $C_{CF}$ which are merged into a cluster labelled $C_{AC}$. The distance matrix is updated:

| Distance | $C_{AC}$ | $C_{BE}$ | $C_D$ |
|---|---|---|--|
| $C_{AC}$ | 0 | 1132.0 | 714.1 |
| $C_{AC}$ | 1132.0 | 0 | 418.0 |
| $C_{AC}$ | 714.1 | 418.0 | 0 |

The closest clusters are now clusters $C_{BE}$ and $C_D$ which are merged into a cluster labelled $C_{BDE}$. At this point, the clustering process is stopped because the total number of clusters is finally 2. The first cluster $(C_{AC})$ consists of cars A, C and F and the second cluster $(C_{BDE})$ consists of cars B, D and E.