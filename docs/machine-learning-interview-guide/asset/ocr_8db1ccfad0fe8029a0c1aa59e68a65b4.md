• Distance metric: The distance metric defines how distances between the input instances are to be computed, which may be Euclidean distance, Manhattan distance, or other methods. It determines the manner in which distance between two points is obtained or calculated with an impact on the clustering.

In other words, the neighborhood size is defined by epsilons, a minimum number of points per neighborhood by MinPts, while distance calculation is bound by a particular distance function. Varying these parameters influences the clustering result and how the algorithm operates.

# Question 4: How does DBSCAN define core points, border points, and noise points?

Answer: In DBSCAN, points in the dataset are classified into three categories:

+   - **Core points**: A core point is a point of the dataset that has at least MinPts points within its ε-neighborhood. Core points are part of clusters and are the dense areas of the database.
+   - **Border points**: A border point is a data point that is ε-close to a core point but is not a core point since it is surrounded by less than MinPts neighbors. A border point is likewise on the vertices of clusters as it aids in the identification of the border line of clusters.
+   - **Noise points (or outliers)**: Non-core points or non-border points are the other kinds of points, and they are referred to as noise points. These points are frequently lone or located in districts of slight population concentration and may not be members of any cluster. The noise points refer to the inaccessible points or data points that cannot be grouped under certain classes or categories.