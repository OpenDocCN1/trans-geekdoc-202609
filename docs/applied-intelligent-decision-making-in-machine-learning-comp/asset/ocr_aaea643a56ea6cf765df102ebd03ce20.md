# Applied Intelligent Decision Making in Machine Learning

8. As the optimal clusters are known, the base clustering techniques are applied, which are hierarchical clustering using ward linkage, fuzzy C-means clustering, and K-means clustering.

9. The results from the base models are represented in binary form using Equation 6.1 of the object membership in the respective clusters.

10. Each object weight is obtained from every pair of objects using Equations 6.2-6.

11. The Jaccard coefficient is calculated as the proportion of the intersection of objects to the union of different clusters. Cluster weighting assignment is calculated using Jaccard similarity (using Equation 6.6).

12. The final cluster weights are used to form the similarity matrix which is an input to the graph-partitioning algorithm METIS.

13. METIS uses the list of partition indices which are used to merge and obtain the final ensemble clustering output.

14. The final cluster labels along with the original pre-processed data are used to measure the effectiveness of the ensemble clustering technique.

15. As truth labels are not available in the case of clustering, intrinsic evaluation metrics using the Davies–Bouldin Index, the Calinski-Harabasz Index, and the Silhouette Coefficient are used.

The evaluation metric results for the base clustering and ensemble clustering are then compared.

From the results of each base clustering algorithm, the cluster labels are represented as a binary membership value using Equation 6.1 (Alqashi and Wang 2019). If the object is present in the particular cluster, then the value is 1, else 0. Figure 6.4 gives the optimal number of clusters for each base clustering algorithm, as mentioned in Table 6.1. The representation is given for hierarchical clustering for the years 2016, 2017, and 2018. The graph shows the optimal number of clusters for the fuzzy C-means and K-means algorithm. So the co-association matrix of 6 	imes 6 is produced. The sample data is given in Table 6.2.

```
\delta(x_i,c_j) = \begin{cases} 1, & \text{if } x_i \in c_j, \forall i=1..n<0 \ 0, & \text{if } x_i \notin c_j \end{cases} \quad (6.1)
```

# TABLE 6.1
Optimal Number of Clusters for Base Clustering

| K-means | Fuzzy C Means | Hierarchical Clustering |
|---|---|---|
| 2016 | 2 | 2 |
| 2017 | 2 | 2 |
| 2018 | 2 | 2 |