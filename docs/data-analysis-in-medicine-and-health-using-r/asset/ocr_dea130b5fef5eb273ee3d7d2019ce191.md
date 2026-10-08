# 4.12 More Complex Plots

![](bbox=[0.121, 0.093, 0.859, 0.403])

To change the parameter shape, for example, to the plus symbol, you can set the argument for shape to equal 3.

```
ggplot(data = gapminder, +
  geom_point(mapping = aes(x = year, y = lifeExp),
             shape = 3) +
  theme_bw())
```

![](bbox=[0.121, 0.591, 0.859, 0.901])