# Generative models and learning from unlabeled data

# M = 3

![](bbox=[0.138, 0.111, 0.413, 0.269])

# M = 5

![](bbox=[0.558, 0.111, 0.833, 0.269])

**Figure 10.8:** k-means applied to the classification data Example 2.1. In ever we have actually labeled data, so the purpose of applying a clustering algorithm to the inputs (without the corresponding labels) is purely for illustrative purposes. We try $M=3$ (left) and $M=5$ (right). It is worth to note that it happens that for $M=3$ there is almost one artist per cluster.

The name of the algorithm, $k$-means, is reminiscent of other methods studied in this book, namely $k$-NN. They do some similarities, in particular that they use Euclidean distance to define similarities in the input space. But being said, $k$-means, is sensitive to the normalization of the input values. While $k$-NN is a supervised learning method (applicable to classification and regression problems), $k$-means is a method for solving the (unsupervised) clustering problem. Note in particular that the “k”, in the name has a different meaning for the two methods.

# Choosing the number of clusters

In both the GMM model and the k-means algorithm for clustering we need to select the number of clusters $M$ before running the corresponding algorithm. Hence, unless there is some application-specific prior knowledge regarding how to select $M$, this becomes a design choice. Many other model selection problems is not possible to optimize $M$ by taking the value that gives the smallest training cost (negative of (10.12) for GMM, or (10.8) for $k$-means). The reason is that increasing $M$ to $M+1$ gives more flexibility to the model, and this increased flexibility can only decrease the value of cost. Intuitively, in the case when $M=n$, we end up with the trivial (unintersecting) solution where each data point is assigned to its cluster. This is a type of overfitting.

Validation techniques such as hold-out and cross-validation (see Chapter 4) can be used to guide the model selection, but they need to be adapted to the unsupervised setting (specifically, there is no new data error $E_{pp}$ for the clustering model). Instance, for the GMM, which is a probabilistic generative model, it is possible to use of the hold-out validation set to find a suitable value for $M$. That is, we set aside validation data $x_{val}$ which is not used to cluster the model. We then train different models for different values of $M$ on the remaining data, and evaluate the hold-out likelihood $p(x_{val}^i)_{i=1}^n|\hat{	heta})$ in each candidate model. The best hold-out likelihood is then selected as the final cluster model.

This provides us with a systematic way of selecting $M$; however, in the unsupervised setting context of a predictive model, minimizing the data (prediction) error is often the ultimate goal of the model, so it makes sense to base the evaluation on this. In the context of clustering, it is not necessarily that minimizing the “clustering loss” over new data is what we want. After, clustering is often applied to gain insights regarding the data, by finding a small number of clusters where data points within each have similar characteristics. Thus, as long as the model results in a coherent and meaningful grouping of the data points, we favor a smaller model over a larger one, even if the latter in a better