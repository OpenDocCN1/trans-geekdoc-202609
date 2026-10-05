
# Types of Machine Learning Algorithms 27

separates the data into two categories. SVM models are closely related to neural networks. In fact, a SVM model using a sigmoid kernel function is equivalent to a two-layer perceptron neural network.

Support Vector Machine (SVM) models are a close cousin to classical multilayer perceptron neural networks. Using a kernel function, SVMs are an alternative training method for polynomial, radial basis function and multi-layer perceptron classifiers in which the weights of the network are found by solving a quadratic programming problem with linear constraints, rather than by solving a non-convex, unconstrained minimization problem as in standard neural network training.

In the parlance of SVM literature, a predictor variable is called an attribute, and a transformed attribute that is used to define the hyperplane is called a feature. The task of choosing the most suitable representation is known as feature selection. A set of features that describes one case (i.e., a row of predictor values) is called a vector. So the goal of SVM modeling is to find the optimal hyperplane that separates clusters of vectors in such a way that cases with one category of the target variable are on one side of the plane and cases with the other category are on the other side of the plane. The vectors near the hyperplane are the support vectors. The figure below presents an overview of the SVM process.

# The SVM algorithm

![](img/e1ab17402154bec3fa9a7873fe3ee232_52_0.png)

# A Two-Dimensional Example

Before considering N-dimensional hyperplanes, let's look at a simple 2-dimensional example. Assume we wish to perform a classification, and our data has a categorical target variable with two categories. Also assume that there are two predictor variables with continuous values. If we plot the data points using the value of one predictor on the X Axis and the other on the Y axis we might end up with an image as shown below. One category of the target variable is represented by rectangles while the other category is represented by ovals.

![](img/e1ab17402154bec3fa9a7873fe3ee232_53_0.png)

In this idealized example, the cases with one category are in the lower left corner and the cases with the other category are in the upper right corner; the cases are completely separated. The SVM analysis attempts to find a 1-dimensional hyperplane (i.e. a line) that separates the cases based on their target categories. There are an infinite number of possible lines; two candidate lines are shown above. The question is which line is better, and how do we define the optimal line.

The dashed lines drawn parallel to the separating line mark the distance between the dividing line and the closest vectors to the line. The distance between the dashed lines is called the margin. The vectors (points) that constrain the width of the margin are the support vectors. The following figure illustrates this.

![](img/e1ab17402154bec3fa9a7873fe3ee232_53_1.png)

# Types of Machine Learning Algorithms 29

An SVM analysis (Luis Gonzalez, 2005) finds the line (or, in general, hyperplane) that is oriented so that the margin between the support vectors is maximized. In the figure above, the line in the right panel is superior to the line in the left panel.

If all analyses consisted of two-category target variables with two predictor variables, and the cluster of points could be divided by a straight line, life would be easy. Unfortunately, this is not generally the case, SVM must deal with (a) more than two predictor variables, (b) separating the points with non-linear curves, (c) handling the cases where clusters cannot be completely separated, and (d) handling classifications with more than two categories.

In this chapter, we shall explain three main machine learning techniques with their examples and how they perform in reality. These are:

- K-Means Clustering
- Neural Network
- Self Organised Map

# K-Means Clustering

The basic step of k-means clustering is uncomplicated. In the beginning we determine number of cluster K and we assume the centre of these clusters. We can take any random objects as the initial centre or the first K objects in sequence can also serve as the initial centre. Then the K means algorithm will do the three steps below until stable (= no object move):

Iterate until stable (= no object move):

1. Determine the centre coordinate
2. Determine the distance of each object to the centre
3. Group the object based on minimum distance

The Figure 3 shows a K-means flow diagram

# Soft Computing and Machine Learning with Python

![](img/e1ab17402154bec3fa9a7873fe3ee232_55_0.png)

**Figure 3:** K-means iteration.

K-means (Bishop C. M., 1995) and (Tapas Kanungo, 2002) is one of the simplest unsupervised learning algorithms that solve the well known clustering problem. The procedure follows a simple and easy way to classify a given data set through a certain number of clusters (assume k clusters) fixed a priority. The main idea is to define k centroids, one for each cluster. These centroids should be placed in a cunning way because of different location causes different result. So, the better choice is to place them as much as possible away from each other. The next step is to take each point belonging to a given data set and associate it to the nearest centroid. When no point is pending, the first step is completed and an early groupage is done. At this point we need to re-calculate k centroids as barycenters of the clusters resulting from the previous step. After we have these centroids, a new binding has to be done between the same data set and the nearest centroid. A loop has been generated. By a result of this loop we notice that the k centroids change their location by step until no more move.

Finally, this algorithm aims at minimizing an objective function, in the data set a squared error function.

$$\sum_{j=1}^{k} \sum_{i=1}^{n} \|x^{(i)}-c_j\|^2$$

# Types of Machine Learning Algorithms 31

where $\|x^{(i)}-c_j\|^2$ is a chosen distance measure between a data point $x^{(i)}$ and the cluster centre $c_j$, is an indicator of the distance of the $n$ points from their respective centres.

The algorithm in figure 4 is composed of the following steps:

1. Place K points into the space represented by the objects that are clustered. These points represent initial group centroids.
2. Assign each object to the group that has the closest centroid.
3. When all objects have been assigned, recalculate the positions of the K centroids.
4. Repeat Steps 2 and 3 until the centroids no longer move. This produces a separation of the objects into groups from which the metric to be minimized can be calculated.

Although it can be proved that the procedure will always terminate, the k-means algorithm does not necessarily find the optimal configuration, corresponding to the global objective minimum. The algorithm is also significantly sensitive to the initial randomly selected cluster centres. The k-means algorithm can be run multiple times to reduce this effect. Kmeans is a simple algorithm that has been adapted to many problem domains. As we are going to see, it is a good candidate for extension to work with fuzzy feature vectors.

# An example

Suppose that we have n feature vectors $x_1, x_2, ..., x_n$ all from the same class, and we know that they fall into k compact clusters, $k < n$. Let mi be the mean of the vectors in cluster i. If the clusters are well separated, we can use a minimum-distance classifier to separate them. That is, we can say that x is in cluster $i$ if $\|x-m_i\|$ is the minimum of all the k clusters. This suggests the following procedure for finding the k means:

- Make initial guesses for the means $m1, m_2, ..., m_k$
- Until there are no changes in any mean
