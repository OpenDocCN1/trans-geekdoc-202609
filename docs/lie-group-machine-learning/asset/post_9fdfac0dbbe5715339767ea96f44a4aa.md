
## 12.5.1 Spectral estimation learning algorithm for the topological invariance of image feature manifolds

Many existing manifold learning algorithms use the LLE feature vectors as features for pattern recognition, such as ISOMAP or other feature mapping methods. In this section, only the eigenvectors corresponding to the maximal two eigenvalues of the Laplacian operator in the manifold are used as features according to the spectral characteristics of the manifold, and pattern recognition and data dimension reduction can be achieved.

**Algorithm 12.2: Spectral estimation learning algorithm for topological invariance of image feature manifolds**

- **Input:** Original data set $X=\{x_i\}$
- **Output:** Reconstructed data set $X'=\{x_i'\}$

1. Determine whether the data set satisfies the four hypothetical conditions given in 12.4.1. If the local dimension of the image feature manifold is unknown, the local dimension $d$ of the manifold can be computed by the maximum likelihood estimation algorithm.
2. Run the LLE algorithm on the data sample set, and return the second feature vector $\{Y_n\}$, where $n$ is the number of required eigenvectors.
3. (Find the local extremum of each feature vector $Y_j$) For each data point, the corresponding neighbourhood $[x_{e_j}]$ is obtained by the relation matrix $E$. If $V_{e,j} \in \{x_{e_j}\}$ satisfies $Y_k(x_i) > Y_k(x_{e})$ (or $Y_k(x_i) < Y_k(x_{e,j})$), then $x_i$ is a local maximum (or local minimum). The number of local extrema represents the degree of analysis of the eigenvector.
4. (Calculate local maximum and minimum curves) **Initialisation**: let $[x_{ic}] = \{x_i\}$. If $Y_k(x_i) \times Y_k(x_{e,i}) > 0$, the adjacent point $x_{e,i}$ is added to the set $[x_{ic}]$ in turn. For all points in $[x_{ic}]$, repeat step (4) until there is no new point before adding the set. Each $[x_{ic}]$ is a curve corresponding to the nonlinear structure of the manifold.

## 12.5.2 Algorithm analysis

Local curves can preserve the nonlinear structure characteristics of manifolds. Because the local curve satisfies the continuous mapping in the bounded domain, there exists an extreme value in each neighbourhood. For a given vector $x_i$, its $k$ nearest neighbours can be denoted as $x_{e1}$, $x_{e2}$, ..., $x_{ek}$. Suppose that $x_{e1}$, $x_{e2}$, ..., $x_{ek}$ satisfies

$$Y_k^{M^n}(x_{e1}) \le Y_k^{M^n}(x_{e2}) \le \cdots \le Y_k^{M^i}(x_{ek})$$

If $x_i$ is not a local extremum, the above expression can be rewritten as

$$Y_k^M(x_{e1}) \le \cdots \le Y_k^M(x_{e_i}) \le Y_k^{M^n}(x_i) \le Y_k^{M^i}(x_{e_{i+1}}) \le \cdots \le Y_k^{M^i}(x_{e_k})$$

then $x_i$ is in its neighbourhood.

If $x_i$ is a local extremum, suppose that $x_i$ is a local maximum:

$$Y_k^{M^n}(x_{e1}) \le Y_k^{M^n}(x_{e2}) \le \cdots \le Y_k^{M^i}(x_{ek}) \le Y_k^{M^i}(x_i)$$

then $x_i$ is outside its neighbourhood.

If $x_i$ is the centre of its neighbourhood, $y_i$ should be the centre of its corresponding neighbourhood $\{y_{ej} = Y^{Mn}_{k}(x_{ej})\}$, so that the local reconstruction error $|y_i - \sum_{j=1}^{k} w_{ej}Y^{Mn}_{k}(x_{ej})|^2$ is minimised. Similarly, if $x_i$ is far from the centre of its neighbourhood, then $y_i$ should also take the local extrema away from the centre of the neighbourhood $\{y_{ej}\}$.

The curves of characteristic vectors of different scales maintain nonlinear manifold structures with different curvatures. In this paper, the local tangent space is selected to reconstruct the sample points, the local reconstruction error is minimised, and the reconstruction error is not increased in the global adjustment process. If the same scale criterion is chosen to adjust each local structure of the manifold, then the reconstruction point $x_i' = \sum_{j=1}^{k} w_{ej}x_{ej}$ will deviate from the sample point $x_i$ and increase its reconstruction error. Compared with the nonlinear error, the reconstruction error is very small, because it is determined by different distribution intervals. However, our ultimate goal is to minimise the global error. Hence, we must consider the nonlinear error and the reconstruction error in equilibrium. The local curve has almost no error while it preserves the nonlinearity. Moreover, the tangent space also preserved the minimum error of the local reconstruction.

## 12.5.3 Example analysis

To verify that the spectral graph theory and spectral estimation algorithm can be well applied to manifold learning, we compare the algorithm in Section 12.2 with other related dimensionality reduction algorithms through experiments. The feasibility and effectiveness of the topological invariance theory algorithm are proved.

### 12.5.3.1 Dimension reduction of a three-dimensional cylindrical manifold

The sample points of the data manifold are sampled in a three-dimensional cylindrical manifold in the ten-dimensional data space. Through the topological invariance spectral estimation learning algorithm, the dimension of the sample points is reduced, and a two-dimensional representation is generated ($R^{1} \times I^{1}$): one is the linear axis and the other is the axis of the torus. In the ten-dimensional Gaussian noise environment, 500 sample points along the three-dimensional cylindrical surface are generated randomly, as shown in Figure 12.10(a). The experimental results are shown in Figure 12.10(b), i.e., the two-dimensional representation of the data manifold.

### 12.5.3.2 Dimensionality reduction of the swiss roll data

The experiments sampled 500 random sample points in the Swiss roll data set, plus the Gaussian noise of the ten-dimensional environment, as shown in Figure 12.11(a). The sample points are distributed along the axis of the Bingham distribution, but they are not always around the equator centre. Thus, the super spherical surface reconstructs the plane coordinate system by mapping it in equal directions to the two-dimensional space, as shown in Figure 12.11(b). Because the interval between the original data is very close, especially the sample points between the two ends of the manifold, there are some non-nearest neighbour sample points. Hence the reduced dimensionality results in a small distortion at both ends of the coordinates, as shown in Figure 12.11(c).

![](img/456a7a56403cbb2b5f1a261793529a51_396_0.png)

Fig. 12.10: 500 sample points along the three-dimensional cylindrical surface manifold and its two-dimensional representation.

![](img/456a7a56403cbb2b5f1a261793529a51_396_1.png)

![](img/456a7a56403cbb2b5f1a261793529a51_396_2.png)

Fig. 12.11: (a) Random sampling of the 500 sample points of the Swiss-roll; (b) 2-Dimensional Dimension Reduction Results of TISE Algorithm; (c) 2-Dimensional Dimension Reduction Results of the LLE Algorithm.

## 12.6 Clustering algorithm based on the topological invariance spectral estimation of image feature manifolds

If the dimension reduction problem is regarded as removing highly correlated (redundant) characteristics or merging these related (redundant) features, then the clustering technique can work here [20]. The clustering algorithm merges the rows of the matrix and uses a few clustering centres to represent all the data. Then, the topological invariance spectrum estimation clustering algorithm of image feature manifolds (TISC) is presented.

**Algorithm 12.3: Topological invariance spectral estimation clustering of image feature manifolds (TISC)**

- **Input:** Sample set $S$, the corresponding graph of the sample set $G$, Characteristic vector number $M$, Cluster number $K$, Upper bound of standard cut set $Ncut$, parameter $n$
- **Output:** Minimum distribution partition $(A_1, A_2, \ldots, A_K)$

1. Construct the similarity matrix of sample sets $W$, degree matrix $D$, and perform initialisation. Given a distribution $\cup_{j=1, \ldots, K}A_j = G$, satisfying $A_i \cap A_{j \neq i} = \emptyset$
2. Compute the first $k$ eigenvalues $\lambda_1, \ldots, \lambda_k$ of the matrix $L = I - D^{-1}W = U \Lambda U^T$ and corresponding feature vectors $x_1, \ldots, x_k$. The new matrix $X'$ is obtained by regularisation of the feature vectors. Construct the matrix $X' = [x_1', \ldots, x_k'] \in R^{n \times k}$
3. Let $k = 1$, $ncut(A(k), W) = Ncut$, compute $e(M) = ncut(A, W) - \sum_{i=1}^{K} \lambda_i/\lambda_{M-1} - \lambda_k$
4. If $k \le n$ and $ncut(A(k+1), W) \le ncut(A(k), W) + \varepsilon(M)\lambda_k$, then $ncut(A(k), W) = Ncut(A(k), W)$, $k = k+1$, return Step 4; Else, return $ncut(A(k), W) = \infty$
5. Let $min = ncut(A(k), W)$, minimum partition $\cup_{j=1, \ldots, min}A_j$ is obtained

## 12.7 Summary

The algorithm of spectral estimation for topological invariance of image feature manifolds was proposed for high-dimensional data space, which is ubiquitous in real life. For visualisation in the research field of machine vision, it is often necessary to embed high-dimensional data into the low-dimensional manifold space, realise effective dimensionality reduction of feature manifolds, or perform unsupervised clustering of data sets. Because the data samples have high similarity characteristics within the sample, effectively maintaining the geometric characteristics of the internal structure
