
## 152 Research Design and Statistical Analysis

As described in Section 6.4.5, the t-test in the (stats) package of R calculates Welch's t by default (var.eq= FALSE). For the data summarized in Table 6.1, $t' = 1.63$, with $df = 67.95$ and $p = .108$. Notice that this result, using Welch's $t'$, is almost identical to the results of the Student's t test described in Section 6.4.4. This is because the group sizes are equal and the deviations are similar.

Many statistical packages, including SPSS, compute values of $t'$ and $t$ when independent-groups t is performed. SPSS also reports a test of homogeneity of variance, Levene's (1960) test. In Levene's test, an average absolute deviation of scores about group mean is calculated and the ratio of these two averages is assessed using an F distribution. We will describe the family of F distributions in Chapter 8. The Brown-Forsythe (1974a) test is similar, except the groups are replaced by their means; some statistical packages call both tests “Levene's tests.”

It may appear to test the homogeneity of variance assumption before choosing a t. However, there are two important reasons to proceed to Welch's $t'$. First, Levene's test has low power (Zimmerman, 2004; Nordstcke & Zumbo, 2006; Delacre, Lakens, & Leys, 2017), and Table 6.3 demonstrates that the Student's t is not robust when the groups have unequal variance. Selecting the t test based on variance does not fully correct for the Type 1 error rate. Skipping the test for homogeneity of variance and proceeding directly to Welch's results in a more robust test with power that is as highly as Student's t. Thus, we advocate using Welch's t for all independent samples t tests.

## 6.7 Measuring the Standardized Effect: Cohen's d

In the experiment on the effects of diet on cholesterol level, the difference between the two groups provides a measure of the size of the effect. However, the measure is on the original data scale. Although this has the advantage of being meaningful to the researcher, it has accompanying disadvantages: It is difficult to evaluate the importance of differences between means, or to compare such differences with effects of the same independent variable in other groups or laboratories, or combine results of several experiments.

The p-value associated with a hypothesis test is sometimes incorrectly interpreted as a measure of the importance of an effect. A p-value simply indicates the probability that data as extreme as observed in our study, or more, would be sampled from the population if the null hypothesis is correct. Very small, perhaps unimportant in any practical or theoretical sense, may be statistically significant because the sample sizes are large. Conversely, what to effects may occur just by chance in small samples, even if the null hypothesis is true. Finally, important effects, even large differences, may not be statistically significant because the sample was too small, or variability too great, for the test to have much power.

In view of these concerns, expressions of effect size have been proposed (e.g., Cohen, 1988; Kraemer, 2005; McGraw & Wang, 1992; Rosenthal & Rubin, 1994, Shieh, 2013), and this remains an active area of research. In all cases, the estimated effect size (ES) is the difference between the sample means measured in standardized units: $ES = \bar{Y}_1-\bar{Y}_2$.

Different assumptions about the most appropriate standardizer lead to variations in the effect size measure. Unfortunately, the same effect measure has sometimes been given different names, different measures have been labeled identically. In all cases, our guiding principles for choosing an effect size measure should be appropriate for the design (independent or correlated samples) and the equality, inequality, of the population variances. As was true of the criteria for other estimators of population statistics, we also use unbiased and consistent estimators of the population effect sizes (see Section 5.2). To this, we add one additional point: the standardizer should be the best available estimator of the population parameter of interest (Cumming, 2013).

In this section, we focus on variants of Cohen’s d, which would evaluate the effect of a treatment relative to its standard deviation. Estimates of d have several:

- 1. They provide indices of the importance of the effect, measured in standardized units.
- 2. As we see in Section 6.8, they provide information for power calculations.
- 3. They are used in meta-analyses, analyses which combine results from several studies.

There is strong agreement that measures of effect size are important and should be reported along with the results of statistical tests. Most journals explicitly require that measures of effect size be reported, and the seventh edition of the Publication Manual of the American Psychological Association (2020) recommends their inclusion to aid readers' understanding of the importance of the effect. Moreover, because effect sizes are themselves point estimates of the population value, the Task Force for Statistical Inference (Wilson & the Task Force on Statistical Inference, 1999) recommends reporting a confidence interval for every effect size. As we see, the confidence intervals for these effect sizes are calculated from a noncentral t distribution, which is also important for power calculations.

### 6.7.1 Estimating Cohen’s d²

Cohen’s d for the independent-groups design is defined as

$$d = |(\mu_1 - \mu_2)| / \sigma$$

where $\mu_1$ and $\mu_2$ are the population means, and $\sigma$ is the pooled standard deviation. For the independent-groups design, Cohen's d is often calculated as $d = (\bar{Y}_1 - \bar{Y}_2) / s_{pool}$, where $s_{pool}$ is the estimated standard deviation of the population.

In the correlated-samples design, Cohen's d is often expressed as $d_c = d_{mean} / s_{diff}$, where $s_{diff}$ is the standard deviation of the difference scores. This measure is related to the independent-groups d by $d_c = d / \sqrt{1-r^2}$, where $r$ is the correlation between the two measures.

When the variances of the two groups differ, the choice of standardizer depends on whether the variances are equal. If we assume homogeneity, we use the pooled standard deviation. If not, we use the standard deviation of each group separately. This approach is similar to the Welch's t-test.
