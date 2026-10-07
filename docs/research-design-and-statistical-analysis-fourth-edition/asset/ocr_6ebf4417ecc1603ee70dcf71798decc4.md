The interaction is not significant. However, if we compare the simple effects of $B$ at $A_1$ we have

```
$t_{B/A_1} = (15-5)/(10\sqrt{2}/9) = 2.12$
```

which is significant at the .021 level. The test at $A_2$ does not yield a significant result ($t=0.42$). Even controlling the FWE at .025 for each test contrasting simple effects, we conclude that there is a difference between the $B$ means at $A_1$. We now have an apparent contradiction: the test of the interaction does not provide evidence of an interaction in the population. However, the significant result of the test at $A_1$, coupled with a non- result of the test at $A_2$, suggests that there is an interaction with $B$ effects at $A_1$, but not at $A_2$. The reason for this inequality is that the standard error of the interaction involves the variance of differences among four means, whereas the standard error for the simple effect involves the variance of only two means. Therefore, it is possible to have a pattern of results for simple effects that is not consistent with the result of the test of interaction because the power of the test of the sample is greater than the power of the test of the interaction.

# 10.10.4 Testing Hypotheses About Interaction

Various proposals have been made about the proper follow-up analyses to perform to understand a significant interaction (Gams, 1973; Marascolo & Levin, 1972, 1973; Tukey, 1991). Remember that an interaction occurs when the simple effect of one variable differs across levels of another. So, a $2\times2$ interaction compares one simple effect across another. Thus, the most direct approach to understanding an interaction effect is to test the embedded $2\times2$ interactions. By bypassing all the $2\times2$ interactions, we can identify the simple effects that differ from one another.

For example, in Table 10.5, we test the interaction involving the two age groups and the $B$, and $drugs$, groups. This interaction effect size is $(12+3)-(15+16)=-16$. Dividing this by its standard error, $\sqrt{MS_{error(a,b)}4}$, we have the $t$ statistic or squaring, we have the $F$. If this test has been planned, the alpha-level would be at .05. However, if such analyses are performed, they are typically post hoc. In that case, we have two options for controlling the familywise error. Assuming homogeneous variances, we can use Scheff’s method; we

```
$S = \sqrt{(a-1)(b-1)F_{error(a,b)}/(a-1)(b-1)}}$. In our example, $(a-1)(b-1)=3$ and $ab(n-1)=40$.
```

The F required for significance at the .05 level with 3 and 40 $df$ is 2.84. So $S=2.92$. An alternative is to use the simple $2\times2$ interaction contrasts as a family and use the Bonferroni correction. With the FWE at .05, the alpha-level for each test $t$ is .056, or .0083. Assuming a two-tailed test, the critical value of $t=2.78$, slightly smaller than the critical value of $S$. In this case its advantage will be it slightly more powerful, though as the number of interaction contrasts increases. When variances are homogeneous, as they are here, the choice between methods rests on a comparison of the critical values (see Perlmutter & Myers, 1973). If variances are heterogeneous, the Bonferroni method should be used, with the error term and freedom $df$ based on the contrast tested

# 10.10.5 Cautions When Using Software to Perform Further Analyses

In most software packages, simple effects can be tested by splitting the file. For example, in R we use the *filter* function in the [dplyr] package to pull out the data for