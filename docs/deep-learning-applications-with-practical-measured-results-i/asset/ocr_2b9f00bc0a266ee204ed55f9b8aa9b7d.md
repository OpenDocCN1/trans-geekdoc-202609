is applied for distance calculation, as shown in Equation (6). Moreover, each centroid of the point cloud is the mean of the coordinates’ values of the points.

$$d(\mathbf{x}, c) = (\mathbf{x} - c)(\mathbf{x} - c)^T \tag{6}$$

where x is the initial observations, c is the centroid.

![](bbox=[0.28, 0.24, 0.65, 0.42])

# Figure 9. Separation of cylinders into individuals.

According to the previous investigations, there are several efficient algorithms for data partitioning, such as the K-means clustering algorithm [33,34] and Lloyd’s algorithm [35]. These two algorithms are iterative data-partitioning algorithms, which assign the initial observations into k clusters according to the squared Euclidean distance metric and the centroids. The number of clusters k is defined before data partition. In our work, the Lloyd’s algorithm is used for finding the centroids of k clusters while the K-means clustering algorithm is used for partitioning the initial observations into k clusters according to the squared Euclidean distance metric with respect to the centroid of each cluster. The K-means clustering algorithm requires the input as a matrix of M points in N dimensions as well as a matrix of K initial cluster centers in N dimensions. Denoting the number of points in cluster L is NC(L), and the Euclidean distance between point I and cluster L is D(I,L), the general procedure of the K-means clustering algorithm is to find a K-partition of clusters with locally optimal within-cluster sum of squares by changing the initial observations from one cluster to another [33], as indicated by Equation (7).

$$\min_{D^2} \sum_{i=1}^{K} \sum_{j=1}^{NC(L)} D^2(I, L) \tag{7}$$

The procedures of the algorithm for partitioning the filtered cylinders into individuals are shown in Figure 10, which consists of 6 steps. It is worth mentioning that the data are subjected to dimensionality reduction before data partitioning. These cylinders are a point cloud of three dimensions. The aim of dimensionality reduction is to produce a compact low-dimensional encoding of a given high-dimensional data set [36]. The dimensionality can be reduced in two ways [37]. The first is by only keeping the most relevant variables from the original dataset, which is called feature selection. The second way is to exploit the redundancy of the input data and to find a smaller set of new variables, each being a combination of the input variables containing basically the same information as the input variables. In this work, the dimensionality of the data is reduced to 2D from 3D by projection along Z-axis.