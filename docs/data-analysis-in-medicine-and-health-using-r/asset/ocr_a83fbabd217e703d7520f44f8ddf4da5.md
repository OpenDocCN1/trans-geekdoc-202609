![](bbox=[0.125, 0.087, 0.839, 0.523])

Another smooth plot but setting the parameter for color but in greyscale. Again, if you print on black and white text, and you will not be able to see the color. To see the color clearly, just remove the scale_colour_grey() + codes.

```
ggplot(data = gapminder) +
  geom_smooth(mapping = aes(x = log(gdpPercap),
                               y = lifeExp,
                               colour = continent)) +
  scale_colour_grey() +
  theme_bw())

## `geom_smooth()` using method = 'loess' and formula = 'y ~ x'
```