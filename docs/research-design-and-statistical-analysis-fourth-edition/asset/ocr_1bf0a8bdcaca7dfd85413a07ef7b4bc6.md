# The t Distribution and Its Applications 159

some consideration, we decide that e = 44 is reasonable; dividing 20 by 44 yields 4 d = .47. (Our original sample size was N = 72, so we do not need to correct d for bias).

Other options exist for setting the effect size. We might use the estimate from our pilot study of .38. However, pilot studies tend to be modest in size, and small samples can dramatically overestimate the true effect size (see Figure 4.2). For this reason, we prefer to think in first terms of the raw effect size that is of interest. Another possibility in our example is based on noting that .47 is close to .5, Cohen's (1988) medium effect size. Therefore, for the purposes of easy communication to a future audience, we set d = .5. Further discussion of the considerations involved in choosing an effect size in an a priori power analysis may be found in Lenth (2001).

What power do we want? Ideally, we want a sample size that will maximum power to detect the effect of interest. Unfortunately, there are practical considerations. The required sample size increases either as the effect size decreases or as the power increases. The N needed, particularly for high power and small effect sizes, is much larger than researchers realize. Suppose we decide on power = .8, a level of that has been frequently suggested as reasonable. In that case, we would need N = 114, with n₁ = n₂ = 57. Increasing the desired power brings a cost; to have .90 power over the alternative, d = .47, we need 79 participants in each group. Our sample size will often be a compromise among considerations of the minimum effect size of interest, the power we would like to have to detect that effect, and the practical limitations of subject availability and the time required for data collection.

# Calculating the Required Sample Size

We noted earlier that power calculations are based on the noncentral t distribution, where location, variance, and shape are defined, in part, by a noncentrality parameter, δ. If our study involves two independent groups, δ is defined as

> $$\delta = \frac{\mu_1 - \mu_2}{\sigma\sqrt{(1/n_1) + (1/n_2)}} (6.19)$

From Equation 6.18, we can express δ as a function of d and the group sizes

> $$\delta = d / \sqrt{(1/n_1) + (1/n_2)} (6.20)$

G*Power takes values of d and the ratio of the ns as input and uses them to calculate δ in doing power calculations. As an example, Figure 6.2 presents our input (in the white boxes) to G*Power and the resulting output (in the shaded boxes). We requested a priori test for independent groups with power = .9, α = .05, with effect size = .47 (our specific alternative), and tested against a one-tailed alternative. The total N of 158 is more than twice the N of 72 in our experimental design.

Suppose we had decided that a practical limit on the total sample size was 150 participants. Generally, we will have to accept that power will suffer if there are constraints on the size of our sample. In this scenario, the power penalty would not be severe because our maximum sample size is not much smaller than that needed for power of .9.

On the other hand, suppose that we were dealing with a much smaller minimum effect size of interest. Even if we lowered our desired power to .8, if we set d to .25 – small by Cohen's (1988) standards – we would require 397 subjects and proceeding with only 150