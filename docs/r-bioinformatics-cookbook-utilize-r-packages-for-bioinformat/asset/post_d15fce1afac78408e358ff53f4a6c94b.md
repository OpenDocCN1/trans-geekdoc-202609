
## ggplot2 and Extensions for Publication Quality Plots

```r
label_key = id +
theme(legend.position = "bottom")

p3 <- ggplot(penguins) +
aes(x = flipper_length_mm
```

```r
p4 <- allele_freqs |>
dplyr::filter(Chr == 1) |>
ggplot() +
aes(x = Pos, y = Allele_Freq, label = info) +
geom_point(aes(color = type)) +
facet_grid(Chr ~ , scales = "free x", space = "free") +
scale_color_manual(
	values = c("steelblue","gray","goldenrod","red"),
labels = c("CDS","NON-CDS","NON-SYN-Coding","CTGA")
) +
theme(legend.position = "bottom")
```

- 2. Remove the legends and compose the plots into a column:

```r
library(cowplot)
left_column <- plot_grid(p1 + theme(legend.position = "none"),
p2 + theme(legend.position = "none"),
p3 + theme(legend.position = "none"),
col = 1, labels = c("A","B","C"))
```

- 3. Extract the legends and compose those into a column:

```r
l1 <- get_legend(p1)
l13 <- get_legend(p3)

right_column <- plot_grid(l1, NULL, l13, ncol=1)
```

## Zooming and making callouts from selected plot sections with facetzoom

- 4. Compose the two columns and the last plot:

```r
two_cols <- plot_grid(left_column, right_column, ncol = 2, rel_
widths = c(0.66, 0.34))
labelled_4 <- plot_grid(p4, labels = "D")
```

```r
plot_grid(two_cols, labelled_4, ncol = 1, rel_heights = c(0.6,
0.4))
```

And that is all we need to create a plot from multiple plots.

## How it works...

Step 1 is a long one, but essentially repeats code discussed earlier in the chapter (for example, the first plot comes from the Changing chapters in this ggrides section). Note that in p1 and p3 we modify the legend, using the guides function in the scale_fill_manual() layer to make sure that the grid flows over two or three lines (so that there is one element per line)—this will be important later as the grid will be extracted into a space of its own.

Step 2 we create a plot that includes p1, p2, and p3 by passing them to cowplot::plot_grid() function and setting the number of columns to 1, such that the plots are stacked vertically. We apply labels for each one. Note that the plots have their legends removed using theme before they are stacked; we will apply the labels manually.

Step 3 cowplot_get_legend() function to extract the legends from the original plots to their objects; these objects are stacked into a column, again using plot_grid(). NULL forces the grid to contain an empty element at that point.

Step 4, we compose the two columns we have (again with plot_grid()), this time in columns two (two_cols), using the rel_widths option to allow the plots to take up sixty percent the width of the plot. To finish, we add a label to p4—which you guessed—plot_grid() and then put that over our previous columns by calling plot_grid() for one last time, the number of columns to 1 and the relative heights such that the columns take up the majority of space. The final plot looks like this in Figure 3.18—or it when rendered in the small space for plots provided by this book's format. You may see a clearer plot when it is your on your own machine. As R works by rendering in a viewport—a rectangle of a specified size—and trying to fit into objects, that can overlap when some objects can't be reduced further. This is a problem in this plot composed of many subplots so some elements can't shrunk too—specifically, text must remain large enough to read when the plots get too small, it will overlap. There is sometimes a physical limit on how much space we have for plots. The packages we have used give you control over how you can lay out your plot in the margins options:

## ggplot2 and Extensions for Publication Quality Plots

![](img/dd0d7d9aaacf496c4d1d0e31d83783b3_96_0.png)

And with that, we can see how to compose multiple plots into one plot.

## There's more...

These plots all have different legends, so we had to accommodate them individually. Many of the plots you will share legends and axes. cowplot can help align subplots by axis through the `align_plots()` function.

## See also

The patchwork library offers an alternative take on composing plots, providing a declarative syntax that looks a bit math-like. In the following example, we make two versions of our plots with the legends set on two rows, and in the final, `(p1 + p3s) / p4`, we create a plot layout that puts two plots on one row, above a third plot on its own row. Imagine this to be like a math expression, that is, `plot1` and `plot3`, both over `plot4`. We also add annotation with the `plot_annotation()`

Figure 3.18 – 
