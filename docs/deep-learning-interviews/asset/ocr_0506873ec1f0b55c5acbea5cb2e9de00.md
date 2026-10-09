# **PRB-133** ${}^{\circled { F}}$ **CH.PRB- 5.34.**

*Answer the following questions:*

+   1 . Implement the sigmoid function $\sigma(x) = \frac{1}{1 + e^{-x}}$ symbolically using a Python based SymPy program.

+   2 . Differentiate the sigmoid function using SymPy and compare it with the analytical derivation $\sigma'(x) = \sigma(x)(1 - \sigma(x)).$

+   3 . Using SymPy, evaluate the gradient of the sigmoid function at x = 0.

+   4 . Using SymPy, plot the resulting gradient of the sigmoid function.

5.2.18 The Beta-Binomial model

# **PRB-134** ${}^{\circled { F}}$ **CH.PRB- 5.35.**

*You will most likely not be given such a long programming task during a face-to-face interview. Nevertheless, an extensive home programming assignment is typically given at many of the start-ups I am familiar with. You should allocate around approximately four to six hours to completely answer all questions in this problem.*

*We discussed the Beta-Binomial model extensively in chapter 3. Recall that the Beta-Binomial distribution is frequently used in Bayesian statistics to model the number of successes in n trials. We now employ SymPy to do the same; demonstrate computationally how a prior distribution is updated to develop into a posterior distribution after observing the data via the relationship of the Beta-Binomial distribution.*

*Provided the probability of success, the number of successes after n trials follows a binomial distribution. Note that the beta distribution is a conjugate prior for the parameter of the binomial distribution. In this case, the likelihood function is binomial, and a beta prior distribution yields a beta posterior distribution.*

*Recall that for the Beta-Binomial distribution the following relationships exist:*

|Prior of $\theta$|Beta(a,b)|  
|---|---|  
|Likelihood|binomial $(n,\theta)$|  
|Posterior of $\theta$|Beta $(a + x, b + n - x)$|  
|Posterior Mean|$(a + x)/(a + b + n - x)$|

+   1 . Likelihood: The starting point for our inference problem is the Likelihood, the