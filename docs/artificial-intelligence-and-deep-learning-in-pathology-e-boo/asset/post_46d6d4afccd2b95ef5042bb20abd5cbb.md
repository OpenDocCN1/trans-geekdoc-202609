
subject to the constraints $\sum_{i=1}^{n} c_i y_i = 0$ and $0 \le c_i \le 1/(2n\lambda)$. The regularizing parameter $\lambda$ penalizes prediction errors. Support vector–based approaches usually perform well even with relatively small training datasets and have the advantage of well-understood mathematical behavior (which is an important consideration in the context of regulatory compliance, among others).

Stepping back for a moment from the technical detail, intuitively what is happening here is that the algorithm is learning which class exemplars are the “most problematic” ones, i.e., which exemplars are nearest to the class boundaries and thus most likely to be misclassified. These are the support vectors that give the approach its name. Inspection of these is insightful. Firstly, a large number of support vectors (relative to the total amount of training data) should immediately raise eyebrows as it suggests overfitting. Secondly, by examining which exemplars end up as support vectors, an understanding of the nature of learning that took place can be gained as well as of the structure of the problem and data representation, which can lead to useful and novel clinical insight.

## Nonparametric, k-nearest neighbor—based methods

The k-nearest neighbor classifier classifies a novel pattern comprising features x1, ..., xn to the class dominant in the set of k-nearest neighbors to the input pattern (in the feature space) among the training patterns with known class memberships [29]. The usually employed similarity metric used is the Euclidean distance.

## Random forests

Random forest classifiers fall under the broad umbrella of ensemble-based learning methods [30]. They are simple to implement, fast in operation, and have proven to be extremely successful in a variety of domains [31,32]. The key principle underlying the random forest approach comprises the construction of many “simple” decision trees in the training stage and the majority vote (mode) across them in the classification stage. Among other benefits, this voting strategy has the effect of correcting for the undesirable property of decision trees to overfit training data [33]. In the training stage, random forests apply the general technique known as bagging to individual trees in the ensemble. Bagging repeatedly selects a random sample with replacement from the training set and fits trees to these samples. Each tree is grown without any pruning. The number of trees in the ensemble is a free parameter which is readily learned automatically using the so-called out-of-bag error [29].

Much like in the case of naïve Bayes– and k-nearest neighbor–based algorithms, random forests are popular in part due to their simplicity on the one hand, and generally good performance on the other. However, unlike the former two approaches, random forests exhibit a degree of unpredictability as regards the structure of the final trained model. This is an inherent consequence of the stochastic nature of tree building. As we will explore in more detail shortly, one of the key reasons why this characteristic of random forests can be a problem in regulatory terms — clinical adoption often demands a high degree of repeatability not only in terms
of the ultimate performance of an algorithm but also in terms of the mechanics as to how a specific decision is made.

## Unsupervised learning

We have already mentioned the task of patient stratification. Indeed, the need for stratification emerges frequently in digital pathology, for example, due to the heterogeneity of many diseases or differential response of different populations to treatment or the disease itself [19].

Given that the relevant strata are often unknown a priori, often because the limitations imposed by previously exclusively manual interpretation of data and the scale at which the data would need to be examined to draw reliable conclusions, it is frequently desirable to stratify automatically. A common way of doing this is by means of unsupervised learning, by applying a clustering algorithm such as a Gaussian mixture model or more frequently due to its simplicity and fewer free parameters, the k-means algorithm [21]. Then any subsequent learning can be performed in a more targeted fashion by learning separate models for each of the clusters individually.

Let X = {x₁, x₂, ..., xₙ} be a set of d-dimensional feature vectors. The k-means algorithm partitions the points into K clusters, X₁, ..., X_K, so that each datum belongs to one and only one cluster. In addition, an attempt is made to minimize the sum of squared distances between each data point and the empirical mean of the corresponding cluster. In other words, the k-means algorithm attempts to minimize the following objective function:

$J(X_1,...,X_k) = \sum_{i=1}^k \sum_{x \in X_i} \|c_i - x\|^2$, 8.8

where the empirical cluster means are calculated as:

$c_i = \sum_{x \in X_i} x / |X_i|$, 8.9

The exact minimization of the objective function in Ref. [1] is an NP-hard problem [34]. Instead, the k-means algorithm only guarantees convergence to a local minimum. Starting from an initial guess, the algorithm iteratively updates cluster centers and data-cluster assignments until (1) a local minimum is attained, or (2) an alternative stopping criterion is met (e.g., the maximal desired number of iterations or a sufficiently small sum of squared distances). The k-means algorithm starts from an initial guess of cluster centers.

Often, this is achieved simply by choosing k data points at random as the centers of the initial clusters, although more sophisticated initialization methods have been proposed [35,36]. Then, at each iteration t = 0, ... the new datum-cluster assignment is computed:

$$X_i^{(t)} = \left\{x : x \in X \land \arg\min_j \left\|x-c_j^{(t)}\right\|^2 = i\right\}$$

In other words, each datum is assigned to the cluster with the nearest (in the Euclidean sense) empirical mean. Lastly, the locations of cluster centers are recomputed from the new assignments by finding the mean of the data assigned to each cluster:

$$c_j^{(t+1)} = \sum_{x\in X_j^{(t)}} \frac{x}{\left|X_j^{(t)}\right|}$$

The algorithm is guaranteed to converge because neither of the updates in Ref. [3] nor [4] can ever increase the objective function of Ref. [1]. Various extensions of the original k-means algorithm include fuzzy c-means [37], k-medoid [38], kernel k-means [39], as well as discriminative k-means when partial labeling is available [40]. The interested reader is referred to the cited publications for further information.

## Image-based digital pathology

Probably one of the most interesting areas of research in digital pathology, both in terms of practical potential and the nature of intellectual challenges, concerns the use of images.

Due to the inherent complexity of images of interest in pathology, the aforementioned distinction between what we termed “conventional” machine learning—and deep learning—based methods is particularly pronounced in this realm of digital pathology. In an outline, the former usually take on a modular, pipeline form whereby explicitly engineered features (sometimes referred to as “handcrafted” features) are extracted from input images first, and then fed into a machine learning algorithm of the sort described in the previous section. In contrast, in deep learning—based approaches, the process is not atomized [41] in this manner—good features, as complex functions of directly sensed data (e.g., pixel intensities), are learned automatically from labeled training data. This distinction has often led to deep learning—based methods being characterized as “data agnostic” [42]; colloquially put, the idea is that no matter what the input is, the algorithm will learn what good features are. However, to describe deep learning in this manner would be a misnomer and highly misleading. For any learning to take place, the model has to be constrained and by virtue of these constraints contain implicit information about the problem at hand; succinctly put, a tabula rasa cannot learn. Indeed, one of the theorems popularly known as “no free lunch theorem” implicitly says the very same:

> > *Any two optimization algorithms are equivalent when their performance is averaged across all possible problems.*
> >
> > **Ref. [18]**
