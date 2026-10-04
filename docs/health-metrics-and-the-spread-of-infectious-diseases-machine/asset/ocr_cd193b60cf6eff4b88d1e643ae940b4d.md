# General Guidelines for Data Visualisation

```
ggplot(data = df, aes(x = x, y = y, color = z))
geom_point()
```

{ggplot2} provides a wide range of ge, scales, and themes to customise the appearance of the plot. By combining these elements, you can create visually appealing and informative visualisations that effectively communicate your data.

It allows you to create complex visualisations by combining simple building blocks, each layer of the plot allowing for an aesthetic mapping of data to visual properties such as colour, fill, shape, and size, making it easy to create a wide range of visualisations, or even new data. In this example there is also the use of an alternative to the `labs()` function with the `ggtitle()` function, which differs when the title is placed in the plot.

```
ggplot(data = df, aes(x = x, y = y, color = z))
geom_point()
geom_point(data = df, aes(x = x2, y = y2, color = z2))
ggt("Scatter Plot")
```

In addition to functions provided by {ggplot2}, there are ggplot extensions, other functions and packages that can be used to create visualisations, such as {plotly}, {plotly}, {leaflet}, {tmap}, and {shiny}. These tools provide additional functionality for creating interactive plots, maps, and dashboards, allowing for more engaging and dynamic data visualisations.

# 10.3 General Guidelines for Data Visualisation

There are many types of plots that can be used to visualise data, such as cross tabulations for categorical variables, scatter plots for continuous variables, side-by-side box plots, and other summaries.

Here are some specifications about the usage of common types of plots:

# 10.4 Example: Visualising Lung Cancer Deaths by Age in Germany

This is an example of visualise lung cancer deaths by age in Germany. It is a line plot showing the number of deaths by age group. We have already seen how to create a line plot using `ggplot2` in previous chapters, the focus here is on customising the line plot to make it more visually appealing and informative.

This is a basic output, and we will enhance it by customising patterns, colours, legend, and adjusting the layout. We will also explore how to save the plot as an image for sharing or publication.

```
library(ggplot2)
library(ggpattern)
```