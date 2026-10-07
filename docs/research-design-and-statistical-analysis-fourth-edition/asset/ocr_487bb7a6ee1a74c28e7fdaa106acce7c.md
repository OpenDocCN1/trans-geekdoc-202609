# The t Distribution and Its Applications 147

the mu option. For example, t.test(dat$Before, dat$After, paired = TRUE, mu = 6) reports
t t from Equation 6.15 assuming mu_{hyp} is 6.

# 6.6 Assumptions Underlying the Application of the t Distribution

Inferences based on data from the independent-groups design rest on the
assumptions:

+   1. The scores in each treatment population are independently distributed.
2. The scores in each treatment population are normally distributed.
3. The variances of the two populations of scores are the same; this is the homogeneity of
variance assumption.

The independence assumption is usually valid except in situations in which there is some
interaction among participants; this might happen when one participant responds in the
presence of another. For example, suppose the scores weights, greater than total cholesterol, and there were weekly weights observed by all participants. The success or
ailure of some individuals might encourage or discourage others adhering to a diet.
In some cases, the scores would not be independent.

Although the independence assumption is usually not a concern in these designs,
normality assumption and the homogeneity of variance assumption are often violated, and
y violations have implications for Type 1 and Type 2 error rates. In the next sections, we
discuss these consequences and suggest some possible remedies.

# 6.6.1 The Normality Assumption

Consequences of Violating the Normality Assumption

When data are not normally distributed, particularly if the distributions are skewed, the
Type 1 error rate may be distorted. For example, when the nominal Type 1 error rate is
.05, the true probability might be .08 or .02, depending on the direction of skew. Although
our data are frequently skewed, the distortion of Type 1 errors is usually slightly with
lately large "large" may be as small as 20 if n1 = n2 and if the two populations symmetric
distributions. More conservatively, in cases of extreme skew, n of 40 or more in both
correlated-errors and independent-group design will suffice to provide valid Type 1
error. Large data sets not yield increased power and narrower confidence intervals,
they also need to provide greater inoculation against Type 1 error distortions from
violations of the normality assumption.

Although the Type 1 error rate may exceed its nominal value, another important
consideration is that there may be a loss of power when populations are skewed or have
outliers. In some cases, the sampling distribution of Y1 - Y2 will tend to be long-tailed
(i.e., a greater proportion of extreme scores); therefore, estimates of the difference between population means will be less
precise, and variability may be greater than the normality assumption holds. We
next consider possible ways of addressing the potential loss of power due to departures
from normality.