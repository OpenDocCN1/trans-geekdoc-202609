# CHAPTER 4 COMING TO COMPLEX CONCLUSIONS: INFERENTIAL STATISTICS AND STATISTICAL TESTING

# # Covariance

Covariance is conceptually similar to correlation, but where correlation is always between -1 and 1, covariance depends on the scale of the two variables being compared. Calculating it means multiplying the differences of the means of both variables and summing for each data point and dividing by degrees of freedom.

It’s also common to display the covariance matrix the same way as correlation, but the numbers will be different, some quite different. Table 4-7 shows the results of the covariance calculation on the same data on sick kids.

**Table 4-7.** Covariance matrix of sick child age, height, and weight

| Age (years) | Height (in) | Weight (Kg) |
| Age (years) | 14.692915 | 25.910734 | 60.605008 |
| Height (in) | 25.910734 | 55.086591 | 125.204444 |
| Weight (Kg) | 60.605008 | 125.204445 | 503.446999 |

We can see that these numbers are not confined between -1 and 1 like correlation, and it’s more difficult to really understand what they mean. Covariance is not often inspected directly and is more often used in other calculations, like ANCOVA as we saw above. Correlation is more intuitive.

# # Correlation vs. Causation

Let’s revisit the adage “Correlation is not causation.” The point it’s making is that you can’t assume that a change in one variable causes a change in the other variable. Sometimes things happen to seem correlated, but it’s simply coincidental. There’s a blog Spurious Correlations that finds funny data correlates. For instance, the popularity of the name Thomas between 1985 and 2020 correlates almost perfectly with the number of car thefts in Maine, which can be seen in Figure 4-6.