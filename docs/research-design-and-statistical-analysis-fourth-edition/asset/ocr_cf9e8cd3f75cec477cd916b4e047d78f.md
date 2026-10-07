Integrated Analysis I 179

```
Console Terminal :
@ R 4.3.1 -~
> YuenTest(data=dat,Y-Method,trim=.2)

Yuen Two Sample t-test
data: Y Method
t = -2.1685, df = 26.856, trim = 0.200, p-value = 0.03915
alternative hypothesis: true difference in trimmed means is not equal to 
95 percent confidence interval:
-3.1142664 -0.0857358
sample estimates:
trimmed mean in group Control      trimmed mean in group Drug
                17.06667                      18.66667
```

**Figure 7.5** Results of trimmed t analysis of memory data.

Frequently, there will be reason to suspect that both the normality and homogeneity of variance assumptions are violated. Yuen (1974) proposed that the means in the numerator of Welch’s t (described in Section 6.6.2) be replaced by trimmed means, and the vari-
ances in statistic, as well as the formula for the degrees of freedom, be replaced by
winsorized variances. This combination of Welch’s t and the trimmed t guards against dis-
tortion of Type 1 error rates due to heterogeneity of variance and increased power
when the distribution of data is long-tailed.

#  7.8 Discussion of the Results

After our original analysis of the data, we estimated that the memory drug has a medium size advantage over a placebo in the population of older adults. However, the difference
was not significant, and confidence intervals on both the raw and standardized effects were
ate. At that point, we could have decided (1) that further development and testing of our
pill is not noteworthy or (2) that there is sufficient indication of to merit
further testing and development. The second choice rests on two assumptions: (1) that an
effect of the size estimated is worth the cost involved in further testing and possible market-
ing; and (2) that the failure to reject the null hypothesis reflects a lack of statistical power
due to the presence of outliers in our small sample.

Further support for the assumption that the pill may provide a memory advantage was
found by reanalyzing the data. The rank-based Mann-Whitney U test found about
2/3 of the samples in the drug condition were higher than in the control condition,
suggestive of a drug memory improvement. The trimmed t reduced the variance caused by the long
tails and,, by the outliers. Although reanalysis used us to reject
t null hypothesis, it is essential that we keep running tests until we obtain the result
we like. Doing so risks inflating the Type 1 error rate and drawing erroneous conclusions.
in our example memory data, we should be cautious about overinterpreting these various
results, and we would feel more confident if we could replicate the result. We should design
a large-scale study if we wish to further investigate the value of the pill. This would mean
deciding on a larger sample size, and possibly additional measures of memory. If we believe
even a medium size effect warrants the pill, and we wanted one-tailed