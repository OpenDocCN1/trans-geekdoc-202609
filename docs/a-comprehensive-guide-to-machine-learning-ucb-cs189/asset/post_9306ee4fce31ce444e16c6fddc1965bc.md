
## 8.1 DECISION TREES

it appears like one. When we splitting one set of points represented by random variable $X$ with split-line $(f_i, v)$, there are a few entropies we should consider.

- $H(X)$
- $H(X|Y=1)$. That is, the entropy of the set of points whose $f_i$ is less than $v$.
- $H(X|Y=0)$. That is, the entropy of the set of points whose $f_i$ is not less than $v$.

In some ways $H(X)$ is non-negotiable: we start with the set of points represented by $X$, and they have some entropy, now we wish to carve these points in a way to minimize the remaining entropy. Thus, the thing we want to minimize is a weighted average of the two sides of the split, where the weights are (proportional) to the sizes of two:

```
Minimize P(X<v)H(X|Y=1) + P(X\ge v)H(X|Y=0)
$=P(Y=1)H(X|Y=1) + P(Y=0)H(X|Y=0)$
```

An equivalent way of saying this is that we want to maximize the information we've learned, represented by how much $H(X)$ gets reduced after learning Y:

```
Maximize H(X) - P(Y=1)H(X|Y=1) + P(Y=0)H(X|Y=0)
H(X|Y)
```

For general indicator functions $Y$, we want to maximize something called the mutual information $I(X;Y)$. This depends on the conditional entropy of $X$ given $Y$:

```
$H(X|Y=y) = \sum_{k} P(X=k|Y=y) \log \frac{1}{P(X=k|Y=y)}$
H(X|Y) = \sum_{y} P(Y=y)H(X|Y=y)$
$I(X;Y) = H(X) - H(X|Y)$
```

Note that $I(X;Y)$ is non-negative and it only zero if the results of the split a decision tree have the same distribution of classes as the original set of points. Let's say you were using a decision tree to classify them as spam and ham. The preceding statement says, you gain no information if you take a set of (20 ham, 10 spam) and split it on some feature to get sets of (12 ham, 6 spam); because the empirical distribution of two resulting sets is equal to the original one.

Now we have addressed how to pick splits, let's talk about when to stop growing the tree. Because decision trees are powerful tools they can be used to represent arbitrarily complex decision boundaries. Thus, it is very easy to overfit them. One way is to keep carving up the feature space until the leaves are entirely pure (as in, they only contain points of a single class). As a result, when training decision trees, we always want to keep in mind a couple of heuristics for stopping early:

- Limited depth: keep track of the depth of each split, and don't go past depth $t$
- Information gain criterion: stop carving your splits don't reward you with enough information (i.e., a threshold for $I(X;Y)$

- Pruning: This isn't a method for stopping early. Rather it's the strategy of growing your tree out as far as you can, and then combining splits back together if so reduces your validation error.

All of these thresholds can be tuned by cross-validation.

## 8.2 Random Forests

Another way to combat overfitting is the use of random forests. A random forest is a set of decision trees whose outputs are aggregated in some way (usually majority vote) to produce the final answer to a classification problem. In addition, each tree of the forest will have some elements of randomness to them. Let's think about why this randomness is necessary.

Imagine you took the set of training points and you built k decision trees with the method of choosing splits in the previous section. What could you say about these trees? They would all be the same set in terms of what splits are chosen: Why because there is only one best of a set of training points, and if we use the same algorithm on the same set of training points, we'd get the same result.

There are two options: (1) change our algorithm for each tree, or (2) change our training points. The algorithm is perfectly good, so let's change the training points. In particular, we'll use the method of bagging: for each tree, we sample replacement some constant number of training points to "bag" and for training. This will avoid the problem of having identical decision trees...

...Or will it? Imagine you had an extremely predictive feature, like the appearance of the word "viagra" for classifying spam, or for your classification task. Then even if you took a random subsample of training points, your k trees would still be very similar, most likely choosing to split on the same features. Thus, randomness of our trees will come from:

- bagging: random sampling of training points per tree
- enforcing that a random sample of features be used for each tree

Both the size of the random sample of training points and the number of features per tree are hyperparameters that need to be tuned through cross-validation.

Remember why this is a good idea: One decision tree by itself is prone to overfitting the training set. However, if we have a bunch of them that are diverse and uncorrelated, then we can be more sure that their average is closer to the true classifier.

## 8.3 Boosting

We have seen in the case of random forests, combining many imperfect models can produce a single model that works very well. However, random forests treat each member of the forest equally, taking a majority vote or an average over their outputs. The idea of boosting is to combine the models (typically called weak learners in this context) in a more principled manner. Roughly, we want to:

- Treat each of the weak classifiers (e.g., trees in a random forest) as "features"
- Hunt for better "features" based on the current performance of the overall classifier

## 8.3. BOOSTING

The key idea is as follows: to improve our classifier, we should focus on finding learners that correctly classify the points which the overall boosted classifier is currently getting wrong. Boosting algorithms implement this idea by associating a weight with each training point and iteratively so misclassified points have relatively high weights. Intuitively, some points are “harder” to classify than others, so the algorithm should focus its efforts on those.

### AdaBoost

There are many flavors of boosting. We will discuss one of the most popular versions, known as AdaBoost (short for *adaptive boosting*). Its developers won the Gödel Prize for this work.

### Algorithm

We present the algorithm first, then derive it later.

1. Initialize the weight of all $n$ training points to $\frac{1}{n}$.
2. Repeat for $m=1, \dots, M$:
   (a) Build a classifier $G_m$ with data weighted according to $w_i$.
   (b) Compute the weighted error $e_m = \frac{\sum_{\text{misclassified}} w_i}{\sum_i}$.
   (c) Re-weight the training points as
$$w_i \leftarrow w_i \cdot \begin{cases} \sqrt{\frac{1-e_m}{e_m}} & \text{if misclassified} \\ \sqrt{\frac{e_m}{1-e_m}} & \text{otherwise} \end{cases}$$
   (d) Optional: normalize the weights $w_i$ to sum to 1.

We address the issue of step (a): how do we train a classifier if we want different samples differently? One common way to do this is to resample from the original set every iteration to create a new training set that is fed to the classifier. Specifically, we create a training set of size $n$ by sampling $n$ values from the original data, according to the distribution $w_i$. (This is why we renormalize the weights in step (d).) Data points with higher weights are more likely to be included in this training set, and the next classifier will place higher priority on such data points.

Suppose that our weak learners achieve an error $e_m/2$. To make sense of the formulas we see in the algorithm, note that for step (c), if the $i$-th data point is misclassified, the weight $w_i$ gets increased by a factor of $\sqrt{\frac{1-e_m}{e_m}}$ (more priority on sample $i$), while if it is correctly classified, its priority decreased. AdaBoost has a weakness that this aggressive reweighting can cause the classifier to focus too much on certain training examples—if the data is noisy with outliers, then this will weaken the algorithm’s performance.

We have not yet discussed how to make a prediction given our classifiers ($G_1, \dots, G_M$). One conceivable method is to use logistic regression with $G_m(x)$ as features. A smarter choice that is based on the AdaBoost algorithm is to set
$$\alpha_m = \frac{1}{2} \ln\left(\frac{1-e_m}{e_m}\right)$$
