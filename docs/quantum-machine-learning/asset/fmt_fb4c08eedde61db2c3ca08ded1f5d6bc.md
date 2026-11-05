
In Equation (7.5), $\\frac{1}{`C_y`}$ is considered as the normalized factor. The mean square error is reduced to obtain more precision in the final model [[19](#ch7.xhtml#ref7_19)]. The cost function reduces the mean square error. However, different researchers have proposed many methods to estimate cost function for a quantum linear regression [[20](#ch7.xhtml#ref7_20)]. Polynomials achieve the extended quantum regression technique based on higher order fit.

## 7.6 Quantum Clustering
Reference \[8\] clustering is recognized as an unsupervised learning algorithm and is mainly useful in identifying the underlying pattern in an input data stream. The patterns are primarily utilized to determine the behavior of the data stream in terms of mathematical notions and statistical inferences, and, in some instances, it is used as a dimensionality reduction technique for hybrid modeling [[21](#ch7.xhtml#ref7_21)]. The underlying principle for clustering is to determine the similarities between data or examples. However, when the data stream is extensive, the redundant computation on classical machines fails to achieve the best results [[22](#ch7.xhtml#ref7_22)]. Quantum computing resolves these issues through its hardware implementation of clustering algorithms for large-scale data streams. Conventional `K-Means` and `K-Median` clustering is utilized next to explain and discuss the implementation of quantum clustering and the effectiveness of the algorithms.

### 7.6.1 Quantum K-Means Clustering
Quantum `K-Means` clustering is performed on training and test data and the correspondence between each vector is identified to obtain the best accuracy [[23](#ch7.xhtml#ref7_23)]. Alternatively, in classical `K-Means` clustering, the training input data is considered for determining test accuracy. The flow diagram in [Figure 7.5](#ch7.xhtml#fig7_5) depicts the process of `K-Means` clustering in a detailed way.

![Figure 7.5 Quantum clustering process.](images/fig7_5_B.jpg)

[Figure 7.5 Quantum clustering process.](#ch7.xhtml#R_fig7_5)

After quantum embedding is performed on the train and test vectors, the correspondence between the train and test vectors is established, with respect to the degree of position [[24](#ch7.xhtml#ref7_24)]. A rotation operation is performed to obtain a new vector from the original and to obtain better correspondence between the input vectors. After obtaining the newly configured `Qubits`, the normalization is performed on the vectors [[25](#ch7.xhtml#ref7_25)]. The `Hadamard` operation is performed on the normalized vector on the most significant qubits. Measurement operations are performed to identify the probabilities of quantum states. The whole process is repeated to identify the relative difference of the quantum states, eventually leading to accurate clustering results by inferencing the variational states.

### 7.6.2 Quantum K-Median Clustering
`K-Median` is a conventional clustering technique where `K` denotes the number of clusters required from the input data. Once the execution starts, `K`-points are selected, and the proximity of the data points to the centroids is calculated and forms a cluster. This process will repeat recursively until it reaches the stable centroids. The recursive nature of the process is time consuming, and the complexity increases exponentially when the data size increases. To address this effectively with large datasets, quantum `K-Median` implementation helps for faster convergence and to decrease the complexity [[26](#ch7.xhtml#ref7_26)]. Multiple versions of `K-Median` clustering have been introduced, and the most famous is the Diffie-Hellman algorithm (`DH`) algorithm, developed by Aïmeur et al. [[27](#ch7.xhtml#ref7_27)], which is widely in used to mitigate the minimization problem in `K-Median` clustering.

### 7.6.3 Quantum Hierarchical Clustering
Quantum hierarchical clustering is one of the leading methods used for clustering and identifying the most prominent features of data. Hierarchical clustering recursively identifies correlations among the training data through proximities at every level [[28](#ch7.xhtml#ref7_28)]. The level denotes the prominent feature of the data which helps to identify the clusters. Proximities are calculated using distance-based methods. Hierarchical clustering is depicted in [Figure 7.6](#ch7.xhtml#fig7_6).

![Figure 7.6 Hierarchical clustering.](images/fig7_6_B.jpg)

[Figure 7.6 Hierarchical clustering.](#ch7.xhtml#R_fig7_6)

Hierarchical clustering is carried out in two different ways. One way is the agglomerative method (bottom-up approach) and the other is the divisive method (top-down approach). The Euclidian distance between the data points is considered for clustering purposes. In the divisive method, the data set is classified into multiple clusters, while in the agglomerative method, the multiple clusters form into a single cluster. The levels represent the important attributes possessed by the dataset. In [Figure 7.6](#ch7.xhtml#fig7_6), we notice that the data points (11, 8, 1, and 2) form cluster 1, (10, 7, and 3) form cluster 2, and (9, 6, 4, and 5) form cluster 3. Every level represents the attribute values and is based on the values of the clusters that will be formed. However, when the dataset size is increased, finding the optimal distance measure between the data points is a tedious process. To identify the optimal distance between the data points for better convergence, quantum computing is employed [[29](#ch7.xhtml#ref7_29)]. The implementation of hierarchical clustering using quantum hardware is discussed below. In quantum hierarchical clustering the same concept of quantum clustering process is applied, as shown in [Figure 7.5](#ch7.xhtml#fig7_5).

## 7.7 The Harrow–Hassidim–Lloyd (`HHL`) Algorithm
Solving any linear system is very important in the field of engineering. Essentially, linear systems yield no solution, multiple solutions, or a single solution. No-solution linear systems are called inconsistent, multiple-solution linear systems are called consistent and dependent, because the solutions are dependent on other solutions, and the single-solution linear system is called consistent and independent, because the solution is independent of any inputs or influences [[30](#ch7.xhtml#ref7_30), [31](#ch7.xhtml#ref7_31)]. All linear systems follow the homogeneous principle as shown in Equation (7.6).

(7.6)
```
\[*a**y*1(*t*)+*b**y*2(*t*)\] = *T*\[*a**x*1(*t*)+*b**x*2(*t*)\] = *a**T*\[*x*1(*t*)\] + *b**T*\[*x*2(*t*)\]
```

Since solving a linear system has severe complexity issues in classical computing, quantum computers are much more successful in solving linear systems to obtain a consistent and independent output. The scientists Hassidim, Harrow, and Lloyd developed an algorithm to solve the linear systems effectively, known as the `HHL` algorithm.

## 7.8 Quadratic Unconstrained Binary Optimization (`QUBO`)
The quadratic unconstrained binary optimization (`QUBO`) method is widely used to solve combinational optimization problems in various fields. The `QUBO` method is a unified modeling framework to solve optimization problems in network flows, scheduling, and in NP-Hard problems such as number partitioning, matching, and spanning trees, among others. `QUBO` solves a set of variables (input), in correspondence to an objective function (min/max), and a set of constraints (need not to follow) [[32](#ch7.xhtml#ref7_32)]. `QUBO` offers to penalize the obtained solution if it is not following the constraint, which eventually allows us to obtain multiple solutions for binary variable problems. [Figure 7.7](#ch7.xhtml#fig7_7) depicts solving the binary optimization problem.

![Figure 7.7 Binary optimization problem (path finding).](images/fig7_7_B.jpg)

[Figure 7.7 Binary optimization problem (path finding).](#ch7.xhtml#R_fig7_7)
