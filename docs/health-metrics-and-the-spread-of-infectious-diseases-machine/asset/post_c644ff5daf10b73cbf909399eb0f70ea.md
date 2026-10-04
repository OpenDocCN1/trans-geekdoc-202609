
```r
scatterplot <- hmsdwR::germany_lungc |>
gplot(aes(x = age, y = dx)) +
geom_point(aes(shape = sex)) +
  labs(title = "Lung Cancer Deaths by Age in Germany",
      x = "Age",
      y = "Deaths")
```

```r
lineplot <- hmsdwR::germany_lungc |>
gplot(aes(x = age, y = dx, group = sex)) +
geom_line(aes(linetype = sex)) +
geom_point() +
  labs(title = "Lung Cancer Deaths by Age in Germany",
      x = "Age",
      y = "Deaths")
```

```r
barplot <- hmsdwR::germany_lungc |>
gplot(aes(x = age, y = dx, group = sex)) +
gpgpattern::geom_col_pattern(aes(pattern = sex),
  position="stack",
  fill='white') +
  labs(title = "Lung Cancer Deaths by Age in Germany",
      x = "Age",
      y = "Deaths")
```

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_185_0.png)

(a) Scatterplot: Lung Cancer Deaths by Age in Germany

(b) Lineplot: Lung Cancer Deaths by Age in Germany

(c) Barplot: Lung Cancer Deaths by Age in Germany

Figure 10.2 Scatterplot and Barplot of Lung Cancer Deaths by Age in Germany

All of these plots have a grammar of graphic structure, which means that they are built using layers of data, aesthetics, and geometric objects. The `ggplot()` initializes the plot, and then we add layers using `geom_point()`, `geom_line()`, and `geom_col_pattern()` in this particular example, to create the visualizations. We can customise these plots by adding titles, labels, and adjusting the appearance of the plot elements.

Finally, another way to visualise Lung Cancer Deaths by Age in Germany is to use the `geom_col()` function and create a bar plot for each sex category. This is a basic bar plot, and we will enhance it by adjusting the layout. The `facet_()` functions are used to create a grid of plots, where each plot represents a different subset of the data. In this case, we are using `facet_grid()` to create a grid of plots based on the sex variable.

# Lung Cancer Deaths by Age in Germany

```r
hmsdwR::germany_lungc |>
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

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_186_0.png)

**Figure 10.3** Barplots Layout - Lung Cancer Deaths by Age in Germany

# 10.4.1 Colors and Patterns

Choosing the right colours for your visualisations is crucial. Colors can highlight important aspects of your data and improve readability. Many tools provide built-in color palettes, but you can also customise your own. Here we just use the `scale_color_manual()` function to customise the original plot, with a new color palette.

By typing `scale_color_manual()` in the console, you can access the documentation and explore other options for customising the `scale_<..>.<..>` functions.

```r
# Example: customised colours in a bar chart
lineplot +
scale_color_manual(values = c("brown", "navy", "orange"))
```

# Example: Visualising Lung Cancer Deaths by Age in Germany

In addition to colors, patterns can be used to de-differentiate between the groups in the plot. The {ggpattern} package provides a variety of patterns that can be used to fill the bars in a bar plot. Here we used the geom_col_pattern() function to add patterns to the bars in the plot. An example is shown in the plot with the barplot. Another way is to use the linetype or shape aesthetics to differentiate groups in a line plot or scatter plot.

# 10.4.2 Theme, Legends, and Guides

Legends and guides are essential for interpreting visualisations. They help the audience understand what different colors, shapes, or sizes represent in the plot. Here we have just changed the title of the legend, but much can be done, such as changing the position, and labels. To change the position of the legend we can use the theme() function as shown below.

In the R console, typing ?theme() will provide more information on customised the appearance of your plots. In this case it is useful to adjust the angle of the text in the x-axis, and this can be done by specifying the angle parameter in the theme() function.

The guides() function can be used to customise the legend, such as reversing the order of the legend items.

```r
# Customising a legend to a plot
lineplot1 <- ggplot +
  labs(linetype = "Sex"
```

# 10.4.3 Plot Layouts

The layout of your plots can significantly impact their effectiveness. Arranging multiple plots in a grid can help compare different aspects of your data side-by-side. We can use the grid.arrange() function from the {gridExtra} package to arrange multiple plots in a grid layout. Or, we can use the layout() function to specify the layout of the plots. There are other packages that can be used with {patchwork} and {cowplot}, which provide additional functionalities for arranging plots.

```r
# Example: Arranging multiple plots
library(gridExtra)

grid.arrange(lineplot, lineplot1, lineplot2, ncol = 3)
```

# Introduction to Data Visualisation

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_188_0.png)

(a) Basic Lineplot

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_188_1.png)

(b) Customised Lineplot

![](img/6b61f0d3dcab44c60cdfe4e888d549c9_188_2.png)

(c) Customised Lineplot on a Log Scale

Figure 10.4 Customised Lineplots and Logarithmic Scale Transformation

# 10.4.3.1 Exercise

Replicate the plots above, customizing the legend and axis text to improve readability. Apply a logarithmic scale to the y-axis for better data visualization, and consider adding a caption to indicate the data source.

# 10.4.4 Saving as an Image

Once you've created your visualisation, you might want to save it as an image file for sharing or publication.

```r
savefig("lineplot.png", plot = leaflet, width = 6, height = 4)
```

# 10.5 Practising Data Visualisation

To practise making data visualisations, there are numerous free resources available to provide valuable information and opportunities to enhance your skills. By engaging with these platforms, you can practise your abilities, share your results, and receive feedback from the community. While the feedback may sometimes be critical, it is an essential part of the learning process and will help you if you stay persistent.

Participating in competitions and challenges as #Tuesday, #30DayChartChallenge, and #30DayMapChallenge offers you to create and share visualisations on various themes, pushing you to experiment with different techniques and styles. By consistently participating in these challenges and actively seeking feedback, you will steadily enhance your proficiency. Over time, you will find yourself becoming more adept and confident in your data visualisation skills.

# Interpreting Model Results Through Visualisation

Learning Objectives

- Visualize predicted vs. observed values and assess residuals
- Interpret model metrics with VIP, accuracy, and partial dependency plots
- Create and customize ROC curves and compute AUC for classification models

In the introduction to data visualisation (Chapter 10), we explored foundational techniques for effectively communicating model results and data insights through plots. We reviewed essential plots used to visualise predictions and outcomes, such as scatter plots, line graphs, and bar charts. The chapter also covered how to customise these plots using colours, palettes, legends, and guides to improve clarity and visual appeal. Additionally, we discussed how to craft data stories by organising multiple plots in a layout and saving them as image files for reports or presentations.

In this chapter, which is an essential part of the data visualisation section, we focus on how to effectively interpret and use the results from machine learning models in the context of health metrics and infectious diseases.

We will explore how to visualise the results of:

- Regression models with a linear regression, and a generalized additive model (GAM)
- Classification models with decision trees, and random forest models.

# 11.1 Practical Insights and Examples

The practise of visualising model results is essential for communicating insights from a model to stakeholders.

Considerations for visualising model results include:

- Understanding the data: Before visualising the results, it is important to understand the data and the model used. This includes the variables, their relationships, and the assumptions of the model.
- Choosing the right visualisation: Different types of data and models require different types of visualisations. It is important to choose the right visualisation to effectively communicate the results.
