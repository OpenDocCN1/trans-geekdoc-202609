# EQUATION 6.1

$$p(k|x)=\frac{p(x|k)\times p(k)}{p(x)}$$

where:

+   - $p(k|x)$ is the probability of having the disease (k) given a positive test result (x). This is called the *posterior probability*.
+   - $p(x|k)$ is the probability of getting a positive test result if you *do* have the disease. This is called the *likelihood*.
+   - $p(k)$ is the probability of having the disease irrespective of any test. This is the proportion of people in the population with the disease and is called the *prior probability*.
+   - $p(x)$ is the probability of getting a positive test result and includes the true positives and false positives. This is called the *evidence*.

We can rewrite the above in plain English:

# EQUATION 6.2

$$\text{posterior}=\frac{\text{likelihood}\times\text{prior}}{\text{evidence}}$$

So our likelihood (the probability of getting a positive test result if we do have unicorn disease) is 90%, or 0.9 expressed as a decimal. Our prior probability (the proportion of people with unicorn disease) is 0.2%, or 0.002 as a decimal. Finally, our evidence (the probability of getting a positive test result) is 5%, or 0.05 as a decimal. You can see all these values illustrated in figure 6.1. Now we simply substitute in these values into Bayes' rule:

# EQUATION 6.3

$$\text{posterior}=\frac{0.9\times0.002}{0.05}=0.036$$

Phew! After taking into account the prevalence of the disease and the proportion of tests that are