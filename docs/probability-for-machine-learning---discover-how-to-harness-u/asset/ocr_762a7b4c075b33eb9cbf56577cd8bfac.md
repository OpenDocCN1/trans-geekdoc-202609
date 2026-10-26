Finally, we can sum the likelihood function across all examples in the dataset to maximize the likelihood:

max Σ_{i=1}^{n} log(yhat_i) × y_i + log(1 − yhat_i) × (1 − y_i)   (13.27)

It is common practice to minimize a cost function for optimization problems; therefore, we can invert the function so that we minimize the negative log-likelihood:

min Σ_{i=1}^{n} −(log(yhat_i) × y_i + log(1 − yhat_i) × (1 − y_i))   (13.28)

Calculating the negative of the log-likelihood function for the Bernoulli distribution is equivalent to calculating the cross-entropy function for the Bernoulli distribution, where p() represents the probability of class 0 or class 1, and q() represents the estimation of the probability distribution, in this case by our logistic regression model (this is described further in Chapter 23).

cross-entropy = −(log(q(class0)) × p(class0) + log(q(class1)) × p(class1))   (13.29)

Unlike linear regression, there is not an analytical solution to solving this optimization problem. As such, an iterative optimization algorithm must be used.

> Unlike linear regression, we can no longer write down the MLE in closed form.
> Instead, we need to use an optimization algorithm to compute it. For this, we need to derive the gradient and Hessian.
> 
> — Page 246, Machine Learning: A Probabilistic Perspective, 2012.

The function does provide some information to aid in the optimization (specifically a Hessian matrix can be calculated), meaning that efficient search procedures that exploit this information can be used, such as the BFGS algorithm (and variants).

# 13.6 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# 13.6.1 Books

+   • Section 4.4.1 Fitting Logistic Regression Models, The Elements of Statistical Learning, 2016.
+     https://amzn.to/2YVqu8s
+   • Section 4.3.2 Logistic regression, Pattern Recognition and Machine Learning, 2006.
+     https://amzn.to/2JwHE7I
+   • Chapter 8 Logistic regression, Machine Learning: A Probabilistic Perspective, 2012.
+     https://amzn.to/2xKSTCP