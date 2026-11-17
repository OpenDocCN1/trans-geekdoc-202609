![](bbox=[0.12, 0.1, 0.39, 0.34])

![](bbox=[0.43, 0.1, 0.7, 0.34])

![](bbox=[0.12, 0.35, 0.39, 0.58])

![](bbox=[0.43, 0.35, 0.7, 0.58])

**Figure 11.14** MADmax applied to four synthesized datasets with inliers (gray) and detected outliers/anomalies (black).

+   - $k_{NN}$: number of nearest neighbors to consider during the analysis of candidate anomalies.
+   - $t_{NM}$: this defines a circle of radius **Mfactor** x MADmax around the median of mini-clusters to determine if they are mini-clusters of anomalies.
+   - $k_{NM}$: number of nearest medians to consider in the $k$-nearest medians approach.

These parameters are set once and then used for all datasets. The reason that this is possible is due to the robust standardization carried out in the first step. Without it, the values would have to be adjusted for each dataset, which would be similar to other manually tuned anomaly detectors.

Figure 11.14 shows the four cases (used earlier to evaluate DBSCAN and IF) when MADmax is applied without modification of the parameters. The goal is to demonstrate the value and effectiveness of using robust statistics and robust techniques to detect anomalies. In all cases, the results are quite acceptable. There are a number of other refinements that can be applied to improve the overall performance on realistic datasets.