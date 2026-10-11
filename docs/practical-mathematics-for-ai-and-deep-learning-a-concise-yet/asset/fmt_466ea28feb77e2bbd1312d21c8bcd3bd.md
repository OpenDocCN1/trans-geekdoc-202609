
# GMMs: An Extension of K-Means

GMMs are an extension of the k-means model, in which each cluster is modeled with multivariate Gaussian distributions. So, we have to not only find the mean but also a covariance that describes their ellipsoidal shape of the clusters. The parameters of this distribution can be estimated by maximizing the likelihood of the observed data, which is done by an algorithm called **Expectation Maximization** (**EM**), discussed in the following sections. This is a soft clustering technique where we assign data to each cluster with some soft probability. Moreover, with this approach of clustering, we are essentially creating a probabilistic generative model (explained in [Chapter 12 Generative Models](#c12.xhtml)) for the data. Hence, with GMM, we can even sample new data points that resemble the points in the data set; we can impute missing data values.

Let’s understand the GMM probability distribution model in one dimension, as shown in [Figure 7.9](#c07.xhtml#fig7_9). Here, we have taken a mixture of three univariate Gaussian distributions with different means and variance ![](images/2161.jpg). The probability of observing any point from this distribution is given by ![](images/2162.jpg). Here, ![](images/2163.jpg) are called the *mixture weights*, and we have ![](images/2164.jpg) ![](images/2165.jpg). Suppose we have 20 points from the leftmost cluster, 10 from the middle cluster, and another 20 from the rightmost cluster; then, we can take ![](images/2166.jpg). Refer to the following figure:

![](images/Image44705.jpg)

**Figure 7.9:** *Three univariate Gaussian distributions*

We can interpret this joint probability distribution over *x* in a simple generative way. To draw a sample *x* from *P(x)*, we first select one of the components with discrete probability ![](images/2167.jpg), that is, if we denote the mixture component by the discrete random variable *Z*, then ![](images/2168.jpg). Components with large probability are selected more often. This is similar to choosing one cluster centre in k-means. Now, we can sample *X* from the corresponding Gaussian ![](images/2169.jpg). Thus, these two distributions make a joint model over *X* and *Z* together.

![](images/2170.jpg)

The variable *Z* is sometimes called *latent* or *hidden variable*. The presence of the unknown value of *Z* helps explain the patterns in the values of *X*. Detailed discussion about this topic can be found in [Chapter 5, Statistical Inference and Applications](#c05.xhtml) and [Chapter 12, Generative Models](#c12.xhtml).

For clustering problem, we have multivariate data and hence we use a multivariate Gaussian with vector mean ![](images/2171.jpg) of length *n* (the same size as the number of features in a data) and an ![](images/2172.jpg) covariance matrix ![](images/2173.jpg). Now, we need to estimate these parameters by **Maximum Likelihood Estimation** (**MLE**). But direct application of MLE is hard for mixture models and hence we will use iterative algorithm called **Expectation Maximization** (**EM**) **algorithm**. EM has two steps: expectation step (E-step) and maximization step (M-step). We know how to calculate MLE parameter estimates of a Gaussian model: Let ![](images/2174.jpg) be the mean of the data, that is, ![](images/2175.jpg), and ![](images/2176.jpg) the covariance estimate the mean of the ![](images/2177.jpg) matrices formed by the outer product of *X* minus ![](images/2178.jpg) with itself, that is, ![](images/2179.jpg).

## EM Algorithm

Let us now discuss the steps of EM algorithm:

*   **Initialize** the means ![](images/2180.jpg), covariances ![](images/2181.jpg) and mixing coefficients ![](images/2182.jpg): One way to initiate the GMM is to first run k-means and choose the centres as initial estimates for ![](images/2180.jpg). k-means also tells us which data points belong to which cluster. A good starting estimate for the ![](images/2184.jpg) is the within-cluster covariances, and the weights ![](images/2185.jpg) are the fractions of data points allocated to each cluster.

*   **Expectation (E-step)**:
    *   For each data point ![](images/2186.jpg):
        *   For each cluster c:
        *   Compute a measure of relative probability ![](images/2187.jpg) (called responsibilities) as follows:
            ![](images/2188.jpg)

*   **Maximization (M-step)**: Re-estimate the parameters using the responsibilities as follows:
    *   For each cluster c:
        *   Total responsibility associated with the cluster ![](images/2189.jpg)
            ![](images/2190.jpg) ![](images/2191.jpg)

Iterate E-step and M-step until convergence, that is, until the norm of the estimated parameters stop changing significantly. Every step of EM algorithm increases the log-likelihood (explained in [Chapter 5, Statistical Inference and Applications](#c05.xhtml)) of our model.

> **Note:** EM algorithm is very similar to k-means algorithm. k-means does not estimate the covariances of the clusters but only the cluster means. It assumes the clusters are circular by taking fixed Identity covariance matrices. Choosing Σ[c] = ∈I, where ∈ is a variance parameter that is shared by all the components, the responsibilities become
>
> ![](images/2192.jpg)
>
> Taking the limit ![](images/2193.jpg), in the denominator, the term ![](images/2194.jpg), which is closest to zero, will vanish slowly and the responsibility for that term will approach 1. So, we get a hard assignment of data points to clusters, that is, each data point is assigned to the cluster having the closest mean. Thus, EM algorithm reduces to k-means with the fixed circular covariance assumption.

The EM algorithm can be generalized for any model with hidden variables. A probabilistic model is one in which we denote all the observed variables by *X* and all the hidden variables by *Z*. The joint distribution ![](images/2195.jpg) is governed by a set of parameters denoted ![](images/1529.jpg). The likelihood function is given by ![](images/2197.jpg).

# Hierarchical-based Clustering

**Hierarchical clustering** builds hierarchy of clusters from the data points. Approaches to build the hierarchy of clusters can be divided into two types: agglomerative and divisive:

*   **Agglomerative** is a bottom-up approach where initially, each data point is treated as a cluster, and then clusters are merged while moving up the hierarchical structure.
*   **Divisive** is a top-down approach where initially, all data points are treated as one cluster, and then clusters are split while moving down the hierarchical structure.

Finding optimal hierarchical structure is NP-hard. So, most times, merging and splitting of the clusters are decided in a greedy manner. Selection of clusters for merging and splitting is based on the distances between clusters. And the choice of the distance metric greatly influences the shape of the clusters. Popular algorithms under this category are **Balanced Iterative Reducing and Clustering Using Hierarchies** (**BIRCH**) [11], **Clustering Using Representatives** (**CURE**) [12], and Robust Clustering using links (**ROCK**) [13].

## Agglomerative Clustering

Algorithms under this category start by treating every data sample as a cluster on its own. Distances among all existing clusters are calculated. Two clusters with the shortest distance are merged to form one cluster at one level up in a hierarchical way. These two steps are performed repeatedly till we reduce clusters to the required number of clusters.
