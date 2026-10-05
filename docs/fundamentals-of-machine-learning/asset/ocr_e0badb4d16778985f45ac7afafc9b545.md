and talk about the true underlying functions and the estimation of such functions. If we know the pdf that governs the random variable $X$, then Egn 6.9 is the definition of the mean. However, in most applications we do not know the pdf, but we can define an approximation of the mean from measurements. For example, if we measure the frequency $p_i$ of values in certain intervals around values $x_i$, then we can estimate the true mean $\mu$ by

```
$$\hat{\mu} = \sum_{i=1}^{N} x_ip_i. \quad (6.10)$
```

It is a common practice to denote an estimate of a quantity by adding a hat symbol to the quantity’s symbol. Also, note that here we used a discretization to approximate random variables that can be continuous in the most general case.

We could enter again the philosophical debate as we treated the pdf as fundamental and described the arithmetic average like an estimation of the mean. This should be viewed as Bayesian. However, we could also be pragmatic and say that we only have a collection of measurements so the numbers are the "real" thing, and that pdfs are only a mathematical construct. We will continue with a Bayesian description note that this makes no difference in the end when using the formalism in specific applications.

The mean of a distribution is not the only interesting quantity that characterizes a distribution. For example, we might want to ask what the median value is. The median value is the value for the random variable for which it is equally likely to find a value lower or higher than this,

```
int_{-\infty}^{median(x)} p(x)dx = \int_{median(x)}^{\infty} p(x)dx. \quad (6.11)$
```

The median is equal to the mean in cases of symmetric distribution. However, the median can sometimes be more informative than the mean in cases of asymmetric distributions. For example, the average income in a nation can be very high if there is a small percentage of very rich people. However, it is usually telling to know the value for the household income on which half the population has to live. In extension, we could ask about the numbers in the bottom quarter, and the next quarter. Most telling is, of course, to the whole distribution of income. The summary statistics like the mean and the median are only crude approximation of the picture provided by the distribution.

Let’s get back to other measurements to characterize the distribution of a random variable. The spread of the pdf around the mean is also very revealing as it gives us a sense of how distributed the values are. This spread is also characterized by the standard deviation (std), or its variance, $\sigma$, and is defined as

```
$$\sigma^2 = \int_{-\infty}^{\infty} (x - \mu)^2 f(x)dx. \quad (6.12)$
```

This mathematically called a second moment of the distribution whereas the mean is the first moment. These two moments are generally not enough to characterize