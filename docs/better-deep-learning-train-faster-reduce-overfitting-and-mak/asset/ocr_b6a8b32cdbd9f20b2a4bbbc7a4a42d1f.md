This is an example of overfitting the data, [...]. It is an undesirable situation because the fit obtained will not yield accurate estimates of the response on new observations that were not part of the original training data set.

> — Page 24, *An Introduction to Statistical Learning: with Applications in R*, 2013.

This often occurs if the model has more capacity than is required for the problem, and, in turn, too much flexibility. It can also occur if the model is trained for too long. A plot of learning curves shows overfitting if:

+   - The plot of training loss continues to decrease with experience.
+   - The plot of validation loss decreases to a point and begins increasing again.

The inflection point in validation loss may be the point at which training could be halted as experience after that point shows the dynamics of overfitting. The example plot below demonstrates a case of overfitting.

![](bbox=[0.15, 0.44, 0.8, 0.78])

Figure 3: Example of Train and Validation Learning Curves Showing an Overfit Model.