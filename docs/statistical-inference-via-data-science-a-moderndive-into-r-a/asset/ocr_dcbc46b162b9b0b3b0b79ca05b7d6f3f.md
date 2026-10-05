# 9.1 Tying confidence intervals to hypothesis testing 305

+   - Remember the equal sign should go under the null hypothesis as this is needed for the method.
- The statement under the null hypothesis is assumed to be true during the process.
- Typically, researchers want to conclude in favor of the alternative hypothesis; that is, try to see if the data provides evidence against the null hypothesis.

+   2. Set a significance level $\alpha$, based on your tolerance for committing a Type I Error, always before working with the sample.
3. Obtain the sample mean, sample standard deviation, $t$-test statistic, and $p$-value.

+   - When working with a two-sided test, as in the almond example above, the $p$-value is the area on both tails.
- For a left-sided test, find the area under the $t$ distribution to the left of the observed $t$ test statistic.
- For a right-sided test, find the area under the $t$ distribution to the right of the observed $t$ test statistic.

+   4. Determine whether the result of the test is statistically significant (if the null is rejected) or non-significant (the null is not rejected).

The simulation-based approach

When using a simulation-based approach such as the bootstrap percentile method, we repeat the first two steps of the theory-based approach:

+   1. State null and alternative hypothesis in terms of $\mu$. The statement under the null hypothesis is assumed to be true during the process.
2. Set a significance level, $\alpha$, based on your tolerance for committing a Type I Error.

In step 1 we need to assume the null hypothesis is true. This presents a technical complication in the bootstrap percentile method as the collected samples are based on the real distribution and if the null hypothesis is not true they cannot reflect it. This solution is to shift the sample values by a constant so as to make the sample mean equal to the claimed population mean under the null hypothesis.

The infer workflow takes this into account automatically, but when introduced to students for the first time, the additional shifting tends to create some confusion in the intuition of the method. We have determined that it is easier to introduce the elements of the simulation-based approach to hypothesis testing via the two-sample problem context using resampling technique called permutation. Details of this method are presented in Sections 9.3, 9.4, and 9.5. Once we are comfortable using this method, we can then explore the bootstrap percentile method