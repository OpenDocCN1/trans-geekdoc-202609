# TIP

Notice that when you specify an aesthetic mapping inside the ggplot() function layer, the mapping is inherited by all additional layers that use that aesthetic. However, you can specify aesthetic mappings using the aes() function inside each geom function, and the mapping will apply to that layer only.

# NOTE

The other option would be to use "mean_cl_normal" to construct the confidence intervals, but this assumes the data are normally distributed, and this may not be true.

I then add another geom_line() layer which will connect the mean across all bootstrap samples. By default, the geom_line() function likes to connect individual values. If we want the function to connect a summary statistic (like a mean), we need to specify the stat = "summary" argument, then use the fun.y argument to tell the function what summary statistic we want to plot. Here I’ve used "mean", but you can supply the name of any function that returns a single value of y for it’s input.

Finally, it would be nice to visualize the 95% confidence interval for the bootstrap sample. 95% confidence intervals tell us that, if we were repeat this experiment 100 times, 95 of the constructed confidence intervals would be expected to contain the true value of the metric. The more the estimates agree with each other between bootstrap samples, the smaller the confidence interval will be. We want to visualize the confidence intervals using the flexible stat_summary() function. The stat_summary() function can be used to visualize multiple summary statistics in many different ways. To draw the mean ± 95% confidence intervals, we use the fun.data argument to specify we want "mean_cl_boot". This will draw bootstrap confidence intervals (95% by default).

So we’ve defined our summary statistics, now let’s specify the geom that we’re going to use to represent them, using the geom argument. The geom "crossbar" draws what looks like the box part of a box plot, where a solid line is drawn through the measure of central tendency we specified (mean in this case), and the upper and lower limits of the box extend to the range of the measure of dispersion we asked for (95% confidence limits in this case). Then according to my preference, I set the width of the crossbars to 0.5, and the fill color to white.



```
ggplot(metricsTib, aes(as.factor(clusters), Value)) +
    facet_wrap(~ Metric, scales = "free_y") +
    geom_line(size = 0.1, aes(group = bootstrap)) +
    geom_line(stat = "summary", fun.y = "mean", aes(group = 1)) +
    stat_summary(fun.data="mean_cl_boot",
        geom="crossbar", width = 0.5, fill = "white") +
    theme_bw()
```