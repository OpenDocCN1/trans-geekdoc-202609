# 9 Kabhie Kabhie

# 9 Hypothesis Testing

| 9 Kabhie Kabhie | 1976 | 7.7 Romance |
| 10 Electric Horseman, The | 1979 | 5.8 Romance |

# i 58 more rows

The variables include the title and year the movie was filmed. Furthermore, we have a numerical variable rating, which is the IMDb rating out of 10 stars, and a binary variable genre indicating if the movie was an Action or Romance movie. We are interested in whether Action or Romance movies got a higher rating on average.

Let's perform an exploratory data analysis of this data. Recall from Subsection 2.7.1 that a boxplot is a visualization we can use to show the relationship between a numerical and a categorical variable. Another option you saw in Section 2.6 would be to use a faceted histogram. However, in the interest of brevity, let's only present the boxplot in Figure 9.14.

```
ggplot(data = movies_sample, aes(x = genre, y = rating)) +
geom_boxplot() +
labs(y = "IMDB rating")
```

![](bbox=[0.118, 0.445, 0.882, 0.775])

FIGURE 9.14: Boxplot of IMDb rating vs. genre.

Eyeballing Figure 9.14, romance movies have a higher median rating. Do we reason to believe, however, that there is a significant difference between the mean rating for action movies compared to romance movies? It is hard to just based on