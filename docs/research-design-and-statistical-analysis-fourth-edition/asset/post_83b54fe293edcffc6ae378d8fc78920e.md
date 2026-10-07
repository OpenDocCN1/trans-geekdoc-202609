
## Contrasting Means in Between-Subjects Designs 267

| Table 10.1 Computing Contrasts in R |
- 1. Begin with the data in a data frame. Here, we'll call it dat.
- 2. Create a vector of weights for each contrast of interest. For example, psi1 <- c(1, -1/3, -1/3, -1/3) compares the first group against the average of the other three. When there are $a$ levels of factor, $a-1$ contrasts may be tested. For example, if $a = 4$, three independent contrasts are possible.
- 3. Combine the contrast vectors into a matrix by rows, adding a row in where every weight is $1/a$: temp.mat<- rbind(constant=1/a, psi1, psi2, psi3). The constant represents the equally weighted mean of the dependent variable (dv).
- 4. Invert the temporary matrix using the solve function and assign it a new name: mat<- solve(temp.mat).
- 5. Delete the first column of the matrix: mat[,-1]
- 6. Run the analysis using the lm or ov function, saving the results: model<- lm(data = dat, ~ iv, contrasts = list(mat)). This command applies the contrasts to the matrix named in iv.
- 7. Review the results using the summary function: summary(model.out). The output will be a table of estimated contrast values, ("estimate"), their standard errors, and corresponding, df, t, and p-values. The Intercept will equal the grand mean.

sample reflect populations that are different in size, the weights on the means in the contrast must take into account the variation in population size.

Equal populations. Suppose we wish to compare the speeds of solving arithmetic problems in four different grades (e.g., Royer et al., 1999; see the Royer_speed data file on the book's website). Table 10.2 represents mean variances and class sizes (n). Although there are different numbers of students in the different grades, this is likely due to chance; there is no reason to view the sampled populations as unequal. Because it is safe to assume the populations are equal in size, any means that are averaged should receive equal weight in a contrast. For, when testing the speed of fifth-graders against the combined average of the sixth, seventh-, and eighth-grades, the weights would be -1, 1/3, 1/3, 1/3 or equivalently, -3, 1, 1, and 1. Equal weighting of means that are averaged on one side of a contrast usually will be appropriate in the analysis of data from any experiment where the independent variable is manipulated. Using integer weights, we use Equation 10.5 to calculate the statistic for the contrast of fifth-graders' mean speed against the combined mean of the sixth, seventh-, and eighth-grades. Using integer weights, you should verify that t=psi/.680/130=5.233. Because the estimate of variability in the calculation of the standard error is MS_error df associated with the test is (90–4) or 86. Again, we defer selection of a critical value of t until our discussion of the FWE. Of course, we could also construct a confidence interval on the contrast. If we used the integer weights and resulting values of .680 for the contrast and .130 for the standard error, the upper and lower boundary values would be divided by 3 to return the interval to our original scale. Using fractional weights in R, the resulting estimate of $\varphi$ is $0.227$ and $SE$ is $.043$ (see Box 10.1).

**Unequal populations.** In contrast to experimental designs, many observational studies, differences in group sizes reflect differences in population sizes. A case in point is the *Seasons* study, which we cited previously. In Chapter 8, we test the omnibus hypothesis that mean depression scores were equal for four populations defined by their education level. The four groups were males with only a high school education (HS), some experience (C), a bachelor’s degree (B), or graduate school (GS). Panel $a$ of Table 10.3 presents group sizes, means, and variances.

Assume that one question was whether the mean depression scores differed between males with high school education and all others. Because group size suggest that the $HS$ population is considerably smaller than the others, we assume that the four populations vary in size. In the case of the last three populations, which we will denote as $\mu_{HS}$ (“greater than high school”), we would be a weighted average; that is,

$$
$$\mu_{>HS} = \frac{w_C\mu_C + w_B\mu_B + w_{GS}\mu_{GS}}{w_C + w_B + w_{GS}}
$$

and we null the hypothesis of interest

$$
$H_0 : \mu_{>HS} = \frac{w_C\mu_C + w_B\mu_B + w_{GS}\mu_{GS}}{w_C + w_B + w_{GS}} = 0$
```

Because the test is not affected when all weights are multiplied by a constant, we can simplify things by multiplying the expression by $w_C + w_B + w_{GS}$, yielding the contrast

$$
$$\{\psi\} = (w_C + w_B + w_{GS})\mu_{HS} - (w_C\mu_C + w_B\mu_B + w_{GS}\mu_{GS}) \quad (10.7)
$$

and we can test the null that this contrast equals zero.

Unless we know the actual sizes of the populations, we now need values of the $ws$. In many situations, the simplest and most reasonable will be the group sizes. Panel $c$ of Table 10.3 presents output for Contrasts 1 and 2; the weights for the two contrasts are presented in Panel $b$. The weights for Contrast 1 would be appropriate if we assumed that the populations are of equal size; that is not the case in this example, but Contrast 1 provides a comparison with Contrast 2, which uses weights based on the assumption that the group

## Research Design and Statistical Analysis

### Table 10.2 Summary information for the Royer response time data

| Grade | 5 | 6 | 7 | 8 |
|---|---|---|---|---|
| Mean | 0.350 | 0.560 | 0.586 | 0.583 |
| Variance | 0.033 | 0.028 | 0.031 | 0.038 |
| n | 23 | 26 | 21 | 20 | N = 90 |

### Table 10.3 Summary statistics (a), contrast coefficients (b), and test results (c), (d) for depression scores as a function of educational level

(a) Statistics

| Educational level | n | Mean | Variance |
| --- | --- | --- | --- |
| HS | 19 | 6.903 | 34.541 |
| C | 33 | 3.674 | 5.97 |
| B | 37 | 3.331 | 9.861 |
| GS | 39 | 4.847 | 26.218 |

(b) Contrast coefficients

| Educational level | HS | C | B | GS |
| --- | --- | --- | --- | --- |
| Equal weights | 1 | -1/3 | -1/3 | -1/3 |
| Sample-size weights | 109 | -33 | -37 | -39 |

(c) Contrast test results

| Contrast | Value of contrast | Std. error | t | df | Sig. (tailed) |
| --- | --- | --- | --- | --- | --- |
| Equal weights | 2.952 | 1.038 | 2.842 | 124 | 0.005 |
| Sample-size weights | 3.1892 | 1.204 | 2.817 | 124 | 0.006 |

(d) Welch's test results

| Contrast | Value of contrast | Std. error | t | df | Sig. (tailed) |
| --- | --- | --- | --- | --- | --- |
| Equal weights | 2.952 | 1.394 | 2.118 | 124 | 0.047 |
| Sample-size weights | 3.1892 | 1.52 | 2.09 | 124 | 0.049 |

## 10.3. Testing Contrasts When Variances Are Not

To this point, we have assumed that populations have the same variance and have therefore used MS$_{s/a}$ in computing the standard error. If the assumption of homogeneity of variance is incorrect, doing so may bias the test. There are two situations in which MS$_{s/a}$ is inappropriate. In one case, relatively small differences in the variances of the contrasted groups can inflate the 1 error. For example, if there are three groups with variances 20, 21, and 5, and the means of the first two groups are to be compared, the variance of 5 should not be included in the denominator because the estimate of standard error will be too small, and the 1 error will be inflated.

The second situation is one in which there is heterogeneity of variance within the set of means that are contrasted. In this case, an extension of Welch's test (t'; Welch, 1947; see Section 6.6.2) should be calculated. Recall that when variances are assumed to be homogeneous, the contrast variances are pooled; however, when variances are assumed to be heterogeneous, the variances are not pooled and should be weighted according to the different weights. Also, the df are adjusted downward unequal variances are assumed. The difference between the standard t results and those for t' are illustrated in Panels c and d of Table 10.3 where two sets of results are presented for each of the two contrasts of the HS mean with the mean of the other three groups. One result is obtained assuming equal variances, and the t is calculated as in Equation 10.5. The second result is obtained when equal variances are not assumed, 

To obtain the result when equal variances are not assumed, calculate

```
t' = \hat{w}/\hat{s}
```

where

```
\hat{s}^2 = \sum_{j=1}^k \frac{w_j^2 s_j^2}{n_j}
```

and the degrees of freedom are

```
df' = \frac{\sum_{j} \frac{w_j^2 s_j^4}{n_j}}{\left(\sum_{j} \frac{w_j^2 s_j^2}{n_j}\right)^2 \sum_{j} \frac{2w_j^2}{n_j(n_j-1)}}
```
