# 244 DATA SCIENCE

a given coefficient comes from the distribution with zero mean. In order to evaluate the hypothesis, we may be able to calculate the t-distribution with general degrees of freedom. We overcome this task by sticking to approximation N → ∞, where the t-distribution converges to a normal distribution.

Further, we may need the probability that we may reject the null at general confidence level, but rather to check whether we can reject the null at several benchmark values. In particular, we check to 90%, 95%, 99%, and 99.9%. We will use the “*” notation, where * stands for a situation where we can reject the null at 90% confidence level, but not at a higher confidence level. Analogously, the case of corresponds to 95% confidence level, *** corresponds to 99%, and **** corresponds to 99.9%, respectively, having with every estimated parameter its corresponding number of “*” gives the easiest-read statistical assessment of the estimated model.

We create a function that assigns the corresponding number of “*” for every given t-statistic under the asymptotic approximation:

```
quantQ.ols.signLevels:{[ts]
// ts -- list of t-statistics
convertPDict(({oj};j1;j2;j3;4j});""* (90% c.l.");""** (95% c.l.");""*** (99% c.l.");"""* (99.9% c.l.");"""")
convertPDict each binr([1.282;1.645;2.326;3.091]) abs ts;
```

The confidence level of the estimated parameters uses:

```
signLevels:.quantQ.ols.signLevels[tStats]
signLevels
```

(**** (99.9% c.l.");"**** (99.9% c.l.");""**** (99.9% c.l.");"""* (99.9% c.l.)

The result shows that all four parameters are statistically significant, or we can reject the null hypothesis at a very high confidence level. Given that the assumptions hold, all the estimated parameters contained within the model are true values. Since we know it is by knowing the true model, this result is not surprising. Still, we cannot assess the overall quality of the model used. This will be done in the following sections.

# 13.6 HOW GOOD THE FIT: R²

The question we have to answer is how good is the overall fit. The significance of individual parameters does not imply. The model has four features, all significant. We include three of them into our model, where each of them have coefficients significantly different from zero. This itself does not answer the question whether we have included the features, or in general, how do we know about the model. We can assert that we have acquired some knowledge about our model.