
![](img/c2ad4b400bf63af9804b2d44510f76a6_189_0.png)

Projection onto x2, Projection onto x1, Fisher most discriminant projection: $w$, Separating hyperplane, $x$: Errors, $S_W$, $S_B$, $\mu_1$, $\mu_0$, $w$.

$$p(C_k|x) = \frac{p(C_k)p(x|C_k)}{p(x)}$$

Where $p(x)$ is the marginal distribution obtained by summing over classes. As usual, the denominator in Bayes’ theorem can be found in terms of the quantities appearing in the numerator, because

$$p(x) = \sum_{k} p(x|C_k)p(C_k)$$

- 4. Classify $x$ using the Maximum-a-Posteriori probability: $C_k = \arg\max_{C_k} p(C_k|x)$

LDA is a **generative model** since the class-conditional distributions can be used to generate samples of each class.

LDA is useful to deal with imbalanced group sizes (e.g., $N_1 \gg N_0$) since prior probabilities can be used to explicitly re-balance the classification by setting $p(C_0) = p(C_1) = 1/2$ or whatever seems relevant.

LDA can be generalised to the multiclass case with $K > 2$.

With $N_1 = N_0$, LDA leads to the same solution as Fisher’s linear discriminant.

### 13.2.1 Exercise

How many parameters are required to estimate to perform a LDA?

```python
import numpy as np
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis as LDA

# Dataset
n_samples, n_features = 100, 2
mean0, mean1 = np.array([0, 0]), np.array([0, 2])
Cov = np.array([[1, .8],[.8, 1]])
np.random.seed(42)
X0 = np.random.multivariate_normal(mean0, Cov, n_samples)
X1 = np.random.multivariate_normal(mean1, Cov, n_samples)
X = np.vstack([X0, X1])
y = np.array([0] * X0.shape[0] + [1] * X1.shape[0])

# LDA with scikit-learn
lda = LDA()
proj = lda.fit(X, y).transform(X)
y_pred_lda = lda.predict(X)

errors = y_pred_lda != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y_pred_lda)))
```

```
/home/edouard/anaconda3/lib/python3.6/site-packages/_pytest/fixtures.py:844:
DeprecationWarning: The convert argument is deprecated in favor of converter.
It will be removed after 2019/01.
params = attr.ib(convert=attr.converters.optional(tuple))
```

```
Nb errors=10, error rate=0.05
```

## 13.3 Logistic regression

Logistic regression is called a generalized linear model, i.e., it is a linear model with a link function that maps the output of linear multiple regression to the posterior probability of each class $p(C_k|x) \in [0, 1]$ using the logistic sigmoid function:

$$p(C_k|w, x_i) = \frac{1}{1 + \exp(-w \cdot x_i)}$$

![](img/c2ad4b400bf63af9804b2d44510f76a6_191_0.png)

Fig. 13.2: logistic sigmoid function

Logistic regression seeks to minimize the likelihood $L$ as the loss function $\mathcal{L}$:

$$\min L(w) = \prod_{i}^{N} p(C_k|w, x_i)$$

Practically, the loss function $\mathcal{L}$ is the log-likelihood:

$$\min \mathcal{L}(w) = \log L(w) = \sum_{i}^{N} \log p(C_k|w, x_i)$$

In the two-class case the algorithms simplify considerably by coding the two classes ($C_0$ and $C_1$) via a 0/1 response $y_i$. Indeed, since $p(C_0|w, x_i) = 1 - p(C_1|w, x_i)$, the log-likelihood can be re-written:

$$\log L(\boldsymbol{w}) = \sum_{i}^{N} \{ y_i \log p(C_1|\boldsymbol{w}, \boldsymbol{x}_i) + (1 - y_i) \log(1 - p(C_1|\boldsymbol{w}, \boldsymbol{x}_i)) \} \tag{13.8}$$

$$\log L(\boldsymbol{w}) = \sum_{i}^{N} \{ y_i \boldsymbol{w} \cdot \boldsymbol{x}_i - \log(1 + \exp(\boldsymbol{w} \cdot \boldsymbol{x}_i)) \} \tag{13.9}$$

(13.10)

Logistic regression is a **discriminative model** since it focuses only on the posterior probability of each class $p(C_k|x)$. It only requires to estimate the $P$ weights of the $w$ vector. Thus it should be favoured over LDA with many input features. In small dimension and balanced situations it would provide similar predictions to LDA.

However imbalanced group sizes cannot be explicitly controlled. It can be managed using a reweighting of the input samples.

```python
from sklearn import linear_model
logreg = linear_model.LogisticRegression(C=1e8, solver='lbfgs')
# This class implements regularized logistic regression. C is the Inverse of regularization strength.
# Large value => no regularization.

logreg.fit(X, y)
y_pred_logreg = logreg.predict(X)

errors = y_pred_logreg != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y_pred_logreg)))
print(logreg.coef_)
```

```
Nb errors=10, error rate=0.05
[[-5.1516729  5.57303883]]
```

### 13.3.1 Exercise

Explore the Logistic Regression parameters and propose a solution in cases of highly imbalanced training dataset $N_1 \gg N_0$ when we know that in reality both classes have the same probability $p(C_1)=p(C_0)$.

## 13.4 Overfitting

VC dimension (for Vapnik–Chervonenkis dimension) is a measure of the **capacity** (complexity, expressive power, richness, or flexibility) of a statistical classification algorithm, defined as the cardinality of the largest set of points that the algorithm can shatter.

Theorem: A linear classifier in $\mathbb{R}^P$ has VC dimension of $P + 1$. Hence in dimension two ($P = 2$) any random partition of 3 points can be learned.

![](img/c2ad4b400bf63af9804b2d44510f76a6_193_0.png)

Fig. 13.3: In 2D we can shatter any three non-collinear points

## 13.5 Ridge Fisher’s linear classification (L2-regularization)

When the matrix $S_W$ is not full rank or $P \gg N$, the Fisher most discriminant projection estimate is not unique. This can be solved using a biased version of $S_W$:

$$S_W^{Ridge} = S_W + \lambda I$$

where $I$ is the $P \times P$ identity matrix. This leads to the regularized (ridge) estimator of the Fisher’s linear discriminant analysis:

$$w^{Ridge} \propto (S_W + \lambda I)^{-1} (\mu_1 - \mu_0)$$

![](img/c2ad4b400bf63af9804b2d44510f76a6_193_1.png)

Fig. 13.4: The Ridge Fisher most discriminant projection

Increasing $\lambda$ will:

- Shrink the coefficients toward zero.
- The covariance will converge toward the diagonal matrix, reducing the contribution of the pairwise covariances.

## 13.6 Ridge logistic regression (L2-regularization)

The **objective function** to be minimized is now the combination of the logistic loss $\log L(w)$ with a penalty of the L2 norm of the weights vector. In the two-class case, using the 0/1 coding we obtain:

$$\min \mathcal{L}_{\text{ridge}}(w) = \log L(w) + \lambda \|w\|^2 \tag{13.11}$$

$$= \sum_{i}^{N} \{ y_i w^T x_i - \log(1 + \exp(w^T x_i)) \} + \lambda \|w\|^2 \tag{13.12}$$

(13.13)

```python
# Dataset
# Build a classification task using 3 informative features
from sklearn import datasets

X, y = datasets.make_classification(n_samples=100,
                                    n_features=20,
                                    n_informative=3,
                                    n_redundant=0,
                                    n_repeated=0,
                                    n_classes=2,
                                    random_state=0,
                                    shuffle=False)
```

```python
from sklearn import linear_model
lr = linear_model.LogisticRegression(C=1)
# This class implements regularized logistic regression. C is the Inverse of regularization strength.
# Large value => no regularization.

lr.fit(X, y)
y_pred_lr = lr.predict(X)

errors = y_pred_lr != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y)))
print(lr.coef_)
```

```
Nb errors=26, error rate=0.26
[[-0.12061092  0.7357655  -0.01842318 -0.10835785  0.25328562  0.4221318
   0.15152184  0.16522461  0.84404799  0.01962765 -0.15995078 -0.01925974
  -0.02807379  0.42939869 -0.06368702 -0.07922044  0.15529371  0.29963205
   0.54633137  0.03866807]]
```

```
/home/edouard/anaconda3/lib/python3.6/site-packages/sklearn/linear_model/logistic.py:433:
FutureWarning: Default solver will be changed to 'lbfgs' in 0.22. Specify a solver to silence this warning.
FutureWarning)
```

## 13.7 Lasso logistic regression (L1-regularization)

The objective function to be minimized is now the combination of the logistic loss $\log L(w)$ with a penalty of the L1 norm of the weights vector. In the two-class case, using the 0/1 coding we obtain:

$$\min \mathcal{L}_{\text{Lasso}}(w) = \log L(w) + \lambda \|w\|_1$$

$$= \sum_{i} \{ y_i \, w \cdot x_i - \log(1 + \exp(w \cdot x_i)) \} + \lambda \|w\|_1$$

```python
from sklearn import linear_model
lr11 = linear_model.LogisticRegression(penalty='l1')
# This class implements regularized logistic regression. C is the Inverse of regularization strength.
# Large value => no regularization.
lr11.fit(X, y)
y_pred_lr11 = lr11.predict(X)
errors = y_pred_lr11 != y
print("Nb errors=%i, error rate=%.2f" % (errors.sum(), errors.sum() / len(y_pred_lr11)))
print(lr11.coef_)
```

```
Nb errors=27, error rate=0.27

[[-0.1133793  0.68158741 0.         0.         0.19755791 0.36483513]
[0.08057281 0.06205131 0.76016935 0.        -0.10808194 0.        ]
[0.        0.33749287 0.         0.         0.0790326  0.20158542]
[0.48384386 0.        ]]
```

```
FutureWarning: Default solver will be changed to 'lbfgs' in 0.22. Specify a solver to silence this warning.
FutureWarning
```

## 13.8 Ridge linear Support Vector Machine (L2-regularization)

Support Vector Machines seek a separating hyperplane with maximum margin to enforce robustness against noise. Like logistic regression it is a discriminative method that only focuses on predictions.

Here we present the non-separable case of Maximum Margin Classifiers with ±1 coding (i.e., $y_i \in \{-1, +1\}$). In the next figure the legend applies to samples of “dot” class.

Linear SVM for classification (also called SVM-C or SVC) minimizes:

$$\min \text{Linear SVM}(w) = \text{penalty}(w) + C \, \text{Hinge loss}(w) = \|w\|_2 + C \sum_{i=1}^N \xi_i \quad \text{with} \quad \forall i, \; y_i (w \cdot x_i) \ge 1 - \xi_i$$

Here we introduced the slack variables: $\xi_i$, with $\xi_i = 0$ for points that are on or inside the correct margin boundary and $\xi_i = |y_i - (w \cdot x_i)|$ for other points. Thus:

- 1. If $y_i (w \cdot x_i) \ge 1$, then the point lies outside the margin but on the correct side of the decision boundary. In this case $\xi_i = 0$. The constraint is thus not active for this point. It does not contribute to the prediction.
