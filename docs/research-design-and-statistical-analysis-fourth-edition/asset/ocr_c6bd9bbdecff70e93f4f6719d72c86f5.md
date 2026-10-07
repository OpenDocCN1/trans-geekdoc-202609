# 18.12 [Computing correlations in real data] Using the penguins data from the [palmerpen-nguins] package in R,

+   a) Correlate bill length with bill depth.
b) Correlate bill length with bill depth, partialing out body mass.
c) Are there any reasons to be cautious when interpreting these correlations? If yes,
make a plot to evaluate the situation.

# Notes

+   1 Note that there are other ways to test this hypothesis. We could use the Fisher Z transformation along with the normal distribution (the next section), or we work directly with the sampling distribution of r. SPSS uses the t test described in this section to test $H_0$: $ho = 0$.
2 G*Power 3.1 refers to the procedure that uses the t distribution to calculate power for this test as the 't-biserial model'. Note that the procedure has a positive bias except for tests of the point-biserial correlation coefficient for X and Y are both quantitative continuous variables, this power calculation slightly overestimates and underestimates the sample size to achieve a desired level of power. This bias increases with N and is negligible for $N=30$.

+   3 The Fisher Z transformation of $r$ is the inverse of the hyperbolic tangent of $r$ (i.e., $Z = \tanh^{-1}r$). This function is available on most scientific calculators.
4 Strictly speaking, the Z transformation is biased by an amount $r/(2N-1)$ (see Pearson & Hartley, 1954, p. 29). However, this bias will be negligible unless N is small and $r$ is large, and we ignore it here. Note also that the sample correlation $r$ is a biased estimator of $ho$ in normal populations, and the bias can be as much as perhaps .04 under realistic conditions (see Zimmerman, Zumbo, & Williams, 2003).

An approximately unbiased estimator of $\hat{ho} = r / [1 + \frac{1-r^{2}}{2N}]$ but this the estimator is rarely used.

+   5 Because bootstrapping involves random sampling, the boundaries of your bootstrapped samples on the Royer data may differ slightly.