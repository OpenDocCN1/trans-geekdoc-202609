# Table 1.4 Comparison of LS and Theil estimations of Figures 1.1(a) and (d).

| Case (LSE) | Estimators | Coefficient | s.e | t-value | p-value |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Figure 1.1(a) | \(\hat{\theta}_n^{LS}\) | -234.2 | 23.4 | -10.0 | <0.001 |
| | \(\hat{\beta}_n^{LS}\) | 0.120 | 0.01 | 10.1 | <0.001 |
| Figure 1.1(d) | \(\hat{\theta}_n^{LS}\) | -983.9 | 325.2 | -3.0 | 0.006 |
| | \(\hat{\beta}_n^{LS}\) | 0.504 | 0.166 | 3.0 | 0.006 |
| Case (Theil) | Estimators | Coefficient | s.e | T-statistic | z* |
| Figure 1.1(a) | \(\hat{\theta}_n^{\text{Theil}}\) | -201.8 | 0.06 | – | – |
| | \(\hat{\beta}_n^{\text{Theil}}\) | 0.104 | 0.02 | 107.0 | -1.23 |
| Figure 1.1(d) | \(\hat{\theta}_n^{\text{Theil}}\) | -270.4 | 0.32 | – | – |
| | \(\hat{\beta}_n^{\text{Theil}}\) | 0.139 | 0.18 | 116.5 | -0.96 |

```
\(\bar{x}_T = \frac{n'(n' + 1)}{4}, \quad s_T = \sqrt{\frac{n'(n' + 1)(2n' + 1)}{24}}, \quad \text{and } z^* = \frac{T - \bar{x}_T}{s_T},\)
```

where \(\bar{x}_T\) is the mean and \(s_T\) is the standard deviation, and \(z^*\) is the z-score for an approximation of the data to the normal distribution. To perform a two-sided test, we reject \(\mathcal{H}_o\) if \(z_{\text{critical}} < |z^*|\). Specifically, for \(\alpha = 0.05, z_{\text{critical}} = 1.96\). In the case of Figure 1.1(d), we have \(n' = 24\) and obtain \(T = 116.5\) (the negative sum is smaller), so \(z^* = (116.5 - 150)/35 = -0.96\). Therefore, we cannot reject \(\mathcal{H}_o\). This suggests there is no difference in the two samples. Similarly, for Figure 1.1(a), we find that \(T = 107.0\) so that \(z^* = (107.0 - 150)/35 = -1.23\). Again, we cannot reject \(\mathcal{H}_o\) suggesting no difference in the two samples. Table 1.4 shows the results of this approach\(^4\) for the telephone data set in the two cases of Figures 1.1(a) and 1.1(d).

# 1.4 Outliers and their Detection

Typically, outliers are created by errors in transcribing the data, or noise in the data collection process, or simply anomalies in data values. It is relatively easy to observe an outlier on a graph in a one-variable setting, but much more difficult to identify in the case of multiple linear regression. Hence, a clear