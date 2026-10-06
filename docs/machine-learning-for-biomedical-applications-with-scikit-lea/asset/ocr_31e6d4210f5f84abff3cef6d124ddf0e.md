Machine Learning for Biomedical Applications

![](bbox=[0.132, 0.085, 0.816, 0.248])

**Figure 4.3** Conditional probabilities and the decision boundary for binary classification with 1D feature space.

the sigmoid of the decision function

$p(y=1|\mathbf{x}) = \sigma(h(\mathbf{x}))
np(y=0|\mathbf{x}) = 1 - \sigma(h(\mathbf{x}))$

These conditional probabilities are illustrated together with the decision boundary for a 1D feature vector in Fig. 4.3. Logistic regression finds parameters ww of the decision function by minimising the **cross-entropy** over the training labels $y_i$ and probabilities $p_i = \sigma(h(\mathbf{x}))$ for class 1 to ensure that they are as similar as possible:

$$\hat{\mathbf{w}} = \arg\min_{\mathbf{w}} \sum_{i=1}^N [y_i \ln(p_i) + (1 - y_i) \ln(1 - p_i)]$

To understand why the cross-entropy loss works, consider a simple sample with a training label $y_i$. If $y_i=1$, the penalty introduced by cross-entropy loss for this sample will be $-\ln(p_i)$. This penalty is zero for $p_i=1$ and tends to infinity as $p_i$ approaches zero. By minimizing this penalty, we will ensure that the predicted probability of label 1 for this sample is high, as prescribed by the training label. On the other hand, if the training label is the penalty $-\ln(1-p_i)$ will be zero if $p_i$ of class 1 is also zero and tends to infinity if it is close to 1.

Cross-entropy is differentiable and can be minimized using numerical methods such as the gradient descent. Unlike for a perceptron, the convergence of the logistic regression is guaranteed.

In scikit-learn logistic regression is formulated and fitted as follows:

```
from sklearn.linear_model import LogisticRegression
model = LogisticRegression()
model.fit(X_train, y_train)
```