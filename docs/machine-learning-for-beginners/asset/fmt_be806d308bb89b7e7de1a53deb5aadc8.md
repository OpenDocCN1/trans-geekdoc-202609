
KNN works well when the number of input variables (p) is small, but it will struggle if this number becomes large.

Every input variable can be seen to be a dimension of p-dimensional input space. Suppose you have two input variables namely x1 and x2, your input space will be 2-dimensional. If the number of dimensions is increased, the volume of input space will increase by an exponential rate.

Some of the examples of uses of KNN algorithm include nearest neighbor content retrieval.

A good example is computer vision applications such as handwriting detection.

For the case of video content, the problem will becomes more interesting. Suppose you are given a video, for example, and need to identify a video which is closely related to it. This problem may seem to be impossibly abstract, but it is a real-life practical problem in a number of contexts. 

A good example of a field in which such a search would be practical is American Sign Language (ASL), in which communication is done solely via hand gestures.

Suppose we need to create an ASL dictionary which the user will be able to query using gestures. The problem will reduce to identification of the nearest (most similar) gestures stored in the database (possibly k). This is a KNN problem.

The KNN algorithm is also widely applicable to gene expression, and KNN performs most beautifully in this field. KNN can also be applied to 3D structure prediction and to protein interaction prediction.

## Advantages of KNN Algorithm

The following are the advantages of using the KNN algorithm:

*   It is a good algorithm for creating prediction models where the data is very noisy.

*   The algorithm works effectively when the available dataset is large.

## Disadvantages of KNN Algorithm

The following are the disadvantages of associated with the KNN algorithm:

*   One is expected, first, to find the value of K, the number of the nearest neighbors.  

*   The cost of computation is very high, since we have to find the distance of every query instance to all the training samples. This computational cost can be reduced via indexing.  

*   Which distance measure to use may be unclear, as well as the attributes which should be used for one to produce the results.

## When should you use the KNN Algorithm?

Although the KNN algorithm can be applied to both classification and regression problems, it is most widely applied in classification problems.

Tip: Whenever you need to determine the similarity between your variables, choose KNN. It is the best algorithm to use.

It is a good algorithm for use for pattern recognition and statistical estimation.

Chapter 10  

Reinforcement Machine Learning Algorithms 

Clustering, a process used to find the structure of a collection of unlabeled data, is the most important kind of unsupervised learning algorithm. 

Clustering divides the data points into a set of groups known as clusters such that the data points in the same cluster are more closely related to each other than to the data points in other clusters.

In simple terms, the goal of clustering is to segregate the data into groups with similar characteristics and then assign them to clusters.

## How Clustering Algorithms Work

Suppose you run a rental store and your aim is to know the preferences of your customers in order to boost your business. It is impossible for you to analyze the preferences of each individual customer and then come up with a strategy for everyone.

The best way to approach this problem is to divide your customers into a number of groups, say 8, according to their purchasing habits. A strategy should then be devised for the customers of each group. This is how clustering algorithms work. 

Clustering can either be hard or soft.

In hard clustering, every data point must belong to a particular group, completely or not.

In our above example, each customer must belong to any of the 8 groups.

In soft clustering, each data point is not put into a separate cluster, but the likelihood or probability of assigning that data point to the cluster is assigned.

In our above example, every customer is assigned a probability of belonging to either of the 8 groups.

## Types of Clustering Algorithms

Clustering is a subjective task, meaning that there may be many paths to the desired goal. In every methodology, a set of rules is followed for the purpose of defining the similarity between the data points.

Let’s discuss some of the common clustering algorithms:

1.  K Means Clustering

This is a clustering algorithm which works iteratively with an aim of finding the local maxima during each iteration. The algorithm follows the following steps:

i. Specify the number of clusters you wish to have, K. 

ii. Assign every data point to a cluster randomly.

iii. Determine the cluster centroids.

iv. Re-assign every point to closest cluster centroid.

v. Re-compute the cluster centroids.

Repeat steps iv. and v. until there are no possible improvements. At this point global optima shall have been reached.

This will be the end of the algorithm (if the algorithm was not explicitly limited).

The following are the advantages of the K-Means clustering algorithm:

*   The K-Means clustering algorithm offers a fast computation if the variables are huge and K is kept small.  

*   The algorithms can produce tighter clusters, making it easy for one to determine the relationship between the cluster members.

The following are the disadvantages of K-Means clustering algorithm:

*   Predicting the value of K may be difficult.  

*   Different initial partitions may give final clusters which are different.  

*   It doesn’t work well in cases where the clusters are of different densities and sizes.

1.  Hierarchical Clustering 

Hierarchical clustering works by creating a hierarchy of clusters. The algorithm begins with data points each of which has been assigned to its own cluster.

The two nearest clusters are then merged into a single cluster. The algorithm will terminate once only a single cluster is left.

A dendrogram is the best way to demonstrate how this clustering algorithm works. In a dendrogram, you begin with a set of data points, with each assigned to a separate cluster.

Two closest clusters are merged, and this continues until we remain with one cluster at the top of the dendrogram. The height in a dendrogram at which any two clusters are merged demonstrates the distance between the two clusters in a data space.

The following are the advantages of a Hierarchical clustering algorithms:

*   The algorithms are easy to implement and sometimes give the best results.  

*   There is no a prior information regarding the number of clusters to be formed.  

The following are the disadvantages of hierarchical clustering algorithms:

*   It impossible for algorithms to undo what has been done previously.  

*   A time complexity of about O(n2 log n) is needed, with n being the number of data points.  

*   There is no direct minimization of objective functions.

*   Identifying the number of clusters in the dendogram may be difficult.  

Note that K-Means is suitable when you have big data. This is because the K-Means algorithm has a linear time complexity, but a hierarchical clustering algorithm has a quadratic time complexity.

In K-Means, the number of clusters is chosen randomly, meaning that obtained results may differ from one selection of K to the next. In hierarchical clustering, we may reproduce the results.

The following are the applications to which you can apply clustering algorithms:

*   Market segmentation

*   Medical imaging

*   Search result grouping

*   Image segmentation

*   Recommendation engines

*   Anomaly detection

*   Social network analysis

## When to use Clustering Algorithms

Clustering algorithms should be used when one has a set of items and there is need to create some number of groups from these items.
