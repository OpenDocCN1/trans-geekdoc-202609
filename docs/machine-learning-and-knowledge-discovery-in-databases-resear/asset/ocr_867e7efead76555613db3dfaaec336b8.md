# Table 2. Comparison on real-world datasets (lower is better). GRAPHWEAVE is best, or close to best, for most measures and datasets.

| | Degree | Pagerank | Cut sizes | Conductance | Modularity | Clustering Coefficient | ORBIT | Max Flow | Resistance |
|---|---|---|---|---|---|---|---|---|---|
| Cora | | | | | | | | | |
| DiGress | 1.73 | 0.10 | 0.99 | 0.12 | 0.09 | 1.06 | 0.25 | 1.63 | **0.05** |
| GSDM | 0.34 | 0.13 | 7.53 | 0.20 | 0.38 | 1.40 | 5.37 | 41.11 | 2.13 |
| GDSS | **0.01** | 0.11 | 32.23 | 0.35 | 0.60 | 1.70 | 95.62 | 117.72 | 2.26 |
| GRASP | 0.03 | 5.30 | 0.71 | 0.85 | 1.27 | 1.14 | 0.47 | 7.15 | 0.77 |
| GraphRNN | 13.13 | **0.02** | 0.20 | 0.44 | **0.07** | 1.08 | 0.30 | 3.26 | 7.18 |
| **GraphWeave** | **0.01** | **0.02** | **0.18** | **0.11** | **0.07** | **0.67** | **0.16** | **0.18** | 0.69 |
| Pubmed | | | | | | | | | |
| DiGress | 10.25 | **0.04** | 0.36 | 0.07 | 0.45 | 0.43 | 0.45 | 1.06 | 0.18 |
| GSDM | 0.37 | 0.16 | 4.04 | **0.02** | 0.06 | 1.02 | 4.07 | 15.79 | 1.42 |
| GDSS | **0.00** | 0.28 | 14.71 | 0.05 | 0.20 | 1.65 | 80.79 | 51.05 | 1.57 |
| GRASP | 0.02 | 17.31 | 0.21 | 2.65 | 3.45 | 1.45 | 0.98 | 0.67 | 0.21 |
| GraphRNN | 11.50 | 0.15 | 0.26 | 0.13 | **0.04** | 0.38 | 0.20 | 1.07 | 6.83 |
| **GraphWeave** | 0.07 | **0.07** | **0.03** | 0.11 | 0.07 | **0.26** | **0.03** | **0.06** | **0.01** |
| Citeseer | | | | | | | | | |
| DiGress | 8.87 | **0.04** | 0.60 | **0.02** | 0.08 | 1.19 | 0.24 | 0.99 | 0.64 |
| GSDM | 0.21 | 0.13 | 3.71 | **0.02** | 0.10 | 1.49 | 8.30 | 20.45 | 1.41 |
| GDSS | 0.11 | 0.13 | 11.42 | 0.09 | 0.27 | 2.02 | 90.31 | 54.23 | 1.54 |
| GRASP | **0.08** | 0.79 | 2.45 | 0.23 | 0.32 | 1.87 | 16.37 | 13.13 | 0.75 |
| GraphRNN | 14.09 | 0.10 | 0.24 | 0.17 | **0.00** | 1.32 | **0.05** | 1.91 | 3.95 |
| **GraphWeave** | 0.17 | 0.07 | **0.03** | 0.13 | 0.08 | **0.48** | 0.09 | **0.23** | **0.23** |
| QM9 | | | | | | | | | |
| DiGress | 0.06 | 0.01 | 0.11 | **0.27** | **0.23** | 0.35 | 0.08 | **0.14** | 0.04 |
| GSDM | 0.25 | 0.03 | 2.60 | 0.98 | 0.76 | 1.76 | 4.09 | 3.19 | 0.91 |
| GDSS | 0.09 | 0.20 | 0.85 | 0.61 | 0.48 | 0.94 | 1.22 | 1.01 | 0.30 |
| GRASP | **0.01** | 0.11 | 0.06 | 0.54 | 0.39 | **0.03** | 0.12 | 0.19 | **0.03** |
| GraphRNN | **0.01** | 0.09 | 0.22 | 0.63 | 0.38 | 0.64 | 0.39 | 0.29 | **0.03** |
| **GraphWeave** | 0.03 | **0.00** | **0.02** | 0.39 | 0.31 | 0.47 | **0.06** | 0.33 | 0.07 |
| Proteins | | | | | | | | | |
| DiGress | 5.94 | 0.33 | 1.03 | 1.87 | 3.41 | 7.19 | 4.64 | 4.17 | 0.61 |
| GSDM | 0.74 | **0.00** | 10.20 | 0.10 | 0.75 | 3.74 | 2254.53 | 35.68 | 1.63 |
| GDSS | 0.78 | 0.01 | 36.58 | 0.19 | 1.11 | **2.95** | 22210.10 | 96.64 | 1.69 |
| GRASP | 0.89 | 31.57 | 2.51 | 14.43 | 8.98 | 5.40 | 1010.18 | 10.48 | **0.60** |
| GraphRNN | 2.30 | 0.16 | 0.24 | 0.19 | **0.06** | 4.88 | **1.51** | 4.01 | 12.04 |
| **GraphWeave** | **0.01** | 0.03 | **0.00** | **0.04** | **0.06** | 5.62 | 2.33 | **0.66** | 3.25 |

Table 3 shows that *Integer* is between 20% – 55% better than *Convex*, and both are significantly better than *Random*. The difference between *Integer* and *Convex* is because the latter needs to threshold edges from [0, 1] to {0, 1}. This thresholding step (Eq. 7) can increase the error in RWT reconstruction.

**Wall-Clock Time:** Figure 3 compares the wall-clock times for the various methods. We see that GRAPHWEAVE has the fastest training time, and has reasonable generation time. Furthermore, GRAPHWEAVE is *10x faster than its closest competitor (DiGress)*.

**Sensitivity Analysis:** We investigate the sensitivity of our measures to variations in the hyperparameters $c$, $\alpha$, and $k$. Recall that $c$ controls the number of bins in the binning function $B(\mathbf{v})$, $\alpha$ smooths the RWTs, and $k$ is the length of an RWT. All the previous experiments used the baseline setting of ($c = 3, k = 10, \alpha = 0.9$). We ran experiments varying one hyperparameter at a time. We report all metrics normalized relative to their values in the baseline setting. Hence, a normalized value greater than 1 implies worse performance than the baseline, and lower than 1 implies better performance.