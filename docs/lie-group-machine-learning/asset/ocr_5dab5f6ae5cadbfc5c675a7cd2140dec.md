dimensional space, as shown in Figure 12.11(b). Because the interval between the original data is very close, especially the sample points between the two ends of the manifold, there are some non-nearest neighbour sample points. Hence the reduced dimensionality results in a small distortion at both ends of the coordinates, as shown in Figure 12.11(c).

# ## 12.6 Clustering algorithm based on the topological invariance spectral estimation of image feature manifolds

If the dimension reduction problem is regarded as removing highly correlated (redundant) characteristics or merging these related (redundant) features, then the clustering technique can work here [20]. The clustering algorithm merges the rows of the matrix and uses a few clustering centres to represent all the data. Then, the topological invariance spectrum estimation clustering algorithm of image feature manifolds (TISC) is presented.

```
**Algorithm 12.3:** Topological invariance spectral estimation clustering of image feature manifolds (TISC)
**Input:** Sample set $S$, the corresponding graph of the sample set $G$, Characteristic vector number $M$, Cluster number $K$, Upper bound of standard cut set $Ncut$, parameter $n$;
**Output:** Minimum distribution partition $(A_1, A_2, \ldots, A_K)$
**Step 1:** Construct the similarity matrix of sample sets $W$, degree matrix $D$, and perform initialisation. Given a distribution $\cup_{j=1, \ldots, K}A_j = G$, satisfying $A_i \cap A_{j \neq i} = \emptyset$;
**Step 2:** Compute the first $k$ eigenvalues $\lambda_1, \ldots, \lambda_k$ of the matrix $L = I - D^{-1}W = U \Lambda U^T$ and corresponding feature vectors $x_1, \ldots, x_k$. The new matrix $X'$ is obtained by regularisation of the feature vectors. Construct the matrix $X' = [x_1', \ldots, x_k'] \in R^{n \times k}$
**Step 3:** Let $k = 1$, $ncut(A(k), W) = Ncut$, compute $e(M) = ncut(A, W) - \sum_{i=1}^{K} \lambda_i/\lambda_{M-1} - \lambda_k$;
**Step 4:** If $k \le n$ and $ncut(A(k+1), W) \le ncut(A(k), W) + \varepsilon(M)\lambda_k$, then $ncut(A(k), W) = Ncut(A(k), W)$, $k = k+1$, return Step 4; Else, return $ncut(A(k), W) = \infty$;
**Step 5:** Let $min = ncut(A(k), W)$, minimum partition $\cup_{j=1, \ldots, min}A_j$ is obtained.
```

# ## 12.7 Summary

The algorithm of spectral estimation for topological invariance of image feature manifolds was proposed for high-dimensional data space, which is ubiquitous in real life. For visualisation in the research field of machine vision, it is often necessary to embed high-dimensional data into the low-dimensional manifold space, realise effective dimensionality reduction of feature manifolds, or perform unsupervised clustering of data sets. Because the data samples have high similarity characteristics within the sample, effectively maintaining the geometric characteristics of the internal structure