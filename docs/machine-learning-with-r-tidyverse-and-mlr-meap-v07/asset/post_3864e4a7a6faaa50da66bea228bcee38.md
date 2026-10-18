
If what we just did is a little unclear to you, print the `metricsTib` tibble to see what the output looks like. We have a tibble with one column for each of the internal cluster metrics, and a column indicating the number of clusters the metrics were calculated for.

### Listing 17.4 Calculating performance metrics of our clustering model

```r
metricsTib <- map_df(gvhdbBoot, function(boot) {
  d <- dist(boot, method = "euclidean")
  cl <- hclust(d, method = "ward.D2")

  map_df(3:8, function(k) {
    cut <- cutree(cl, k = k)
    cluster_metrics(boot, clusters = cut, dist_matrix = d)
  })
})
```

Let’s plot the result of our bootstrapping experiment. We’re going to create a separate sub-plot for each internal cluster metric (using facetting). Each sub-plot will show the number of clusters on the x axis, the value of the internal cluster metric on the y axis, a separate line for each individual bootstrap sample, and a line that connects the mean value across all bootstraps.

To achieve this, we first need to mutate a new column, indicating the bootstrap sample each case belongs to. As there are ten bootstrap samples, evaluated for six different numbers of clusters each (three to eight), I create this variable by using the `rep()` function to repeat each number from one to ten, six times. I wrap this inside the `factor()` function to ensure this isn’t treated as a continuous variable when plotting. Next, I gather the data so that the choice of internal metric is contained within a single column, and the value of that metric is held in another column. I specify `-clusters` and `-bootstrap` to tell the function **not** to gather these variables. Print this new tibble and ensure you understand how we got there.

### Listing 17.5 Transforming the data ready for plotting

```r
metricsTib <- metricsTib %>%
  mutate(bootstrap = factor(rep(1:10, each = 6))) %>%
  gather(key = "Metric", value = "Value", -clusters, -bootstrap)
```

Now that our data is in this format, we can create the plot (follow along with me in code listing 17.6). I map the number of clusters (as a factor) to the x aesthetic, and the value of the internal cluster metric to the y aesthetic. I add a `facet_wrap()` layer to facet by internal cluster metric, setting the `scales = "free_y"` argument as the metrics are on different scales. Next, I add a `geom_line()` layer, using the `size` argument to make these lines less prominent, and map the bootstrap sample number to the group aesthetic. This layer will therefore draw a separate, thin line for each bootstrap sample.

### TIP

Notice that when you specify an aesthetic mapping inside the `ggplot()` function, the mapping is inherited by all additional layers that use that aesthetic. However, you can specify aesthetic mappings using the `aes()` function inside each geom function, and the mapping will apply to that layer only.

### NOTE

The other option would be to use "mean_cl_normal" to construct the confidence intervals, but this assumes the data are normally distributed, and this may not be true.

I then add another `geom_line()` layer which will connect the mean across all bootstrap samples. By default, the `geom_line()` function likes to connect individual values. If we want the function to connect a summary statistic (like a mean), we need to specify the `stat = "summary"` argument, then use the `fun.y` argument to tell the function what summary statistic we want to plot. Here I’ve used "mean", but you can supply the name of any function that returns a single value of y for its input.

Finally, it would be nice to visualize the 95% confidence interval for the bootstrap sample. 95% confidence intervals tell us that, if we were to repeat this experiment 100 times, 95 of the constructed confidence intervals would be expected to contain the true value of the metric. The more the estimates agree with each other between bootstrap samples, the smaller the confidence interval will be. We want to visualize the confidence intervals using the flexible `stat_summary()` function. The `stat_summary()` function can be used to visualize multiple summary statistics in many different ways. To draw the mean ± 95% confidence intervals, we use the `fun.data` argument to specify we want "mean_cl_boot". This will draw bootstrap confidence intervals (95% by default).

So we’ve defined our summary statistics, now let’s specify the geom that we’re going to use to represent them, using the `geom` argument. The geom "crossbar" draws what looks like the box part of a box plot, where a solid line is drawn through the measure of central tendency we specified (mean in this case), and the upper and lower limits of the box extend to the range of the measure of dispersion we asked for (95% confidence limits in this case). Then according to my preference, I set the width of the crossbars to 0.5, and the fill color to white.

```r
ggplot(metricsTib, aes(as.factor(clusters), Value)) +
    facet_wrap(~ Metric, scales = "free_y") +
    geom_line(size = 0.1, aes(group = bootstrap)) +
    geom_line(stat = "summary", fun.y = "mean", aes(group = 1)) +
    stat_summary(fun.data="mean_cl_boot",
        geom="crossbar", width = 0.5, fill = "white") +
    theme_bw()
```

The resulting plot from code listing 17.6 is shown in figure 17.5. Take a moment to appreciate how beautiful the result is after all the hard work we just put in. Look back at code listing 17.6 to make sure you understand how we created this plot (`stat_summary()` is probably the most confusing bit). It seems that the number of clusters resulting in the smallest mean Davies-Bouldin index, and the largest mean Dunn index and mean pseudo F statistic is four. Take a look at the thin lines representing each individual bootstrap. Can you see that some of them might have led us to conclude a different number of clusters was optimal? This is why bootstrapping these metrics is better than calculating each metric only once, using a single dataset.

![](img/a22105d68c35e8d5bd3c7bafb4644881_437_0.png)

Figure 17.5 Plotting the result of our bootstrap experiment. Each sub-plot shows the result of a different internal cluster metric. The x axes show cluster number and the y axes show the value of each metric. Faint lines connect the results of each individual bootstrap sample, while the bold line connects the mean. The top and bottom of each crossbar indicate the 95% confidence interval for that particular value, and the horizontal line represents the mean.

![](img/a22105d68c35e8d5bd3c7bafb4644881_439_0.png)

Next, let's plot the clusters using `ggpairs()` like we did for our k-means model in the last chapter.

```r
gvhdTib <- mutate(gvhdTib, hclustCluster = as.factor(gvhdCut))
ggpairs(gvhdTib, aes(col = hclustCluster),
    upper = list(continuous = "density"),
    lower = list(continuous = wrap("points", size = 0.5)))
    + theme_bw()
```

The resulting figure from code listing 17.8 is shown in figure 17.7. Compare these clusters to the ones returned by our k-means model in figure 17.8. Both methods result in similar cluster membership, and the clusters from our hierarchical clustering also seem to undercluster cluster three.

> Jaccard index = \left( \frac{number of values in both sets}{total number of unique values} \right) \times 100

For example, if we have two sets:
a = {3, 3, 5, 2, 8}
b = {1, 3, 5, 6}
then the Jaccard index is:

> Jaccard index = (2/6) × 100 = 33.3%

So if we cluster on multiple bootstrap samples, we can calculate the Jaccard index between the "original" clusters (the clusters on all the data), and each of the bootstrap samples, and take the mean. If the mean Jaccard index is low, then cluster membership is changing considerably between bootstrap samples, indicating our clustering result is unstable and may not generalize well. If the mean Jaccard index is high, then cluster membership is changing very little, indicating a stable clustering result.

Luckily for us, the `clusterboot()` function from the fpc package has been written to do just this! Let’s first load the fpc package into our R session. As the `clusterboot()` function produces a series of base R plots as a side effect, let’s split the plotting device into three rows and four columns to accommodate the output, using `par(mfrow = c(3, 4))`.

The first argument to the `clusterboot()` function is the data. This argument will accept either the raw data or a distance matrix of class `dist` (it will handle either appropriately). The argument B is the number of bootstrap samples we wish to calculate, which I’ve set to ten for the sake of reducing running time. The `clustermethod` argument is where we specify which type of clustering model we wish to build (see `?clusterboot` for a list of available methods, but many common methods are included). For hierarchical clustering, we set this argument equal to `disthclustCBI`. The `k` argument specifies the number of clusters we want to return, `method` lets us specify the distance metric we want to use for clustering, and `showplots` gives us the opportunity to suppress the printing of the plots if we want. The function may take a couple of minutes to run.

I’ve truncated the output from printing the result of `clusterboot()` to show the most important information: the Clusterwise Jaccard bootstrap means. These four values are the mean Jaccard
