Classification 99

![](bbox=[0.298, 0.093, 0.722, 0.266])

**Figure 4.7** Interpretation of slack variables $\zeta_i$.

margin objective can be written as

$$\minimize \frac{1}{2}\mathbf{w}^T\mathbf{w} + C\sum_{i=1}^{N} \zeta_i$\n$\text{subject to } y_i(\mathbf{x}_i) \geq 1 - \zeta_i, \zeta_i \geq 0 \text{ for } i=1, \dots, N.$

The hyperparameter $C$ represents the trade-off between margin width and margin violations. For large $C$ we will have smaller margins with fewer violations, for small $C$ we will have larger margins with more violations.
			The soft-margin objective has to be minimized by minimized numerically, usually using quadratic solvers [7]. Alternatively, we can equivalently express the soft-margin objective by the hinge loss

$$\hat{\mathbf{w}} = \arg\min_{\mathbf{w}} C\sum_{i=1}^{N} \max(0, 1-\mathbf{w}^T\mathbf{x}+b) + \frac{1}{2}\mathbf{w}^T\mathbf{w}.$

that can be minimized using a gradient descent with subgradients (Sec. 3.1.2).
			In scikit-learn the linear support vector classifier model can be formulated as

```
from sklearn.svm import LinearSVC
model = LinearSVC(C=10)
```

Alternatively, it is implemented as a stochastic gradient descent classifier with hinge loss

```
from sklearn.linear_model import SGDClassifier
model = SGDClassifier(loss='hinge', alpha = 0.01)
```

Here, the parameter alpha is the hyperparameter for the ridge penalty, and it is equal to 1/C.