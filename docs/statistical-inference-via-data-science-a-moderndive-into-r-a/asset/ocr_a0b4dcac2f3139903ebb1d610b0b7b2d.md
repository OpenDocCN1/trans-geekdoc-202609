# 8 Estimation, Confidence Intervals, and Bootstrapping

jackknife but quickly gained recognition for its broader applicability and efficiency. Since then, it has been shown in multiple contexts that the bootstrap performs at least as well as traditional methods in estimating standard errors, constructing confidence intervals, performing hypothesis testing, and many other statistical techniques.

Furthermore, the 1980s (but even more in the last two decades), the use of simulations to compare advanced bootstrap methods against other techniques, such as cross-validation, further established its superiority in specific contexts, particularly when dealing with small sample sizes. The use of the bootstrap and bootstrap-related methods has become a cornerstone in modern statistical and science practices.

In this section, we introduce additional details about the bootstrap, and explain the advantages and limitations of using bootstrap.

# 8.3.2 Confidence intervals and rate of convergence

We want to compare how the bootstrap performs when building confidence intervals with respect to the theory-based approach discussed in Section 8.1. The formal comparison requires mathematical concepts beyond the scope of this book, and it is not pursued. Instead, we provide just enough elements to help you with the intuition of how this comparison is made and why bootstrap-related methods can be as strong as or even stronger than theory-based or alternative methods.

Let's start with an illustration using the theory-based confidence interval. A 95% confidence interval for $\mu$, when a sample size of $n = 100$ is used, is given by

> $$\mu \pm 1.96\frac{\sigma}{\sqrt{n}}$

when $\sigma$ is unknown or

> $$\mu \pm 1.98\frac{s}{\sqrt{n}}$

when $\sigma$ is unknown. We use 95% and $n = 100$ for this illustration, but the exposition is also true with any other confidence level or other sample sizes. We understand that 95% of all the possible samples would lead to an interval that contains $\mu$. This statement is exactly true if the distribution of $\bar{X}$ is precisely normal, and we say that 95% is the true coverage probability. In reality, we do not know what the distribution of the population is, but because of the Central Limit Theorem we know that for a large sample size $n$ the distribution of $\bar{X}$ is approximately normal. In this case, the 95% is an approximate coverage probability. This means that if we were to take every possible sample of size $n$ and construct a confidence interval using the formulas above, nearly 95% of the intervals will include $\mu$. Again, this happens because $X$ is not exactly, but approximately, normal. Still, the Central Limit Theorem states that when $n$ tends to infinity, the distribution of $X$ tends to normal, so the larger the