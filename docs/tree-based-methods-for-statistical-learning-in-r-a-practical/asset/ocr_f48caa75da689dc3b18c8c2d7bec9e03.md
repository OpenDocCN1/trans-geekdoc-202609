used in CTree will only have high power for certain directions of deviation from independence and depends on the choice of g() and h(). A useful guide for selecting g() and h() can be found in Table 4 of coin’s “Implementing a Class of Permutation Tests: the coin Package” vignette; to view, use vignette("Implementation", package = "coin") at the R console.

In the presence of outliers, the general test of independence discussed in Section 3.3 would be more powerful at a given sample size and α if g() and h() converted X and Y to ranks (because ranks are more robust to outlying observations).

To illustrate, let’s run a quick Monte Carlo experiment. Suppose X = X has a standard normal distribution and that Y = Y is equal to X with a tad bit of noise: Y = X + ε, where ε ~ N(0, σ = 0.1). Figure 3.3 shows a scatterplot for two random samples of size N = 100 generated from X and Y. The left panel in Figure 3.3 shows a clear association between X and Y. The right panel shows a scatterplot of the same sample, but with three of the observations replaced by outliers. Even with the outliers, there is still a clear relationship between X and Y.

![](bbox=[0.15, 0.44, 0.85, 0.72])

FIGURE 3.3: Scatterplots of two linearly related variables. Left: original sample. Right: original sample with three observations replaced by outliers.

The code chunk below applies the gi.test() function, using both the identity and rank transformations, to 100 random samples from X and Y for sample sizes ranging from 10–100; note that each sample includes three outlying Y values. For each sample size, the approximate power of each test is computed as the proportion of times out of 100 that the null hypothesis was rejected