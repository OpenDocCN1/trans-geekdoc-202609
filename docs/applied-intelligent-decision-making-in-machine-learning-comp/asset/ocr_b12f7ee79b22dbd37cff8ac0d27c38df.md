# Forecasting Air Quality in India

TABLE 6.10
Year-Wise Silhouette Coefficient Metric for Base Clustering Model

| Year | Hierarchical clustering | Fuzzy C means | K means |
|---|---|---|--|
| 2016 | 0.657571268 | 0.723436528 | 0.684701362 |
| 2017 | 0.602559157 | 0.707689134 | 0.598002859 |
| 2018 | 0.632259157 | 0.658438986 | 0.521425682 |

For a single sample, the Silhouette Coefficient s is given by:

```
s(x) = b(x) - \frac{a(x)}{\max[b(x),a(x)]} \quad (6.7)
```

The value is bounded by -1 and +1; -1 indicates poor or incorrect clustering; values close to +1 indicate dense clustering which are well separated. Values near zero indicate overlapping clusters. The base clustering results given in Table 6.10 include the Silhouette Coefficient values for the years 2016, 2017, and 2018. In comparison to the evaluation metrics on the base clustering results, the Silhouette Coefficient for the final METIS output clusters are higher, which proves the efficiency of the ensemble method. The base clustering results also show high Silhouette coefficient values of around 0.521425682 to 0.723436528. The highest Silhouette Coefficient value of the ensemble clustering technique, however, was calculated as 0.751745327.

# 6.5.2 CALINSKI-HARABAZ INDEX

Another evaluation metric is the Calinski-Harabaz index, which is also named the variance ratio criterion. The index is the proportion of the sum of intra-cluster variance to the inter-cluster variance for all clusters (where the sum of the square of the distances is taken as). The Calinski-Harabaz score is defined as the proportion of the mean inter-cluster variance to the intra-cluster variance where $E$ represents a set of data size $n_E$ has been clustered into $k$ clusters.

```
s = \frac{t_r(B_k)}{t_r(W_k)} \times \frac{n_E - k}{k - 1} \quad (6.8)
```

the trace of the intra-cluster variance matrix is represented by $t_r(W_k)$ and the trace of the inter-cluster variance matrix. The intra and inter-cluster variance matrices are defined as:

```
W_k = \sum_{q=1}^k \sum_{x \in C_q} (x - c_q)(x - c_q)^T \quad (6.9)
```