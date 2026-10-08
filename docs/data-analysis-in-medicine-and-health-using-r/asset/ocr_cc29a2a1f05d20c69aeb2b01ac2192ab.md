# 4.12 More Complex Plots

![](bbox=[0.121, 0.093, 0.878, 0.523])

# 4.12.4 Combining different plots

We can combine more than one geoms (type of plots) to overlay plots. The trick is to use multiple geoms in a single line of R code:

```
ggplot(data = gapminder) +
geom_point(mapping = aes(x = log(gdpPercap), y = lifeExp)) +
geom_smooth(mapping = aes(x = log(gdpPercap), y = lifeExp)) +
theme_bw())

## `geom_smooth()` using method = 'gam' and formula = 'y' ~ s(x, bs = "cs")
```