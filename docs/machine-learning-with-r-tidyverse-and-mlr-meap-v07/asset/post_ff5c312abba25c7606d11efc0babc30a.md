
In this section, I’ll show you ways of deciding how many clusters to extract from our hierarchy. Another way of thinking about this is that we’re deciding what level of the hierarchy to use for clustering.

To define a finite number of clusters following hierarchical clustering, we need to define a cut point on our dendrogram. If we cut the tree near the top, we’ll get fewer clusters, and if we cut the tree near the bottom, we’ll get more clusters. So how do we choose a cut point? Well, our friends the Davies-Bouldin index, the Dunn index, and the pseudo F statistic can help us here. For k-means clustering, we performed a cross-validation-like procedure for estimating the performance of different numbers of clusters. Sadly, we can’t use this approach for hierarchical clustering because unlike k-means, hierarchical clustering cannot predict cluster membership of new cases.

> The hierarchical clustering algorithms themselves can’t predict the cluster membership of new cases, but you could do something like assign new data to the cluster with the nearest centroid. You could use this approach to create separate training and test sets to evaluate internal cluster metrics on.

Instead, we can make use of bootstrapping. Recall from chapter 8, that bootstrapping is the process of taking bootstrap samples, applying some computation to each sample, and returning a statistic(s). The mean of our bootstrapped statistic(s) tells us the most likely value, and the distribution gives us an indication as to the stability of the statistic(s).

> Remember that a bootstrap sample is where we randomly select cases from a dataset with replacement, to create a new sample the same size as the old. Sampling "with replacement" simply means that once we sample a particular case, we put it back again, such that there is a possibility it will be drawn again.

In the context of hierarchical clustering, we can use bootstrapping to generate multiple samples from our data, and generate a separate hierarchy for each sample. We can then select a range of cluster numbers from each hierarchy, and calculate the internal cluster metrics for each. The advantage of using bootstrapping is that calculating the internal cluster metrics on the full dataset doesn’t give us an indication as to the stability of the estimate, whereas the bootstrap sample does. The bootstrap sample of cluster metrics will have some variation around its mean, and so we can choose the number of clusters with the most optimal and stable metrics.

Let’s start by defining our own function that takes our data and a vector of cluster memberships, and returns our three familiar internal cluster metrics for the data: the Davies-Bouldin index, the Dunn index, and the pseudo F statistic. As the function we’ll use to calculate the Dunn index expects a distance matrix, we’ll include an additional argument in our function to supply a pre-computed distance matrix too.

Take a look at the function body in code listing 17.2 and follow it through with me so what we’re doing makes sense. I use the `function()` function to define a function, assigning it to the name `cluster_metrics` (this will allow us to call the function using `cluster_metrics()`). I define three mandatory arguments for the function:

- `data`, to which we will pass the data we’re clustering
- `clusters`, a vector containing the cluster membership of every case in `data`
- `dist_matrix`, to which we will pass the pre-computed distance matrix for `data`

The *body* of the function (the instructions that tell the function what to do) is defined inside curly brackets (`{}`). Our function will return a list with four elements, the Davies-Bouldin index (`db`), the pseudo F statistic (`G1`), the Dunn index (`dunn`), and the number of clusters. Rather than define them from scratch, I’m using pre-defined functions from other packages to compute the internal cluster metrics. The Davies-Bouldin index is computed using the `index.DB()` function from the clusterSim package, which takes the `data` and `clusters` arguments (the statistic itself is contained in the `$DB` component). The pseudo F statistic is computed using the `index.G1()` function, also from the clusterSim package, and takes the same arguments as `index.DB()`. The Dunn index is computed using the `dunn()` function from the clValid package, which takes the `dist_matrix` and `clusters` arguments.

Our motivation for defining this function is that we’re going to take bootstrap samples from our dataset, learn the hierarchy in each, select a range of cluster numbers from each, and use our function to calculate these three metrics for each number of clusters, within each bootstrap sample.

### Listing 17.2 Defining the cluster_metrics function

```r
cluster_metrics <- function(data, clusters, dist_matrix) {
    list(db       = clusterSim::index.DB(data, clusters)$DB,
         G1       = clusterSim::index.G1(data, clusters),
         dunn     = clValid::dunn(dist_matrix, clusters),
         clusters = length(unique(clusters))
    )
}
```

So now, let’s create our bootstrap samples. We’re going to create ten bootstrap samples from our gvhdScaled dataset. I’m using the `map()` function to repeat the sampling process ten times, to return a list where each element is a different bootstrap sample.

> **NOTE** Remember that `~` is just shorthand for `function()`.

We’re using the `sample_n()` function from the dplyr package to create our samples. This function randomly samples rows from a dataset. As this function cannot handle matrices, we first need to pipe our gvhdScaled data into the `as_tibble()` function. By setting the argument `size = nrow(.)`, we’re asking the `sample_n()` function to randomly draw a number of cases, equal to the number of rows in the original dataset (the `.` is shorthand for "the dataset that was piped in"). By setting the `replace` argument equal to `TRUE`, we’re telling the function to sample with replacement. Creating simple bootstrap samples really is as easy as this!

### Listing 17.3 Creating bootstrap samples

```r
gvhdBoot <- map(1:10, ~ {
  gvhdScaled %>%
    as_tibble() %>%
    sample_n(size = nrow(.), replace = TRUE)
})
```

Now, let’s use our `cluster_metrics()` function to calculate those three internal metrics for a range of cluster numbers, for each bootstrap sample we just generated. Take a look at code listing 17.4 and don’t go cross-eyed! I’m going to take you through the code step-by-step. I start by calling the `map_df()` function, so that we can apply a function to every element of our list of bootstrap samples. I define an anonymous function, which takes boot (the current element being considered) as its only argument.

> **TIP** The `map_df()` function is just like `map()`, but instead of returning a list, it will combine each element together row-wise to return a data frame instead.

For each element in `gvhdBoot`, the anonymous function computes its Euclidean distance matrix and stores it as the object `d`, and performs hierarchical clustering using that matrix and Ward’s method. Once we have the hierarchy for each bootstrap sample, we then use another `map_df()` function call to select between three and eight clusters to partition the data into, and calculate the three internal clustering metrics on each result. We’re going to use this process to see which number of clusters, between three and eight, gives us the best internal cluster metric values.

Selecting the number of clusters to retain from a hierarchical clustering model is done using the `cutree()` function. We use this function to cut our dendrogram at a place that returns a number of clusters. We can do this either by specifying a height at which to cut, using the `h` argument, or by specifying a specific number of clusters to retain, using the `k` argument (as done here). The first argument is the result of calling the `hclust()` function. The output of the `cutree()` function is a vector indicating the cluster number assigned to each case in the dataset. Once we have this vector, we can call our `cluster_metrics()` function, supplying the bootstrap data, the vector of cluster membership, and the distance matrix.

> **WARNING** This took nearly three minutes to run on my machine!
