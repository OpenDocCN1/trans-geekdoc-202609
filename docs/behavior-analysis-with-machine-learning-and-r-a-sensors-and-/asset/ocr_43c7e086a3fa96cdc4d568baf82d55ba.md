# CHAPTER 2. PREDICTING BEHAVIOR WITH CLASSIFICATION MODELS

2. $P(H)$ is called the **prior**. This is the probability of a hypothesis happening without having any evidence. In our example, this translates to the probability that an instance belongs to a particular class without looking at its features. In practice, this is estimated from the training set containing 100 instances and from those, 80 are of type 'Walking' and 20 are of type 'Jogging'. Then, the prior for 'Walking' is $P(C = Walking) = 80/100 = 0.8$ and the prior for 'Jogging' is $P(C = Jogging) = 20/100 = 0.2$.

3. $P(E)$ is the probability of the evidence. Since this one doesn't need to compute it. This can be thought of as a normalization factor. When choosing the final class we only need to select the one with the highest score, so there is no need to normalize them into proper properties between 0 and 1.

4. $P(E|H)$ is the **likelihood**. For numerical variables we can estimate this using a Gaussian probability density function. This sounds intimidating! but all we need to do is compute the **mean** and **standard deviation** for each feature-class pair and plug them into the probability density function (pdf). The formula for a Gaussian (also called normal) pdf is:

```
$f(x) = \frac{1}{\sigma\sqrt{2\pi}}e^{-(x-\mu)^2/2\sigma^2}$  (2.12)
```

where $\mu$ is the mean and $\sigma$ is the standard deviation.

Suppose that some feature $f1$ and when the class is 'Walking', its mean is 5 and its standard deviation is 3. That is, we filter the train set and only select those instances with class 'Walking' and compute the mean and standard deviation for feature $f1$. Figure 2.14 shows how its pdf looks like.

If we have a query instance with a feature $f1=1.7$ we can compute its likelihood given the 'Walking' class $P(f1=1.7|C=Walking)$ with equation (2.12) by plugging in $x=1.7$, $\mu=5$ and $\sigma=3$. In $R$, the function `dnorm()` implements the norm.

```
dnorm(x=1.7, mean = 5, sd = 3)
# [1] 0.07261739
```

Figure 2.15 shows the likelihood with a solid circle when $x=1.7$.

If we have one more feature we need to compute the likelihood for each and take our **product**: $P(f1|C=Walking) * P(f2|C=Walking) * \dots * P(fn|C=Walking)$. Each feature and class pair has its own $\mu$ and $\sigma$ parameters. Thus, Naive Bayes requires to learn