# ggplot2 and Extensions for Publication Quality Plots

predicate will be highlighted and others backgrounded. The predicate here is simply whether the scaled_p value is over 10, and the value for label_type tells which column to use for labels. ggighlight() actively shades the predicate-failing uninteresting genes and puts the rest in the foreground with labels; Figure 3.9.

![](bbox=[0.135, 0.198, 0.864, 0.433])

Figure 3.9 – Highlighted volcano plot

The second example is a line plot of gene expression-levels over time; each line represents a single gene. We again start by creating a base ggplot using ath_ts, which comes in the data package, though this time with the geom_line() geom, and we add a more readable x axis with scale_continuous() while we are at it. Then, we apply a highlighting filter with ggighlight(), specifying the predicate as any whose minimum over the whole course drops below 0.05 (i.e., significant at any time point). We format the look of the unhighlighted lines with the unhighlighted_params argument, which takes a list of settings for ggplot aesthetics. Figure 3.10.

![](bbox=[0.135, 0.635, 0.864, 0.866])

Figure 3.10 – Highlighted time series