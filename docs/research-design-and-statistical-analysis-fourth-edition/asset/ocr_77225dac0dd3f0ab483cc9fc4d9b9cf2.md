# Research Design and Statistical Analysis

random effects like the ones we have indicated, (and therefore Y) will tend to normally distributed.

We do not want to give the impression that the normality assumption applies in all circumstances. Although the normal distribution is a reasonable approximation to the distribution of many variables, others are not normally distributed. We cited reviews of data sets in Chapter 2 and presented examples from Seasons data sets that Royer make this point. In later chapters, we will consider the consequences of nonnormality and alternatives to these classical statistical procedures that rest on the assumption of normality. Nevertheless, because of its central role in statistical inference, we will devote the remainder of this chapter to considering the normal distribution. The normal distribution also merits our consideration because it provides a relatively simple context within which to continue our development of inferential procedures such as interval estimation and hypothesis testing.

# 5.4.2 The Normal Distribution's Probability Density Function and z Scores

The normal distribution is characterized by its density function:

```
f(y) = \frac{1}{\sigma/2\pi} e^{-(y-\mu)^2/\sigma^2} (5.7)
```

where $\mu$ and $\sigma$ are the mean and standard deviation of the population and $\pi$ and $e$ are mathematical constants. The random variable $Y$ can take on any value between $-\infty$ and $+\infty$, and the curve is symmetric about its mean, $\mu$.

Infinitely many normal distributions are possible, one for each combination of mean and variance. However, inferences based on normal distributions are made by the fact that all possible normal distributions are related to a single distribution. The standardized normal distribution is obtained by subtracting the mean from each score and dividing the difference by the distribution standard deviation; specifically, it is the distribution of the z score

```
z = (Y - \mu) / \sigma (5.8)
```

As we showed in Chapter 2, the distribution of z scores is zero and its standard deviation is one. This is true of any complete set of z scores. In addition, if the variable $Y$ is normally distributed, the corresponding distribution of z scores also will be normal. In this case, the variable $z$ is often referred to as a standardized normal distribution.

Standardization provides information about the relative position of an individual score. For example, assume a normally distributed population of scores with $\mu=500$ and $\sigma=15$. We can write this assumption like: $Y~N(500, 15)$, where the tilde $(\sim means 'distributed as' and the $N$ indicates a normal distribution with the mean and standard deviation given. A value $Y$ of 525 would correspond to a z score of 1.67; $z=(525-500)/15=1.67$, meaning that a raw score of 525 is 1.67 standard deviation units above the population mean of 500. Turning to Appendix C.2, we find that $F(z)=.925$ when $z$ is 1.67. $F(z)$ is the proportion of standardized scores less than $z$ in a normally distributed population of such scores. In this example, we may conclude that the score of 525 exceeds 95.25% of the