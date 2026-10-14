
$$ G = \frac{2}{5} G_{left} + \frac{3}{5} G_{right} = \frac{2}{5} \times 0 + \frac{3}{5} \times \left(1 - \frac{2^2}{3} - \frac{1^2}{3}\right) = 0.27 \tag{5.46} $$

Here, $G_{left}$ is the Gini index of $\{x_i, y_i: x_{ij} \le 2\}$ and is equal to zero, since both class labels are equal to 1 (i.e., a pure leaf cluster) and $G_{right}$ is the Gini index of $\{x_i, y_i: x_{ij} > 2\}$ and contains a mix of class labels $y_{right} = [2,2,3]$.

The key to CART algorithm is finding the optimal feature and threshold such that the cost (e.g., Gini index) is minimized. During training, we’ll need to iterate through every feature one by one and compute the Gini cost for all possible thresholds for that feature. But how do we compute $\tau_j$ a set of all possible thresholds for feature $j$? We can sort the training data $X[:, j]$ in $O(n \log n)$ time and consider all midpoints between two adjacent data values. Next, we’ll need to compute the Gini index for each threshold that can be done as shown in equation 5.47. Let $m$ be the size of the node and $m_k$ be the number of points in the node that belong to class $k$.

$$ G = 1 - \sum_{k=1}^{K} \pi_k^2 = 1 - \sum_{k=1}^{K} \left(\frac{m_k}{m}\right)^2 \tag{5.47} $$

We can iterate through the sorted thresholds $\tau_j$ in $O(n)$ time and compute the Gini index that would result in applying that threshold in each iteration. For $i$-th threshold, we get the following.

$$ G_i = \frac{i}{m} G_i^{left} + \frac{m - i}{m} G_i^{right} $$

$$ G_i^{left} = 1 - \sum_{k} \left(\frac{m_k^{left}}{i}\right)^2 $$

$$ G_i^{right} = 1 - \sum_{k} \left(\frac{m_k^{right}}{m - i}\right)^2 \tag{5.48} $$

Having found the optimum feature and threshold, we split each node recursively until the maximum depth is reached. Once we’ve constructed a tree during training, given test data, we simply traverse the tree from root to leaf, which stores our class label. We can summarize the CART algorithm in the pseudo-code in figure 5.14.

As we can see from the definition of TreeNode, it stores the predicted class label, id of the feature to split on and the best threshold to split on, pointers to the left and right subtrees, as well as the Gini cost and size of the node. We can grow the decision tree recursively by calling the grow_tree function, as long as the depth of the tree is less than the maximum depth determined ahead of time. First, we compute the class label via majority vote and the Gini index for training labels.

```
1: class TreeNode(gini, num_samples, num_samples_class, class_label):
2: self.gini = gini // gini cost
3: self.num_samples = num_samples // size of node
4: self.num_samples_class = num_samples_class //number of pts with label k
5: self.class_label = class_label //predicted class label
6: self.feature_idx = 0 //idx of feature to split on
7: self.threshold = 0 //best threshold to split on
8: self.left = None //left subtree pointer
9: self.right = None //right subtree pointer
10: function grow_tree(X_train, y_train, depth)
11: class_label = majority_vote(y_train)
12: gini = compute_gini(y_train)
13: node = new TreeNode(gini, class_label)
14: //split recursively until max depth is reached
15: if depth < max_depth
16:   idx, threshold = best_split(X_train, y_train)
17:   if idx is not None:
18:     indices_left = X_train[:,idx] < threshold
19:     node.feature_index = idx
20:     node.left = grow_tree(X_left, y_left, depth + 1)
21:     node.right = grow_tree(X_right, y_right, depth +1)
22: return node
```

## Figure 5.14 CART decision tree algorithm pseudo-code

Next, we determine the best split by iterating over all features and over all possible splitting thresholds. Once we determine the best feature idx and feature threshold to split on, we initialize left and right pointers of the current node with new TreeNode objects that contain data less than the splitting threshold and greater than the splitting threshold, respectively. We iterate in this fashion until reaching the maximum tree depth. We are now ready to implement the CART algorithm.

## Listing 5.5 CART decision tree algorithm

```
import numpy as np
import matplotlib.pyplot as plt

from sklearn.datasets import load_iris
from sklearn.metrics import accuracy_score
from sklearn.model_selection import train_test_split

class TreeNode():
    def __init__(self, gini, num_samples, num_samples_class, class_label):
        self.gini = gini          ← Gini cost
        self.num_samples = num_samples          ← Size of the node
        self.num_samples_class = num_samples_class
        self.class_label = class_label          ← Predicted class label

Number of node points with the label k → self.num_samples_class
```
```
self.feature_idx = 0
self.threshold = 0
self.left = None
self.right = None

class DecisionTreeClassifier():
    def __init__(self, max_depth = None):
        self.max_depth = max_depth

    def best_split(self, X_train, y_train):
        m = y_train.size
        if (m <= 1):
            return None, None

        mk = [np.sum(y_train == k) for k in range(self.num_classes)]

        best_gini = 1.0 - sum((n / m) ** 2 for n in mk)
        best_idx, best_thr = None, None

        #iterate over all features
        for idx in range(self.num_features):

            thresholds, classes = zip(*sorted(zip(X[:, idx], y)))

            num_left = [0]*self.num_classes
            num_right = mk.copy()

            for i in range(1, m):
                k = classes[i-1]

                num_left[k] += 1
                num_right[k] -= 1

                gini_left = 1.0 - sum(
                    (num_left[x] / i) ** 2 for x in range(self.num_classes)
                )

                gini_right = 1.0 - sum(
                    (num_right[x] / (m - i)) ** 2 for x in
                    range(self.num_classes)
                )

                gini = (i * gini_left + (m - i) * gini_right) / m

                if thresholds[i] == thresholds[i - 1]:
                    continue

                if (gini < best_gini):
                    best_gini = gini
                    best_idx = idx
                    best_thr = (thresholds[i] + thresholds[i - 1]) / 2
```
Best threshold to split on

idx of the feature to split on

Left subtree pointer

Right subtree pointer

Number of points of class k

Gini of the current node

Sorts data along a selected feature

Iterate over all possible split positions

Midpoint

```
#end if
#end for
#end for
return best_idx, best_thr

def gini(self, y_train):
    m = y_train.size
    return 1.0 - sum((np.sum(y_train == k) / m) ** 2 for k in
        range(self.num_classes))

def fit(self, X_train, y_train):
    self.num_classes = len(set(y_train))
    self.num_features = X_train.shape[1]
    self.tree = self.grow_tree(X_train, y_train)

def grow_tree(self, X_train, y_train, depth=0):

    num_samples_class = [np.sum(y_train == k) for k in
        range(self.num_classes)]
    class_label = np.argmax(num_samples_class)

    node = TreeNode(
        gini=self.gini(y_train),
        num_samples=y_train.size,
        num_samples_class=num_samples_class,
        class_label=class_label,
    )

    if depth < self.max_depth:
        idx, thr = self.best_split(X_train, y_train)
        if idx is not None:
            indices_left = X_train[:, idx] < thr
            X_left, y_left = X_train[indices_left], y_train[indices_left]
            X_right, y_right = X_train[~indices_left],
            y_train[~indices_left]
            node.feature_index = idx
            node.threshold = thr
            node.left = self.grow_tree(X_left, y_left, depth + 1)
            node.right = self.grow_tree(X_right, y_right, depth + 1)

    return node

def predict(self, X_test):
    return [self.predict_helper(x_test) for x_test in X_test]

def predict_helper(self, x_test):
    node = self.tree
    while node.left:
        if x_test[node.feature_index] < node.threshold:
            node = node.left
        else:
            node = node.right
    return node.class_label
```

Split recursively until the maximum depth is reached
