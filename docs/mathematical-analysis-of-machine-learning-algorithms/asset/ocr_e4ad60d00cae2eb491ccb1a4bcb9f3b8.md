![](bbox=[0.28, 0.09, 0.78, 0.28])

Figure 1.1 Training and test errors versus model complexity

+   - Performance of prediction function on the test data should match that on the training data. The difference is smaller for a less expressive model with a smaller parameter space Ω.

The gap between training error and test error depends on model complexity, which characterizes how large the model parameter space Ω is. When Ω is too large, the training error becomes smaller, but the difference between training error and test error increases. Therefore, in practice, there is a trade-off in machine learning, and the best prediction performance is achieved with the right balance, often via a tuning parameter in the learning algorithm that characterizes model complexity. The phenomenon is described in Figure 1.1. Such a tuning process is often referred to as hyperparameter optimization.

When the class of prediction functions is too large (or complex), then the difference between training error and test error increases. This leads to the so-called overfitting phenomenon. A simple example of overfitting can be described as follows. Let X be a one-dimensional feature uniformly distributed in [−1, 1], with class label Y = 1 when X ≥ 0 and Y = −1 when X < 0. The optimal classifier can achieve a test error of 0.

Given training data (X_i, Y_i) (i = 1, …, n), and assuming X_i are all different, if we consider a prediction function class that contains all possible functions, then the empirical risk minimization method with the following solution can fit the data perfectly:

f̂(X) = { Y_i   if X = X_i for some i, 1   otherwise. }

This model class has high model complexity measured by its covering number, which we will study in the book. However, the resulting ERM prediction rule does not make any meaningful prediction when X is not in the training data. This is because, although the training error of 0 is small, it is significantly different from the test error of 0.5.