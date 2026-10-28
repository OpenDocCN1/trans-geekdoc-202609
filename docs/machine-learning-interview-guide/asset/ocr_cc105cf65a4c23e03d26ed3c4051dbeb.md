Here is a brief explanation:

+   • Shallow decision trees: Decision trees with a small number of splits or entries, and not very deep ones, or used interchangeably with decision tree stumped.
+   • Weak learners: These decision trees are a little better than a random guess and yet each of these trees by itself is not a very accurate one.
+   • Limited complexity: AdaBoost regulates the decision trees' size in such a way that each weak learner only makes small enhancements to the final model.
+   • Efficient training: Lower levels of decision trees are easier to learn; hence, it is possible to use them in the training process in AdaBoost.

Therefore, the base learners that are normally incorporated into the AdaBoosted trees for regression are shallow decision trees, preferably involving weak learners with maximum depth. These simple models are easy to train and give a small improvement to the final ensemble of AdaBoost in terms of prediction.

# Question 7: How does AdaBoost handle the issue of overfitting in regression tasks?

Answer: AdaBoost handles the issue of overfitting in regression tasks through the following mechanisms:

+   • Weak learners: AdaBoost uses simple weak learners. These learners are not complex since there is a probability of overemphasizing or overcomplicating the training data.
+   • Iterative training: It updates weak learners in the process of learning step by step and minimizes probability of over-fitting on training data, by paying