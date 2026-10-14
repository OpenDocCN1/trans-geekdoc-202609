$$\hat{a} = E[a(x)] = \frac{\frac{1}{n}\sum_{i=1}^n \tilde{w}^i a(x_i)}{\frac{1}{n}\sum_{i=1}^n \tilde{w}^i} = \frac{1}{n}\sum_{i=1}^n w_*^i a(x_i),$$
where $w_*^i = \frac{\tilde{w}^i}{\frac{1}{n}\sum_i \tilde{w}^i}$  (2.30)

By the weak law of large numbers (WLLN), assuming independent samples $x_i$, we know that the average of iid samples converges in probability to the true mean.

$$a = E[w_*(X_i) a(X_i)] \to b(\hat{a}) = E[\hat{a}] - a = 0 \tag{2.31}$$

Here, $X_i$ are assumed to be iid random variables distributed according to $q(x)$. As a result, IS is, in theory, an unbiased estimator. The variance of the IS estimator is given by the following.

$$\mathrm{VAR}(\hat{a}) = \frac{\sigma^2}{n} = \frac{1}{n} \frac{\sum_{i=1}^n \left(\tilde{w}^i (a(x_i)-\hat{a})\right)^2}{\left(\sum_{i=1}^n \tilde{w}^i\right)^2} \tag{2.32}$$

To check whether the IS estimate is consistent, we need to show that as we increase the number of samples $n$, the estimate converges to the true value in probability.

$$\lim_{n\to\infty} P\left(|\hat{a}_n - a| > \epsilon\right) = 0 \tag{2.33}$$

Using Chebyshev's inequality, we can bound the deviation as follows.

$$\lim_{n\to\infty} P\left(|\hat{a} - a| > \epsilon\right) \le \frac{\mathrm{VAR}(\hat{a})}{\epsilon^2} = \frac{\sigma^2}{n\epsilon^2} = 0 \tag{2.34}$$

As a result, the IS estimator is consistent; here, we didn't need to use an assumption that samples are independent, but we needed to assume that the variance of importance weights is finite. Thus, we expect the variance around the estimate to shrink as we add more samples. One factor that affects the variance of the estimator is the magnitude of importance weights. Since $w(x_i)=p(x_i)/q(x_i)$, the weights are small if $q(x_i)$ is similar to p(xi) and has heavy tails. This is the desired case that leads to a small variance in our estimate.

We would like to have a way of knowing when the importance weights are problematic (e.g., when only a couple of weights dominate the weighted sum). When samples are correlated, the variance is $\sigma^2 / n_{\text{eff}}$, where $n_{\text{eff}}$ is the effective sample size. To compute an expression for effective sample size, we set the variance of the weighted average equal to the variance of the unweighted average.