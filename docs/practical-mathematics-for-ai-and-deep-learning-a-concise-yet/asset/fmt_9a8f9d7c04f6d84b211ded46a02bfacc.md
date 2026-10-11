
A critical value of the statistic `Z` at significance level `α` is defined as `Z_{α/2}` for two-tailed test. Here, `P(Z > Z_{α/2}) = α/2`, implies `P(Z < -Z_{α/2}) = α/2`. This is depicted in the shaded regions in [Figure 5.2](#c05.xhtml#fig5_2). So, we have `P(Z > Z_{α/2}) = α/2`. By symmetry, `P(Z < -Z_{α/2}) = α/2`. For testing alternate hypothesis with one tail, we will have only one shaded region, either left or right, based on the type of test, as shown in [Figure 5.2](#c05.xhtml#fig5_2); the shaded region is called *critical region or rejection region*:

![Figure 5.2: Critical region for hypothesis testing](images/one-two-tailed_critical.jpg)

**Figure 5.2:** *Critical region for hypothesis testing*

### 6. Conclusion

The computed value of `Z` is compared with the significance value `Z_{α/2}` at a given level of significance `α`. If the value of `Z` falls in the defined critical region, the null hypothesis is *rejected* with confidence `1 - α`. Choosing `α = 0.01`, we can say that the null hypothesis (that is, the claim of expert committee here) is false and can be rejected with 99% confidence.

Now, let’s look at a few examples on hypothesis testing where we follow the mentioned steps to validate the statistical hypothesis.

**Example**: Testing whether a die is fair or unbiased (that is, all six face values are equally likely to occur). A die is thrown 9000 times, and the number of times values 5 or 6 is observed is 3600. Is the die unbiased?

For an unbiased die, the probability of each face is `1/6`. We can take the event of getting 5 or 6 as success and denote it by `S`. We have `P(S) = 1/3`. Getting any value other than 5 or 6 is considered a failure. So, we have a binomial distributed variable with `n = 9000` trials, the probability of success `p = 1/3`, and the number of successes observed is 3600. Here, the null hypothesis is `H_0: p = 1/3`, that is `p = 0.333...`, and the alternate hypothesis is `H_1: p ≠ 1/3`. Let random variable `X` denote the count of success. For binomial distribution, we have mean as `np` and variance as `npq`:

Hence, `μ = 3000` and `σ² = 2000` for large `n`

Therefore, `Z = (3600 - 3000) / √2000 ≈ 13.42`

Since `Z > Z_{0.005} ≈ 2.576`, choosing the significance level `α = 0.01`, and we know this by the empirical rule for normal distribution. Hence, `Z` falls inside the critical region or rejection region. So, we can reject the null hypothesis with confidence of 99%. Hence, the die is not a fair die.

# Statistical Inference

Let us consider a random variable `X` with probability density `f(x; θ)`. Here, `θ` represents the set of parameters of the distribution or more formally, `θ` represents a parameter vector. For example, in case of normal distribution, `θ = (μ, σ²)`. The set of all possible values of the parameters is called the *parameter space*. Thus, the parameter space defines a family of probability distributions:

`{ f(x; θ) : θ ∈ Θ }`

Now, let’s consider a random sample `X_1, X_2, ..., X_n` of size `n` from a population, with probability density function `f(x; θ)`. Can we estimate the parameter vector `θ` as a function of sample values, that is, can we define a statistic `t` that can approximate a population parameter? Let vector `X = (X_1, X_2, ..., X_n)`, then we want to find sample statistic:

`θ̂ = t(X)`

such that the distribution of `θ̂` is concentrated around the true value of the population parameter `θ`. Here, `t(·)` depicts the estimator function for statistic `θ̂`. In this case, the statistic `θ̂` is called an *estimator of the population parameter* `θ`.

## Estimator Properties

Let’s now discuss what properties of a statistic makes it a good estimator:

*   **Unbiasedness**: An estimator `θ̂` is called an *unbiased* estimator of the population parameter `θ` if `E(θ̂) = θ`. Suppose, for an unknown population with probability distribution `f(x)`, we are given the expectations: `E(X) = μ` and `Var(X) = σ²`. The sample points `X_i` can be viewed as a set of `n` **independent and identically distributed** (**i.i.d.**) random variables `X_1, X_2, ..., X_n`, assuming values `x_1, x_2, ..., x_n` and each `X_i`. Then, each `X_i` has mean `μ` and `Var(X_i) = σ²`. For the statistic sample mean `X̄`, we have `E(X̄) = μ`.

    Hence, the sample mean is an *unbiased* estimate of the population mean. The sample expectation of variance is as follows:

    `E(S²) = (n-1)/n σ²`

    Reference to the proof is given in the *Further reading section [3]*. Hence, *sample variance is not an unbiased estimate of population variance*.

*   **Consistency**: For any estimator `θ̂_n`, we can define a sequence of variables as follows: `θ̂_1, θ̂_2, ..., θ̂_n`. Here, `θ̂_n` is dependent on the number `n` of sample values taken. We call estimator `θ̂` a consistent estimator of parameter value `θ` if this sequence of values `θ̂_n` converge in probability to the true parameter value. We denote this as `θ̂_n → θ`, where the operator `→` indicates convergence in probability, that is, for any arbitrarily small `ε`:

    `lim_{n→∞} P(|θ̂_n - θ| > ε) = 0`

    Clearly, the sample mean is a *consistent* estimator of the population mean.

*   **Efficiency**: There may exist multiple unbiased and consistent estimators for a population parameter. So, there is a need for some further criterion to choose the best estimator. The one with lower variance is called an *efficient* estimator because it will tend to have values that are concentrated more closely around the correct value of the parameter, and hence, our estimate will be closer to the actual value. For normal distribution, because of the symmetry of the bell curve, the sample median is also an unbiased estimate of the population mean `μ`. Now, which one should you choose as a better estimator? Here, we can compare the variance or square of standard error of both the estimators. Now, `Var(X̄) = σ²/n` and it can be proved that for sample median `Md`, `Var(Md) ≈ πσ²/(2n)`. Hence, the sample mean is a more efficient estimator of `μ`.

*   **Sufficiency**: An estimator is called sufficient if it contains all information in the sample regarding the population parameter being estimated. This property of an estimator is out of scope of further discussion in this book.

## Minimum Variance Unbiased (M.V.U) Estimators

If a statistic `T` is unbiased estimator of a population parameter `θ` and `T` has the smallest variance among the class of all unbiased estimates, then `T` is called the minimum variance unbiased estimator of `θ`. Formally:

*   `E(T) = θ`
*   `Var(T) ≤ Var(T')` for all unbiased estimators `T'`

The MVU is unique. To check whether an unbiased estimator is MVU, **Cramer-Rao inequality** is used. This inequality provides a lower bound for the variance of an unbiased estimator of a parameter. The quantity `E(θ̂) - θ` is called the *bias* of the estimator in general. For unbiased estimator, bias is zero.

## Likelihood Function
