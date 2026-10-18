If what we just did is a little unclear to you, print the `metricsTib` tibble to see what the output looks like. We have a tibble with one column for each of the internal cluster metrics, and a column indicating the number of clusters the metrics were calculated for.

# Listing 17.4 Calculating performance metrics of our clustering model

```
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
```

Let’s plot the result of our bootstrapping experiment. We’re going to create a separate sub-plot for each internal cluster metric (using facetting). Each sub-plot will show the number of clusters on the x axis, the value of the internal cluster metric on the y axis, a separate line for each individual bootstrap sample, and a line that connects the mean value across all bootstraps.

To achieve this, we first need to mutate a new column, indicating the bootstrap sample each case belongs to. As there are ten bootstrap samples, evaluated for six different numbers of cluster each (three to eight), I create this variable by using the `rep()` function to repeat each number from one to ten, six times. I wrap this inside the `factor()` function to ensure this isn’t treated as a continuous variable when plotting. Next, I gather the data so that the choice of internal metric is contained within a single column, and the value of that metric is held in another column. I specify `--clusters` and `--bootstrap` to tell the function **not** to gather these variables. Print this new tibble and ensure you understand how we got there.

# Listing 17.5 Transforming the data ready for plotting

```
```r
metricsTib <- metricsTib %>%
  mutate(bootstrap = factor(rep(1:10, each = 6))) %>%
  gather(key = "Metric", value = "Value", --clusters, --bootstrap)
```
```

Now that our data is in this format, we can create the plot (follow along with me in code listing 17.6). I map the number of clusters (as a factor) to the x aesthetic, and the value of internal cluster metric to the y aesthetic. I add a `facet_wrap()` layer to facet by internal cluster metric, setting the `scales = "free_y"` argument as the metrics are on different scales. Next, I add a `geom_line()` layer, using the `size` argument to make these lines less prominent, and map the bootstrap sample number to the group aesthetic. This layer will therefore draw a separate, thin line for each bootstrap sample.