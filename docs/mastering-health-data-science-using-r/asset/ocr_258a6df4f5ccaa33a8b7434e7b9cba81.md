```
```r
pain_df$HAS_FOLLOW_UP <-
  !is.na(pain_df$PAIN_INTENSITY_AVERAGE_FOLLOW_UP)
ggplot(pain_df) +
  geom_density(aes(x = PROMIS_PHYSICAL_FUNCTION,
                   group = HAS_FOLLOW_UP,
                   color = HAS_FOLLOW_UP)) +
  scale_x_continuous(breaks = c(0:10)) +
  scale_color_discrete(name = "Follow-Up", labels = c("No", "Yes")) +
  labs(x = "PROMIS Physical Function T-Score",
       y = "Estimated Density") +
  theme_minimal()
```
```

![](bbox=[0.127, 0.365, 0.788, 0.636])

Let’s try another example. Suppose that we want to find the distribution of initial overall pain by those that do and do not have a follow-up. In this case, we want to plot the proportion of each pain score for each group rather than compare counts. We first need to find these proportions, which we do by grouping and summarizing over our data.

```
```r
pain_df_grp <- pain_df %>%
  group_by(HAS_FOLLOW_UP, PAIN_INTENSITY_AVERAGE) %>%
  summarize(tot = n()) %>%
  mutate(prop = tot/sum(tot)) %>%
  ungroup()
head(pain_df_grp)
#> # A tibble: 6 x 4
```
```