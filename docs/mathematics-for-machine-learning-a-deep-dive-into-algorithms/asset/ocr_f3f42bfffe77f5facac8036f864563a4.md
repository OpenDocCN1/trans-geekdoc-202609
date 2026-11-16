# # 6.1 LOGISTIC REGRESSION

Logistic Regression is a widely used statistical method in machine learning for modeling the relationship between one or more independent variables and a binary outcome. Despite its name, Logistic Regression is used for classification tasks rather than regression. It's a fundamental technique that provides insights into the probability of a certain event occurring and is the foundation for more complex classification algorithms. Let's dive into how Logistic Regression contributes to the machine learning landscape:

**Basic Idea:** Logistic Regression models the probability of a binary outcome (0 or 1) as a function of independent variables. It uses the logistic function (sigmoid function) to map the linear combination of variables to a probability value between 0 and 1.

**Sigmoid Function:** The logistic function is an S-shaped curve that "squashes" the linear combination of variables into the range [0, 1]. It's defined as p(x) = 1 / (1 + e^(-z)), where z is the linear combination of variables.

[121]

**Log Odds:** The log-odds (logit transformation of the probability p(x) is represented as log(p(x) / (1 - p(x))) = z. This log-odds can take any value between negative infinity and positive infinity.

**Parameter Estimation:** Similar to linear regression, Logistic Regression involves estimating coefficients (weights) for the independent variables. These coefficients determine the influence of each variable on the log-odds.

**Maximum Likelihood Estimation:** Coefficients are estimated using Maximum Likelihood Estimation (MLE), which maximizes the likelihood of observing the given binary outcomes under the logistic model.

**Decision Boundary:** The decision boundary is a threshold value that separates the predicted probabilities into two classes. For binary classification, if the predicted probability is above the threshold, the instance is assigned to class 1; otherwise, it's assigned to class 0.

**Training:** Logistic Regression models are trained using optimization techniques like gradient descent to find the optimal coefficient values.

[122]

**Regularization:** L1 (Lasso) and L2 (Ridge) regularization can be applied to Logistic Regression to prevent overfitting and improve generalization.