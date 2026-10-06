# Easily Performing Statistical Tests Using Linear Models

5. Create a balloon plot for the data:

```
library(ggplot2)
gggplot(side_effects) +
aes(treatment, side_effect) +
geom_point(aes(size = frequency))
```

We end up with a good view of the categ data and how it varies by group.

# How it works...

In the first part of the recipe, we look at ordinal data. The data load is disease scores, which are given numbers for the categories. This is a clear source of confusion; although the categories look like numbers, we cannot treat them as such, as they don' behave like that. For example, a score of four does not indicate twice much as a score of two. In step 1, we explicitly make the numbers into factors, which will help R to treat them as they should be. We use transmute() to change the scheme color of the data frame in the order using factor() with the ordered option set. We then create a column stating the rank of the observation throughout the data. Note that transmute() quietly discards columns that aren't mentioned, so we add the names of the columns we want to keep (but not) to the end of the factor. We can now model in the way that we used to, and we do so in step 3. The results of the modeling and ANOVA appear as:

```
## Simultaneous Tests for General Linear Hypotheses
##
## Multiple Comparisons of Means: Tukey Contrasts
##
##
## Fit: 1lm(formula = rank_score - strain, data = scores)
##
## Linear Hypotheses:
## Estimate Std. Error t value Pr(|t|) **
## deadly control == 0 5.5000 0.9129 6.025 0.00211 *
## mild control == 0 3.5000 0.9129 3.834 0.00217 *
## mild deadly == 0 -2.0000 0.9129 -2.191 0.01564
##
## Signif. codes: 0 **** 0.001 *** 0.01 ** 0.05 * .01 . 1
## (Adjusted p values reported -- single-step method)
```

We can see that the deadly and mild strains significantly greater evidence of disease than the control, they do not differ from each other.

In step 4, we change over to looking at some nominal, non-ordered data. There's no way to systematically convert these categories to numbers (e.g., by ranking), and while it is possible to examine them with linear models in the way we in the earlier steps, it is much more complicated. So we take advantage