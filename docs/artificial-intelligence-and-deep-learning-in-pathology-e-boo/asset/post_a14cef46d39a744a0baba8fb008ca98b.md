
![](img/ec668102bd6cbe5645156f246a7c2e8b_27_0.png)

## FIGURE 2.4

Creating a linear separator for the data by adding a dimension to it. The separating plane shown in the 3D space on the left is analogous to a line drawn in 2D space. In general, for any N-dimensional space, a linear construct such as this is defined as a hyperplane.

> *Reprinted with permission from Eric Kim (www.eric-kim.net).*

to see that a flat plane can divide them. In general, an SVM can raise the dimensionality of the data space until an (N-1) hyperplane can separate the classes. In this example, the two-dimensional plot is transformed into a three-dimensional space such that an N = 2 hyperplane can provide a boundary.

## The K-Means Algorithm (KM)

This is also a classic clustering algorithm, but it is discussed in a separate section because it is important not to confuse it with KNN, and so they are presented separately for pedagogical rather than conceptual reasons. This is another important distinction, in that unlike the K nearest neighbor algorithm, it involves unsupervised learning. As such, it has important applications not only on its own but also in conjunction with some deep learning methods.

The K means algorithm attempts to find clustering in unlabeled data. One starts by making a guess as to how many clusters there are (this will be refined later). A centroid is the arithmetic mean position of all the points in a cluster. Next make a random guess as to where the central points of each cluster are so as to create k pseudo-centers. These should be reasonably distant from each other, but need to have no relationship to the actual clusters and can be chosen randomly (unless there is some prior knowledge about the data structure). Next assign each point of the dataset to its nearest pseudo-center. We now form clusters with each cluster comprising all of the data points associated with its pseudo-center. Next update the location of each cluster’s pseudo-center so that it is now indeed in the center of all its members. Do this recursively until there are no more changes to cluster membership.

We can determine the best choice for K by plotting within-cluster scatter as a function of the number of clusters. As an extreme example, if K equals the number of data points, there is obviously no variance within each cluster, as they each consist of one element. The smaller the number of clusters, the greater the variance within the clusters. When variance is plotted as a function of K, the equation is reminiscent of exponential decay, and it is easy to pick a value of K such that larger values do not appreciably change the overall variance. This is analogous to the so-called “scree plots” used in principal component analysis (PCA), described in a separate section below.

## Probabilistic models

In the previous section, the basic building blocks of clustering and distance were used to learn relationships among data and to use those relationships to predict class labels. We can also approach this problem by asking the following question; given the feature set for an unknown example, what is the probability that it belongs to a given class? More precisely, if we let X represent the variables we know about, namely our instance’s feature values, and Y the target variables, namely the instance’s class, then we want to use machine learning to model the relationship between X and Y.

Since X is known for a given instance, but Y is not (other than in the training set), we are interested in the conditional probabilities; what is the probability of Y given X. This is another way of saying that given a sample’s feature set (X), predict the class it belongs to (Y). In mathematical notation, this is written as P(Y|X) which is read as “the probability of Y given X.” As a concrete example, X could indicate the phrase "my fellow Americans" and Y could indicate whether the speaker is a member of the class politician (thus using the words “class” and “politician” in the same sentence, possibly for the first time).

The classification problem is thus simply to find P(Y|X). The probabilities of several kinds of occurrence can be calculated directly from the training set. In the data matrix in Fig. 2.1, for any given feature X, we can simply count the number of times its value appears divided by the total number of variables, giving P(X). For any given value of Y, we can similarly count the ratio of the number of times that class appears relative to the overall number of classes. In this manner, we can calculate values for the sets X,Y to get P(Y) and P(X).

There is one more thing we can do, and that is to calculate P(X|Y), the probability of the feature, given the class, which is simply based on looking only at that class and determining how many times the feature value X appears in samples of that class in the training set. We now know P(X|Y). Given this information, we can calculate the probability of the class given our knowledge of its feature set, P(Y|X) by means of the easily proven Bayes theorem (the only equation used in this chapter):

P(Y|X) = (P(X|Y)*P(Y))/P(X) which, if a Venn diagram is drawn, becomes intuitively obvious.

In practice this formula is too simple, since in order to make predictive assignments from attributes to class, each sample must have more than one attribute, and in real-world problems, many more than one. The procedure for dealing with multiple attributes is more complicated [6]. In any case, the Bayes theorem is a formulation of one of the basic rules for conditional probabilities. However, the problem with computing probabilities in this way is that some of the features in a feature set may be dependent on each other (for embryos, mass and cell number are dependent variables), which makes the calculations difficult. In practice, this complication is ignored, and the features are treated as if they were independent. This algorithm is known as **Naïve Bayes** where naïve means that we are foolish enough to assume independence. Surprisingly Naïve Bayes works remarkably well in spite of this limitation, and so it has become an important machine learning model. There are many more complex models that deal with dependency relationships; these are known as Bayesian optimal classifiers. There is also a middle ground that is based on the idea that some things are conditionally dependent but some things are not.

These approaches fall into the framework of probabilistic graphical models that are known as Bayesian Belief Networks or Directed Graphical Networks. These are networks that represent a set of variables and their conditional dependencies via the use of a directed graph. A simple network of this kind is shown in Fig. 2.5. Rain influences whether the sprinkler is turned on, and both rain and the sprinkler influence whether we get wet. Bayesian Belief Networks are beyond the scope of this chapter, but additional information may be found in Ref. [7]. All these algorithms learn from probability distributions within their sample space, rather than spatial metrics, as was the case for SVMs and other geometrical models.

![](img/ec668102bd6cbe5645156f246a7c2e8b_29_0.png)

## FIGURE 2.5

Relationships among three objects. Whether it is raining or not determines whether the sprinkler gets turned on, but not vice versa, so this is a directed graph. Similarly, either rain or the sprinkler will get us wet, but the state of wetness does not cause either rain or the sprinkler to happen, so these arrows are also directional.

![](img/ec668102bd6cbe5645156f246a7c2e8b_31_0.png)

## FIGURE 2.6

A decision tree for predicting tomorrow's maximum temperature. Seattle, 12/27/2017. From Koehrsen, Random forest simplified. In this tree, there is a binary decision made at each branch, so each parent node gives rise to two children nodes.
https://medium.com/@williamkoehrsen/random-forest-simple-explanation-377895a60d2d.

One can construct decision trees for a given dataset in a variety of ways:
- using different subsets of the data for different trees,
- using different decision criteria,
- limiting the depth of each tree, and so on.
For (a) a technique called bagging is commonly used. In bagging, multiple new training subsets are taken by sampling from the main dataset with replacement after each sample is generated. Each subset is used in a different tree. A Random Forest consists of a set of several of such decision trees, with majority voting or some other consensus criterion determining final output values (Fig. 2.7).

## The curse of dimensionality and principal component analysis

Intuitively, adding more features to the data would seem to improve our ability to classify it, but in many applications, this can make things worse [8]. As the dimensionality of the feature set increases, the space in which the samples reside increases with the power of the dimension, and so the sample density at any given point falls below that which is needed for an accurate prediction. The obvious solution is to get more data, but this may not always be possible in practice. There are techniques for dimensional reduction that minimize the loss of information that comes from this
