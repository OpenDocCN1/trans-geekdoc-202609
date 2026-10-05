56

2 Data Visualization

Lastly, another type of barplot is a faceted barplot. Recall in Section 2.6 we visualized the distribution of hourly wind speeds at the 3 NYC airports split by month using facets. We apply the same principle to our barplot visualizing the frequency of carrier split by origin: instead of mapping origin to fill we we include it as the variable to create small multiples of the plot across the levels of origin.

```
ggplot(data = flights, mapping = aes(x = carrier)) + 
geom_bar() + 
facet_wrap(~ origin, ncol = 1)
```

![](bbox=[0.118, 0.276, 0.882, 0.773])

FIGURE 2.26: Faceted barplot comparing the number of flights by carrier and origin.