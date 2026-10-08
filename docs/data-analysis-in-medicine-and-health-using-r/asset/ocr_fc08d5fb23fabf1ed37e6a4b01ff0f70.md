![](bbox=[0.218, 0.103, 0.781, 0.365])

From the plot, we can see

+   - a scatterplot
- the scatterplot shows the relationship between year and life expectancy
- as variable year advances, the life expectancy increases

If you look closely, you will notice that

```
ggplot() : function tells R to be ready to make a plot from specified data
geom_point() function tells R to make resources about a scatter plot
```

Users may find more resources about ggplot2 package on the ggplot2 webpage (Wickham et al., 2020). Other excellent resources include the online R Graphics Cookbook and its physical book (Chang, 2013).

# 4.12 More Complex Plots

# 4.2.1 Adding another variable

We can see that the variables we want to plot are specified by aes(). We can add a third variable to make a more complex plot. For example:

+   - data: data = gapminder
- variables: x = year, y = lifeExp, colour = continent