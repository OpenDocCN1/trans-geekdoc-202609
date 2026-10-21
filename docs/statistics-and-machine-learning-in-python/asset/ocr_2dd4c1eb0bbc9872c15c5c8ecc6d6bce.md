$$p(C_k|x) = \frac{p(C_k)p(x|C_k)}{p(x)}$$

Where $p(x)$ is the marginal distribution obtained by suming of classes: As usual, the denominator in Bayes’ theorem can be found in terms of the quantities appearing in the numerator, because

$$p(x) = \sum_{k} p(x|C_k)p(C_k)$$

+   4. Classify $x$ using the Maximum-a-Posteriori probability: $C_k = \arg\max_{C_k} p(C_k|x)$

LDA is a **generative model** since the class-conditional distributions cal be used to generate samples of each classes.

LDA is useful to deal with imbalanced group sizes (eg.: $N_1 \gg N_0$) since priors probabilities can be used to explicitly re-balance the classification by setting $p(C_0) = p(C_1) = 1/2$ or whatever seems relevant.

LDA can be generalised to the multiclass case with $K > 2$.

With $N_1 = N_0$, LDA lead to the same solution than Fisher’s linear discriminant.

# 13.2.1 Exercise

How many parameters are required to estimate to perform a LDA ?

```
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

/home/edouard/anaconda3/lib/python3.6/site-packages/_pytest/fixtures.py:844:
DeprecationWarning: The convert argument is deprecated in favor of converter.
It will be removed after 2019/01.
params = attr.ib(convert=attr.converters.optional(tuple))

```
Nb errors=10, error rate=0.05
```