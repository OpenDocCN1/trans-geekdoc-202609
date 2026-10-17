![](bbox=[0.169, 0.114, 0.871, 0.401])

This motivates us to look at the correlation between these two columns by state. We plot this using the `plot_usmap()` function from the usmap package. Interestingly, we observe different relationships throughout the country, but none of the correlations are particularly strong.

```
```r
# Calculate and plot correlation between cases and mobility, y state
covid_cor <- covid %>%
  group_by(state) %>%
  summarize(correlation = cor(weekly_cases, m50,
                              use = "complete.obs"))

plot_usmap(regions = "states", data = covid_cor,
           values = "correlation") +
  scale_fill_gradient2(low = "darkblue", high = "darkred",
                       mid = "white", name = "Correlation") +
  labs(title = "Correlation Between Cases and Mobility") +
  theme(legend.position = "right")
```
```