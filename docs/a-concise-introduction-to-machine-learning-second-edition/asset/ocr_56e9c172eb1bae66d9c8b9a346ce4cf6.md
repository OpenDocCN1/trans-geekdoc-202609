Setting to zero, multiplying by $\mu(1-\mu)$ and solving for $\mu$ gives the Maximum-Likelihood Estimate (MLE)

```
$\mu_{ML} = \frac{m}{N}$
```

Returning to flipping the coin, if we happen to get tails $(x_n = 0)$ three times in a row $(m=0)$, then the MLE is $\mu_{ML} = 0$. The interpretation is that in all future flips we would continue to see tails. Equally, if we happen flip heads $(x_n = 1)$ three times in a row $(m=3)$, the MLE is $\mu_{ML} = 1$. Both cases are realistic, but the conclusion is not caused and by a small number of trials. In general, to get a good likelihood estimate for any parameter, many observations are necessary.

However, in real applications this abundance of data might be a luxury. If we describe about $\mu$, mathematically and then use Bayes rules to modify "weak" data is necessary to estimate the parameter $\mu$. It is the probability of success, and therefore $\mu \in [0, 1]$. Thus the beta distribution $Beta(\mu, \beta)$ lends itself to describe $\mu$, where $\alpha$ and $eta$ are known as hyperparameters and to some reasonable initial values. In the distribution, we will see how these parameters get updated with data becoming available.

The joint probability density of $\mu$ and $m$ is the product of the likelihood and the prior

```
$f(\mu, m, \alpha, \beta) = p(D)Beta(\mu, \beta) \n\n = \mu^{m}(1-\mu)^{N-m} \frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)} \mu^{\alpha-1}(1-\mu)^{\beta-1}$
```

The posterior density of $f, \mu, m, \alpha, \beta$, is proportional to the joint distribution following Bayes' rules. The constant factors can be dropped when using the proportionality $\propto$ sign, and

```
$f(\mu, m, \alpha, \beta) \propto \mu^{m+\alpha-1}(1-\mu)^{N-m+\beta-1}$
```

Its has functional form of another, different beta distribution. Inserting appropriate factor to ensure the integral over the distribution is one,

```
$f(\mu, m, \alpha, \beta) = \frac{\Gamma(N+\alpha)}{\Gamma(\alpha+\beta)} \mu^{m+\alpha-1}(1-\mu)^{N-m+\beta}$
```

Observing $m$ successes and $N$ failures changes the shape of the prior distribution to arrive at the posterior distribution. The posterior values are\alpha^{post} = m+\alpha$ and $\beta^{post} = N-m+\beta$. The order of successes and failures is irrelevant.

What is the probability of success after taking the data $D$ into account, $p(x=1|D)$ The data is sufficiently specified by $N$ and $m$. There is no longer