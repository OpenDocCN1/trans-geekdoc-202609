# 9.6 Case study: Are action or romance movies rated higher?

this plot. The boxplot show that the median sample rating is higher for romance movies.

However, there is a large amount of overlap between the boxes. Recall that the median is not necessarily the same as the mean either, depending on whether the distribution is skewed.

Let's calculate some summary statistics split by the binary categorical variable genre: the number of movies, the mean rating, and the standard deviation split by genre. We will do this using dplyr wrangling verbs. Notice in particular how we count the number of each type of movie using the n() summary function.

```
movies_sample |>
group_by(genre) |>
summarize(n = n(), mean_rating = mean(rating), std_dev = sd(rating))
```

```
# tibble: 2 x 4
genre n mean_rating std_dev
<chr> <int> <dbl> <dbl>
1 Action 32 5.275 1.36121
2 Romance 36 6.2222 1.60963
```

Observe that we have 36 movies with an average rating of 6.322 stars and 32 movies with an average rating of 5.275 stars. The difference in these average ratings is thus 6.322 - 5.275 = 1.047. So there appears to be an edge of 1.047 stars in favor of romance movies. The question is, however, are these results indicative of a true difference for romance and action movies? Or could we attribute this difference to chance variation?

# 9.6.2 Sampling scenario

Let's revisit this study in terms of terminology and notation related to sampling we studied in Subsection 7.2.1. The study population is all movies in the IMDb database that are either action or romance (but not both). The sample from this population is the 68 movies included in the movies_sample dataset.

Since this sample was randomly taken from the population movies, it is representative of all romance and action movies on IMDb. Thus, any analysis and results based on movies_sample can generalize to the entire population. What are the relevant parameter and point estimates? We introduce the fourth sampling scenario in Table 9.6.