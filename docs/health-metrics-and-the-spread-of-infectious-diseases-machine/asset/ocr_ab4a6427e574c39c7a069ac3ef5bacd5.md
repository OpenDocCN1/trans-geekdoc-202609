# Lung Cancer Deaths by Age in Germany

```
hmsidWR:germany_lungc |>
```r
gplot(aes(x = age, y = dx, group = sex) +
  geom_col(position='identity',
    fill='white',
    colour='black') +
  # adjust the layout with three barplot for each category
  facet_grid(sex ~ .) +
  labels(title = 'Lung Cancer Deaths by Age in Germany',
    x = 'Age',
    y = "Deaths") +
  theme(axis.text.x = element_text(angle = 45, hjust = 1))
```
```

![](bbox=[0.125, 0.301, 0.873, 0.638])

**Figure 10.3** Barplots Layout - Lung Cancer Deaths by Age in Germany

# 10.4.1 Colors and Patterns

Choosing the right colours for your visualisations is crucial. Colors can highlight important aspects of your data and improve readability. Many tools provide built-in color palettes, but you can also customise your own. Here we just use the `scale_color_manual()` function to customise the original plot, with a new color palette.

By typing `scale_color_manual()` in the console, you can access the documentation and explore other options for customising the `scale_<..>.<..>` functions.

```
# Example: customised colours in a bar chart
lineplot +
scale_color_manual(values = c("brown", "navy", "orange"))
```