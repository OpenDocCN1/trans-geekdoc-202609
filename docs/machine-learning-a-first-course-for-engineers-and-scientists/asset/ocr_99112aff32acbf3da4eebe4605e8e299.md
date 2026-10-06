# 7 Ensemble methods: Bagging and boosting

![](bbox=[0.32335, 0.08735, 0.67365, 0.27645])

**Figure 7.6:** Random forest applied to the classification problem from Example 2.1. This figure can be compared to Figure 2.11a, which is the decision boundary from a single tree.

Since random forest is a bagging method, the tools and properties from Section 7.1 also applies to random forests, such as out-of-bag error estimation. As bagging, taking $B \rightarrow \infty$ does not lead to overfitting in forests. Hence, the only reason to choose $B$ small is to reduce the computational cost. Compared to using a single tree, a random forest requires $B$ times as computations. Since all trees are identically distributed, it is however possible to parallelize the implementation of random learning.

The choice of $q$ is a tuning parameter, for $q=p$ allows us to recover the bagging method described previously. As a rule-of-thumb we can set $q=\sqrt{p}$ for classification problems and $q=p/3$ for regression problems (values rounded down to closest integer). A more systematic way of selecting $q$ is to use out-of-bag error estimation or cross-validation and select $q$ such that $E_{OOB}$ or $E_{k-fold}$ is minimized.

We finally apply random to the classification problem from Example 2.1 in Figure 7.6.

# 7.3 Boosting and AdaBoost

As we have seen, bagging is an ensemble method for reducing the variance in high-variance models. Boosting is another method, which is primarily used for reducing bias in high-bias models. A typical example of a simple (or, in other words, weak) bias model is a classification tree of depth one (sometimes called a classification stump). Boosting is built on the idea that a weak high-bias model can capture some of the relationships between the inputs and the output. By training multiple weak models, each describing part of the input-output relationship, it might be possible to combine the predictions of these models into an overall better prediction. Hence, the intention is to reduce the bias by training an ensemble of weak models into one strong model.

Boosting methods share some similarities with bagging, in the sense that they are based on combining the predictions from multiple models (an ensemble). Both bagging and boosting can be viewed as meta-algorithms, in the sense that they are algorithms built on top of other algorithms. However, there are also important differences between boosting and bagging we will discuss below.

The main difference is how the models are learned. In learning $B$ identically distributed models in parallel. Boosting, on the other hand, uses a sequential construction of the ensemble members. This is done in a way that each tree corrects the mistakes made by the previous one. This is achieved by modifying the training dataset at each iteration in order to put more emphasis on the data points for which the model (so far) has performed poorly. The final prediction is obtained from a weighted average or a weighted majority vote among the models. We will use the simple example 7.5 to illustrate this idea.