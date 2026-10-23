where This is an example of sequential Bayesian updating or online Bayesian inference. It will give the same results as batch Bayesian inference, but is often more efficient. We give concrete examples of this applied to logistic regression in Sec. 10.6.5 and linear regression in Sec. 11.6.7.

# 4.7 Parameter uncertainty

In this chapter, we have focused on computing a “best guess” for the parameters $\hat{\theta}$. There are two main ways to represent our uncertainty in this estimate, based on **Bayesian statistics** and **frequentist statistics**. See Chapter 7 and Chapter E for details.

# 4.8 Exercises

# **Exercise 4.1** [MLE for the univariate Gaussian]

Show that the MLE for a univariate Gaussian is given by

$\hat{\mu} = \frac{1}{N} \sum_{n=1}^{N} y_n$ (4.113)

$\hat{\sigma}^2 = \frac{1}{N} \sum_{n=1}^{N} (y_n - \hat{\mu})^2$ (4.114)

# **Exercise 4.2** [MAP estimation for 1D Gaussians]

(Source: Jaakkola.)

Consider samples $x_1, \dots, x_n$ from a Gaussian random variable with known variance $\sigma^2$ and unknown mean $\mu$. We further assume a prior distribution (also Gaussian) over the mean, $\mu \sim \mathcal{N}(m, s^2)$, with fixed mean $m$ and fixed variance $s^2$. Thus the only unknown is $\mu$.

+   a. Calculate the MAP estimate $\hat{\mu}_{MAP}$. You can state the result without proof. Alternatively, with a lot more work, you can compute derivatives of the log posterior, set to zero and solve.
+   b. Show that as the number of samples $n$ increase, the MAP estimate converges to the maximum likelihood estimate.
+   c. Suppose $n$ is small and fixed. What does the MAP estimator converge to if we increase the prior variance $s^2$?
+   d. Suppose $n$ is small and fixed. What does the MAP estimator converge to if we decrease the prior variance $s^2$?