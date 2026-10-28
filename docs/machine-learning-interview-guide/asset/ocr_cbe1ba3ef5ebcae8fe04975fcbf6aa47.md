+   - Sensitive to noisy data:
+     - Susceptibility: May contain noise, and hence interferes with the generalization of the outcome.
+   - Black-box nature:
+     - Interpretability challenge: Social relations as well as complex relations learned can oftentimes be more complicated to decipher.
+   - Need for tuning:
+     - Hyperparameter sensitivity: This depend on hyperparameter tuning to make sure it fits well in order to offer the best results.

# Adaptive boosted trees

AdaBoost, or adaptive boosted trees for regression, is a process where more than one weak learner is combined to create a strong learner model that will give a better prediction of the outcome. It operates by placing new trees iteratively into the residuals of previous trees so as to rectify mistakes made in previous models. AdaBoost is overfitting resistant (in reality, if the data is noisy or if a higher number of iterations are used, then the model is prone to overfitting), available for many types of data, and has been shown to give better performance over single regression models. AdaBoost is significant in learning since it demonstrates the technique that can combine relatively complex models to achieve better performance and increase model generality.

Question 1: Can you explain the concept of weak learners in the context of AdaBoosted trees?

Answer: In the context of AdaBoost, a weak learner may be defined as a model that is very basic, but has a tiny edge