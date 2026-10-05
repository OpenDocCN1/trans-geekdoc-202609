# 9.6 Case study: Are action or romance movies rated higher?

What proportion of the null distribution is shaded? In other words, what is the numerical value of the p-value? We use the get_p_value() function to compute this value:

```
null_distribution_movies |>
get_p_value(obs_stat = obs_diff_means, direction = "both")
```

```
# A tibble: 1 x 1
p_value
  <dbl>
1  0.004
```

This p-value of 0.004 is very small. In other words, there is a very small chance that we would observe a difference of 5.275 - 6.322 = -1.047 in a hypothesized universe where there was truly no difference in ratings.

But this p-value is larger than our (even smaller) pre-specified α significance level of 0.001. Thus, we are inclined to fail to reject the null hypothesis H₀ : μₐ - μₛ = 0. In non-statistical language, the conclusion is: we do not have the evidence needed in this sample of data to suggest that we should reject the hypothesis that there is no difference in IMDb ratings between romance and action movies. We, cannot say that a difference exists in romance and action movie ratings, on average, for all IMDb movies.

# Learning check

(LC9.9) Conduct the same analysis comparing action movies versus romantic movies using the median rating instead of the mean rating. What was different and what was the same?

(LC9.10) What conclusions can you make from viewing the faceted histogram looking at rating genre that you could not see when looking at the boxplot?

(LC9.11) Describe in a paragraph how we used Allen Downey's diagram to conclude if a statistical difference existed between mean movie ratings for action and romance movies.

(LC9.12) Why are we relatively confident that the distributions of the sample ratings will be good approximations of the population distributions of ratings for the two genres?

(LC9.13) Using the definition of p-value, write in words what the p-value represents for the hypothesis test comparing the mean rating of romance to action movies.