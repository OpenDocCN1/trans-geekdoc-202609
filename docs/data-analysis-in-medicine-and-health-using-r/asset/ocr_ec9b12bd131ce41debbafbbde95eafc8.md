# 4.12 More Complex Plots

GDP (in log) and life expectancy:

Data from Gapminder

![](bbox=[0.118, 0.142, 0.882, 0.527])

And we can label the x-axis and y-axis:

```
mypop +
ylab("Life Expectancy") +
xlab("Percapita GDP in log")
```

## 'geom_smooth()' using method = 'loess' and formula = 'y ~ x'