# 6.2 SOFTMAX REGRESSION

Softmax Regression, also known as Multinomial Logistic Regression or Multiclass Logistic Regression, is an extension of Logistic Regression to handle multiclass classification problems. It generalizes the idea of Logistic Regression to scenarios where there are more than two classes. Softmax Regression models the probabilities of each class and provides a way to assign an instance to one of multiple classes while maintaining the probabilistic interpretation. Let's explore how Softmax Regression contributes to the machine learning landscape:

**Basic Idea:** Softmax Regression models the probabilities of multiple classes as a function of independent variables. It uses the softmax function to convert the raw scores (logits) for each class into normalized probabilities.

**Softmax Function:** The softmax function takes an input vector of scores (logits) for each class and transforms them into a probability distribution over all classes. It's defined as p(y = k|x) = e^(z_k) / Σ(e^(z_i)) for each class k, where z is the vector of logits. [125]

**Parameter Estimation:** Similar to Logistic Regression, Softmax Regression involves estimating coefficients (weights) for the independent variables. Each class has its own set of coefficients.

**Maximum Likelihood Estimation:** Coefficients are estimated using Maximum Likelihood Estimation (MLE), which maximizes the likelihood of observing the given multiclass outcomes under the softmax model.

**Training:** Softmax Regression models are trained using optimization techniques like gradient descent to find the optimal coefficient values.

**Decision Rule:** In Softmax Regression, the class with the highest predicted probability is selected as the predicted class for an instance.

**Multiclass Formulation:** Softmax Regression is formulated to model the joint probability distribution of all classes. It ensures that the predicted probabilities sum to 1 across all classes. [126]

**Cross-Entropy Loss:** The loss function used in Softmax Regression is the cross-entropy loss, which measures the difference between the predicted probabilities and the true class labels.

**Regularization:** Similar to Logistic Regression, Softmax Regression can be regularized using techniques like L1 (Lasso) and L2 (Ridge) regularization.