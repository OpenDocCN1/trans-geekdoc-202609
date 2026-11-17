for each of the $n$ rows, rather than one for each of the $d$ columns. But it turns out most of the $\alpha_i$ values are 0 since all points outside the margins will have no contribution to the sum. Only the support vectors have nonzero coefficients and it is this sparsity that makes SVMs efficient from a computational point of view. The support vectors comprise only a small number of points in the training set.

We now have to find the values of the $\alpha_i$'s using some optimization method on a different problem with linear constraints. The dual setup is a maximization problem given by

```
maximize_{\boldsymbol{\alpha} \in \mathbb{R}^n} \sum_{i=1}^n \alpha_i - \frac{1}{2} \sum_{i,j=1}^n \alpha_i \alpha_j y_i y_j \mathbf{x}_i^T \mathbf{x}_j \text{ s.t. } \sum_{i=1}^n \alpha_i y_i = 0 \text{ and } 0 \le \alpha_i < C.
```

The details of the derivation of the above are not important here but rest assured that the $\alpha_i$'s can be computed in an efficient manner using it. Once found, the support vectors due to nonzero $\alpha_i$'s come in two flavors: some will be located exactly at the two margins while others will be located within the margins. This is controlled by the regularization factor $C$. The new criterion for the decision on some test point $\mathbf{x}$ is based on a sign test by replacing $\boldsymbol{\beta}$ with $\boldsymbol{\alpha}$, as follows:

```
\text{sgn}(\boldsymbol{\alpha}^T \boldsymbol{\beta} + \beta_0) = \text{sgn} \left( \sum_{i=1}^n \alpha_i y_i \mathbf{x}_i^T \mathbf{x} + \alpha_0 \right),
```

where $\beta_0 = \alpha_0$. If the sign test is positive, then $\mathbf{x}$ belongs to Class 1, otherwise it belongs to Class 0. Only linear boundaries are possible with this formulation, as mentioned before regarding SVCs. The interesting part is that it depends on $\mathbf{x}_i^T \mathbf{x}$ where $\mathbf{x}_i$ is from the training data and $\mathbf{x}$ is a new test data point. This can be written more generally as $k(\mathbf{x}_i, \mathbf{x})$, which is called a *kernel function*.

To obtain different classifiers, we simply choose different kernel functions and then compute the associated $\alpha_i$'s. Three useful kernel functions are the **linear kernel**,

```
k(\mathbf{x}_i, \mathbf{x}) = \mathbf{x}_i^T \mathbf{x},
```

the **polynomial kernel**, with expansion up to the $d^{th}$ power, given by

```
k(\mathbf{x}_i, \mathbf{x}) = (1 + \mathbf{x}_i^T \mathbf{x})^d,
```

and the **radial basis function (RBF) kernel** or Gaussian kernel,

```
k(\mathbf{x}_i, \mathbf{x}) = \exp(-\gamma ||\mathbf{x}_i - \mathbf{x}||^2).
```

The latter one, the Gaussian kernel, is the most popular and produces a nonlinear decision boundary that is quite adept at capturing complex boundaries between the two classes. As a result, SVM is a powerful alternative to logistic regression.

The RBF kernel has the property of decreasing in value as a function of the distance from a support vector (i.e. it is an exponential decay that depends on the $\gamma$ hyperparameter). The SVM has an added advantage over CELR and LCLR in that it does not require specification of all the various polynomial expansions of the variables to create the needed features. It will figure that out for itself from the original variables and data using the RBF. However, the user must adjust two hyperparameters, $\gamma$ and $C$, to obtain satisfactory results. After computing $\boldsymbol{\alpha}$ using the training set, the decision of whether $\mathbf{x}$ belongs to Class 1 is based only on

```
\text{sgn} \left( \sum_{i=1}^n \alpha_i y_i k(\mathbf{x}_i, \mathbf{x}) + \alpha_0 \right) > 0
```