
the ensemble and aggregated using either majority voting (for classification) or averaging (for regression).

## 7.2.4 Exercise: bootstrap sampling

To visualize what a bootstrapped data looks like, open your IDE, import numpy as np, and copy and paste the following function:

```python
def bootstrap_sample(dataset):
    """Sample from the dataset with
    replacement:
        input:
            dataset: shape (N,M)
        output:
            samples: shape (N,M)
    """

    n_sample = dataset.shape[0]
    indices=np.random.choice(n_sample, n_sample,
                        replace=True)

    return dataset[indices]
```

Then, create a random set with 10 rows (examples) and 3 features (columns). Pass the data through the passed function a few times and observe how the output changes. You will see that the output is fixed to the same size as the input, which is the default setup for bagging and forests.²

## 7.2.5 Random forests

While bagging seeks to optimize uncorrelated models solely by training on different bootstrapped samples from the data, random forests [5] further randomization by presenting each node of the tree with a random subset of the total available features. In this way, each decision stump is trained—without seeking the optimal feature for that—forcing each tree to find several different solutions to each classification problem, increasing randomization, and further reducing correlations in the predictions across all trees. The overall effect is to reduce model variance and the chance of overfitting. (see Sect. 7.2, 8), random forests always build ensembles of trees.

> ² Skeleton code and the solution is available from github.com/MachineLearningBiomedicalApplication-notebooks.

## 7.2.6 Training bagging and forests with scikit-learn

To implement bagging and forests with scikit-learn, import the models from the ensemble base class, e.g., for classification,

```python
from sklearn.ensemble import BaggingClassifier
from sklearn.ensemble import RandomForestClassifier

n_trees=50

# create a bagged ensemble of 50 decision trees
clf=BaggingClassifier(DecisionTreeClassifier(),
    n_estimators=n_trees)

# create a random forest of 50 trees
# with 30% of the total number of features
clf=RandomForestClassifier(n_estimators=n_trees,
    max_features=0.3)
```

You should consider the first argument of the bagging classifier is the choice of base model, whereas for forests there is no choice. In both cases, you can control the size of the ensemble using n_estimators.

The arguments of the random forest class parallel those of the decision tree class, max_features specifically determines the degree of undersampling of the features at each node. In example, the use of a float (0.3) sets the number of randomly selected features to 30% of the total available. For full options, on all arguments, see the scikit-learn documentation.

## 7.2.7 Out-of-bag error

One advantage of training bagged ensembles is that it is possible to return an estimate of the likely generalization by testing each tree on the examples that were left out during bootstrap sampling. These are known as out-of-bag (oob) samples. For large data sets, this can be set to approximately 37%.

Once all models are trained, out-of-bag predictions for each training example can be combined, using averaging or majority voting; then, a final score can be calculated from the accuracy (classification) or error (regression) across all examples. To track error using scikit-learn, oob_score=True, when instantiating your model, e.g.,

```python
# track oob error during training
clf=BaggingClassifier(DecisionTreeClassifier(),
    n_estimators=n_trees, oob_score=True)
```

The oob performance can be returned after training using the oob_score_ attribute:

## 7.2.8 Boosting

```python
# train model
clf.fit(X,Y)
# report oob score
print("the oob score is ".format(clf.oob_score))
```

Boosting contrasts with bagging and forests in that it tags weak learners serially, one after another. After each model is fit, misclassified examples are identified and given higher importance for subsequent runs.

To see how this works, the toy example is in Fig. 7.8. In this case, the various classes of example are indicated by pluses or minuses. We can see from Fig. 7.8a, perfect supervision would require a nonlinear decision boundary. 7.8b-f simulate the process of boosting. 7.8b an initial axis-aligned decision step is fit by the red box. This correctly classifies two red crosses and all of the minus class. However, three red crosses are misclassified as belonging to the blue class. 7.8c shows how boosting upgrades the misclassified examples in the second round, ensuring that these are correctly classified by the second classifier (shown in Fig. 7.8d); now here three blue are misclassified and so boosted for the third round. The third and final classifier is the ensemble in Fig. 7.8e. This trains an axis-aligned classifier on the vertical axis, correctly classifying the weighted cross and minus class. We can see that, when all three classifiers in the ensemble are combined (with weightings as in Fig. 7.8f) the final result achieves correct classification for all examples.

In this way boosting can learn precise, nonlinear models that significantly improve the accuracy of the ensemble relative to individual learners. Boosting can be shown that, even when training performance has saturated, boosting continues to refine predictions by the margins and further optimizing the losses of each base learner [42]. In other words, it seeks to make the margins between classes and bigger, similarly to the behavior of support machines.

## 7.2.9 AdaBoost

There are many variants of boosting that differ primarily in the way they combine and weight during training. Here, we will focus on one of the earliest and best known, AdaBoost [15], where we will assume each learner is an axis-aligned decision stump, similar to that in Fig. 7.8.

The AdaBoost classifier (Algorithm 7.2) starts by giving all examples in the training set equal weights ($w_i = \frac{1}{n}$). Then, for each tree or stump, the algorithm first estimates $p^i$ (which represents normalized weights, or probabilities, for each example).

Decision trees and ensemble learning 167

img/d219b4c20ff50f4b97845decacecb185_0.png
img/d219b4c20ff50f4b97845decacecb185_1.png
img/d219b4c20ff50f4b97845decacecb185_2.png
img/d219b4c20ff50f4b97845decacecb185_3.png
img/d219b4c20ff50f4b97845decacecb185_4.png
img/d219b4c20ff50f4b97845decacecb185_5.png

**Figure 7.8** Boosting toy example.

**Algorithm 7.2** AdaBoost classifier.
Given $\mathbf{x} \in \mathbf{X}$ and $y_i \in \{0, 1\}$
Assign all $n$ examples equal weight $w_t' = 1/n$
**for** $t$ in $E$ **do**
$\quad \mathbf{w}^t' = \mathbf{w}^t / \sum w_i^t$ // for each tree $t$ in the ensemble
$\quad$ convert weights into probabilities
$\quad \quad f_t(\mathbf{X}, \theta) = \text{train\_stump}(\mathbf{p}, \mathbf{y})$ // train decision stump
$\quad \quad \epsilon \leftarrow \sum p_i |f_t(\mathbf{x}_i, \theta) - y_i|$ // calculate the error
$\quad \quad \beta_t \leftarrow \frac{1-\epsilon}{\epsilon}$ // update weights
$\quad \quad w_i^{t+1} \leftarrow w_i' \beta_t / |f_t(\mathbf{x}_i, \theta) - y_i|$
**end for**

weights are passed to the weak learner for iteration, directing it to minimize the relative cost to that probability distribution—in other words, it will learn a weighted cost that will pay more attention to classifying higher weighted examples. After that, an error ($e$) is calculated over all the examples as a weighted sum, where $|f(x_i, \theta) - y_i|$ will be 0, if the predicted $f(x_i, \theta)$ has the same class as the true label ($y_i$), and will be 1. Therefore, there is zero contribution to the error of correctly classified examples, and the contribution from incorrectly classified examples is larger for examples that have been upweighted in previous rounds. Note that the error is never allowed to drop below 0.5 or 50% accuracy because this would mean it performs worse than random chance. If this occurs, the tree or stump is reset and a different learner is fit.

In the next step, the error is turned into a $\beta_i$ value, bounded between 0 and 1, with smaller $\beta_i$ corresponding to smaller error. This is used to re-weight examples for the next round of boosting. Counter to the example in Fig. 7.8, the actual effect is that since $|f(x_i, \theta) - y_i|$ is 1 for incorrect predictions, which makes the exponent grow and reduces the $\beta_i$ term to 1. This indirectly upweights misclassified examples, during probability estimation in the next round probability is estimated by normalizing over the sum of weights. The lower the overall error, the smaller the $\beta_i$ and hence the more correctly classified examples for that are downweighted. Finally, at the end, the prediction for each example, is aggregated from the predictions across all base learners as a weighted majority vote.

Regression (Algorithm 7.3) [12] starts similarly but diverges at the point where the error is calculated. Typically a range of choices are offered for estimation of the loss including absolute error, mean squared error or exponential. An average loss is then estimated across training samples, and used to estimate the $\beta_i$ parameter. Similarly to classification, the smaller the loss, the more the weight is reduced for the correctly predicted examples. The final prediction is calculated as a weighted median across all models in the ensemble.

## 7.2.10 Boosting with scikit-learn

Scikit-learn implements Adaboost [15] and gradient boosting [16]. For example, to create a classifier instance of Adaabo implement:

```python
from sklearn.ensemble import AdaBoostClassifier
```

```python
n_trees=50
```

```python
# create a boosted ensemble of 50 trees
clf=AdaBoostClassifier(DecisionTreeClassifier(),
    n_estimators=n_trees)
```
