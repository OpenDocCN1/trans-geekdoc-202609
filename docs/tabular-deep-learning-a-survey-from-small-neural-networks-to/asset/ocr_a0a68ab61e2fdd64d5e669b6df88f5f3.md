• Binary values: A special case of categorical features, where the feature can have only two values (generally 0 or false). An example is the vital status of a patient, which can be either alive or dead.

• Ordinal values: A special type of categorical feature, where the values are discrete, there is an intrinsic order. Examples include the frequency of gym activity (sometimes > rarely) or highly expressed in discrete values (age > short).

• Continuous values: A feature that contains continuous values.

For a linear model, the relationship is typically given by:

```
$f(X) = WX + \mathbf{b}$
```

where $W \in \mathbb{R}^{d 	imes n}$ is a matrix of weights, and $\mathbf{b} \in \mathbb{R}^d$ is the bias.

In the case of a neural network with a single hidden layer (a multilayer perceptron), a non-linear function $\sigma$ is introduced:

```
$f(X) = \sigma(WX + \mathbf{b})$
```

where $W \in \mathbb{R}^{d \times n}$ and represents the number of neurons in the hidden layer.

In a multilayerayer perceptron (MLP) with multiple layers, the representation at layer $l+1$ is:

```
$H^{(l+1)} = \sigma(W^{(l)}H^{(l)} + \mathbf{b}^{(l)})$
```

For a neural network training, the difference between the predictions and the labels is minimized by a loss function:

```
$\min_{\theta} \sum_{i=1}^{N} L(f(x_i; \theta), y_i)$
```

In some cases, a regularization term (where $\theta$ is a generic function) may be added to training:

```
$\min_{\theta} \sum_{i=1}^{N} L(f(x_i; \theta), y_i) + \lambda \Omega(\theta)$
```

The specific definition of $\hat{y}$ and $y$ depends on the task, such as cross-entropy for classification and mean squared error for regression.

| ID | Height | Gender | Age |
|---|---|---|---|
| 1 | High | Male | 35 |
| 2 | Medium | Male | 48 |
| 3 | Low | Low | NA |
| 4 | Female | Male | 31 |

Figure 1: An example of a tabular dataset highlighting challenges. The first column (ID) represents an index (in red and bold), the second numerical feature cannot reach such values. The third column represents a categorical variable, and the fourth an ordinal categorical variable that should be respected. The last column has a missing value (in red and bold) that should be input. By convention, rows represent, and columns features

# 2.1. Background

More formally, a tabular dataset is described as consisting of $n$ instances and $d$ features, respectively denoted as $X \in \mathbb{R}^{n \times d}$ (sometimes denoted as $X \in \mathbb{R}^d$), and $x_j$ denotes the $j$-th feature of the $i$-th example. A example is

This definition applies to both unsupervised and supervised learning. In supervised learning, each case is associated with a label, $y$. The target value is a single value (vector) given below:

+   - for binary classification,

+   - $[C] = [1, 2, \dots, C]$ for multi-class classification,

+   - for regression.

For a supervised learning task, given a dataset $\mathcal{D} = \{(x_i, y_i)\}_{i=1}^N$, we aim to find a mapping $f$ that maps inputs to outputs $y$, i.e., to obtain the prediction $\hat{y} = f(x_i; \theta)$, for instance $i$. In the case of a parametric model, this can be expressed as $\hat{y} = f(x, \theta)$. This function is learned by minimizing the distance between the predicted $\hat{y}$ and the true labels $y$.

# 2.2. Tabular data

Regression and classification tasks are unique. The simplest but most common case of classification task is binary classification. The starting point of classification evaluation is the confusion matrix (a matrix representing all possible combinations of real labels). Next, a single value is obtained from the confusion matrix by aggregating statistics. These metrics capture a particular aspect of the task, and each has its own flaws.

However, it is useful to reduce the confusion matrix to a single metric [25]. Accuracy, Area Under the Curve (AUC), and F1 score are the most widely used metrics, as it can be thought of as the probability of observing a correct prediction in testing. On the other hand, error rate (false negatives and false positives are treated equally) is sensitive to imbalance (if one class dominates, one can achieve high accuracy by predicting the majority class), and does not reflect model confidence (an uncertain but correct prediction