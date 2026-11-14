
Manhattan distance is calculated as the sum of the absolute difference of the Cartesian coordinates of two points. The formula for Manhattan distance is the sum of the lengths between a new data point (`x`) and an existing trained data point (`y`) using a line segment on the coordinate axes (Equation 6.2).

Minkowski distance is the distance between two points in the normed vector space and is a generalization of the Euclidean distance and the Manhattan distance (Equation 6.3). In the formula for Minkowski distance when `p` = 2, we get the Euclidian distance, also known as L2 distance. When `p` = 1 we get the Manhattan distance, also known as L1 distance, city-block distance, and LASSO. The distance functions as follows:

```
(6.1)  

$$\text{Euclidean Distance} = \sqrt{\sum\limits_{i = 1}^{k}\left( x_{i} - y_{i} \right)^{2}}$$  
```

```
(6.2)  

$$\text{Manhattan Distance} = \sum\limits_{i = 1}^{k} \mid x_{i} - y_{i} \mid$$  
```

```
(6.3)  

$$\text{Minkowski Distance} = \left( \sum\limits_{i = 1}^{k}\left( \mid x_{i} - y_{i} \mid \right)^{q} \right)^{1/q}$$  
```

[Figure 6.5](#ch6.xhtml#fig6_5)

![Figure 6.5 Distance functions.](images/fig6_5_B.jpg)

[Figure 6.5 Distance functions.](#ch6.xhtml#R_fig6_5)

### 6.2.5 Two Parameters of KNN

Although the KNN algorithm is nonparametric, there are two parameters we usually use to build the model: `k` (the number of neighbours that will vote) and the **distance metric**.

There are no strict rules around the selection of `k`. It really depends on the data set as well as your experience when it comes to choosing an optimal `k`. When `k` is small, the prediction would be easily impacted by noise. When `k` is getting larger, although it reduces the impact of outliers, it will introduce more bias. (Think about when we increase `k` to `n`, the number of data points in the data set. The prediction will be the majority class in the data set).

The selection of the other parameter, **distance metric**, also varies on different cases. By default, people use Euclidean distance (L2 norm). However, Manhattan distance and Minkowski distance might also be great choices in certain scenarios.

The two parameters that are used to assess different `k` values are the training error rate and the validation error rate. [Figure 6.6](#ch6.xhtml#fig6_6) shows the plot of the training error rate for varying values of `k`.

![Figure 6.6 Training error rate.](images/fig6_6_B.jpg)

[Figure 6.6 Training error rate.](#ch6.xhtml#R_fig6_6)

At `k` = 1 the error is always zero and the prediction is always accurate. However, the validation error curve shows a different picture. [Figure 6.7](#ch6.xhtml#fig6_7) shows the validation error curve for varying value of `k`.

![Figure 6.7 Validation error curve.](images/fig6_7_B.jpg)

[Figure 6.7 Validation error curve.](#ch6.xhtml#R_fig6_7)

At `k` = 1, the boundaries are overfitted. The error rate initially decreases and reaches a minimum, after which it increases with increasing `k`. To get the optimal value of `k`, we can segregate the training and validation data sets and then plot the validation error curve to get the optimal value of `k`. This value of `k` should be used for all predictions.

### 6.2.6 KNN Algorithm

*   Store all input data in the training set.
*   Initialize the value of `k`.
*   For each sample in the test set,
    *   Search for the `k` nearest samples to the input sample using a Euclidean distance measure. (other distances such as Hamming or Manhattan, or metrics such as Chebyshev, cosine, etc. can also be used.)
*   For classification, compute the confidence for each class as
    *   `C[i]`/`k` (where `C[i]` is the number of samples among the `k` nearest neighbors belonging to class `i`).
    *   The classification for the input sample is the class with the highest confidence.

### 6.2.7 Pros and Cons of KNN

There are multiple advantages of using KNN:

1.  It is a simple machine learning model. It is also very easy to implement and interpret.
2.  There is no training phase of the model.
3.  There are no prior assumptions on the distribution of the data. This is especially helpful when we have ill-tempered data.
4.  KNN has a relatively high accuracy.

Of course, there are disadvantages of the model:

1.  High requirements on memory. We need to store all the data in memory in order to run the model.
2.  Computationally expensive. Recall that the model works in the way that it selects the `k` nearest neighbors. This means that we need to compute the distance between the new data point to all the existing data points, which is quite expensive in computation.
3.  Sensitive to noise. Imagine we pick a really small `k`; the prediction result will be highly impacted by the noise if there is any.

## 6.3 Decision Based Methods—Decision Tree Algorithm

### 6.3.1 Decision Tree Based Algorithm

Decision trees, an induction learning technique, are essentially if-then rules and can be easily interpreted by humans. Decision trees are used to predict the relationship between input variables and the desired target (output) variable based on a series of Boolean tests.

The decision tree algorithm can be used for solving both **regression and classification problems**. The decision tree creates a training model by **learning simple decision rules** inferred from prior data (training data). This model is then used to predict the class of the unknown data. Instances are classified by decision trees starting at the root of the tree and, depending on the value of the attribute associated with the example, choosing the appropriate sub-tree at each decision node until a leaf node is reached.

Decision trees can be classified depending on whether the target variable is categorical or continuous as a **categorical variable decision tree** and **continuous variable decision tree**, respectively.

### 6.3.2 Terminology Associated with Decision Trees

[Figure 6.8](#ch6.xhtml#fig6_8) shows the components of a decision tree:

1.  **Root node**: This is the initial node of the decision tree and represents the entire population. A decision tree is grown by starting at the root node and dividing or splitting the sample space into homogeneous sets.
2.  **Splitting**: Starting from the root node and dividing a node into two or more sub-nodes is called splitting. There exist several methods to split a decision tree, involving different metrics (e.g., information gain, Gini impurity).
3.  **Decision node**: The internal node of a decision tree which can be split into sub-nodes is called the decision node.
4.  **Leaf/terminal node**: This represents a final node and cannot be further split.
5.  **Pruning**: By removing sections that are not critical, in other words removing some sub-nodes of a decision node, we reduce the size of the decision tree. This pruning process enables better generalization and less overfitting, leading to better predictive accuracy.
6.  **Branch**: A subtree rooted at the root or any of the decision nodes is called a branch.
7.  **Parent and child node**: A parent node is divided into sub-nodes or children of the node.

![Figure 6.8 Components of decision trees.](images/fig6_8_B.jpg)

[Figure 6.8 Components of decision trees.](#ch6.xhtml#R_fig6_8)
