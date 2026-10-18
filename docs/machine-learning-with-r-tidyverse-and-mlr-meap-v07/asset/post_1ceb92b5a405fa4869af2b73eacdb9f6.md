
```r
gatheredTuningData <- gather(kMeansTuningData$data,
                             key = "Metric",
                             value = "Value",
                             c(-centers, -iteration, -algorithm))

ggplot(gatheredTuningData, aes(centers, Value, col = algorithm)) +
  facet_wrap(~ Metric, scales = "free_y") +
  geom_line() +
  geom_point() +
  theme_bw()
```

The resulting plot from code listing 16.14 is shown in figure 16.7. Each facet shows a different performance metric, and each separate line shows one of the three algorithms. Notice that for the clustering models with four clusters (centers), the Davies-Bouldin index is minimized, and the Dunn index and pseudo F statistic (G1) are maximized. As lower values of the Davies-Bouldin index and higher values of the Dunn index and pseudo F statistic indicate (in theory) better-separated clusters, all three of the internal metrics agree with each other that four is the optimal number of clusters for this dataset. There is also very little disagreement between the different algorithms, particularly at the optimal value of four clusters.

The greatest difference between the algorithms is their training time. Notice that MacQueen’s algorithm is consistently faster than either of the others. This is due to the algorithm updating its centroids more frequently than Lloyd’s algorithm, and having to recompute distances less often than the Hartigan-Wong algorithm. The Hartigan-Wong algorithm seems to be the most computationally intense at low cluster numbers, but overtakes Lloyd’s algorithm as the number of clusters increases beyond seven.

> **NOTE**
>
> The tuning process selected Lloyd’s algorithm, as its Davies-Bouldin index was slightly smaller than for the other algorithms. For very large datasets, computation speed may be more important to you than a performance increase this small, in which case you might prefer to select MacQueen’s algorithm due to its smaller training time.

![](img/a22105d68c35e8d5bd3c7bafb4644881_416_0.png)

*Figure 16.7* Plotting our tuning process. Each sub-plot shows the values of a different internal cluster metric. The different lines indicate the performance of each of the three different algorithms.

In this section, we’ll take our tuned hyperparameters, and use them to train our final clustering model. You’ll notice that I’m not going to use nested cross-validation to cross-validate the whole model-building process. While the k-means algorithm is able to predict cluster membership for new data, it isn’t typically used as a predictive technique. Instead, we might use k-means to help us better define classes in our dataset, that we can later build classification models to make predictions.

Let’s start by creating a k-means learner that uses our tuned hyperparameter values, using the `setHyperPars()` function. We then train this tuned model on our `gvhdTask` using the `train()` function, and use the `getLearnerModel()` function to extract the model data, so we can plot the clusters. Print the model data by calling `kMeansModelData`, and examine the output; there is a lot of useful information in the output. By extracting the `$iter` component of the object, we can see that it took only three iterations for the algorithm to converge (far fewer than `iter.max`).

```r
tunedKMeans <- setHyperPars(kMeans, par.vals = tunedK$x)
tunedKMeansModel <- train(tunedKMeans, gvhdTask)
kMeansModelData <- getLearnerModel(tunedKMeansModel)
```

```r
kMeansModelData$iter
```

```
[1] 3
```

Now, as finding the optimal number of clusters is not a well-defined problem, while internal metrics give us evidence as to the correct number of clusters, you should still always try to validate your cluster model visually, to understand whether the result you’re getting is sensible, at the very least. This may seem subjective, and it is, but it’s much better for you to use your expert judgment, than to rely solely on internal metrics. We can do this by plotting the data (like in figure 16.2), but coloring each case by its cluster membership.

> **TIP**
>
> If the correct number of clusters is difficult for you to determine, it could be there simply aren’t well-defined clusters in the data, or you may need to do further exploration, including generating more data. It may be worth trying a different clustering method, for example, one that doesn’t find spherical clusters like k-means does, or one which can exclude outliers (like DBSCAN that we’ll meet in chapter 18).

To do this, I first add the cluster membership of each case as a new column in our `gvhdTib` tibble, using the `mutate()` function. I extract the vector of cluster memberships from the `$cluster` component of the model data, and turn this into a factor using the `as.factor()` function, to ensure a discrete color scheme is applied during plotting.

I then use `ggpairs()` to plot all variables against each other, mapping `kMeansCluster` to the color aesthetic. I use the `upper` argument to plot density plots on plots above the diagonal, and apply the black and white theme.

```r
gvhdTib <- mutate(gvhdTib,
                  kMeansCluster = as.factor(kMeansModelData$cluster))

ggpairs(gvhdTib, aes(col = kMeansCluster),
        upper = list(continuous = "density")) +
    theme_bw()
```

The resulting plot from code listing 16.18 is shown in figure 16.8. By eye, it looks like our k-means model does a pretty good job of capturing the structure in the data overall. But look at the plot of CD8 vs CD4, cluster three appears to be split. This either suggests that we have underclustered our data, or that these cases have been assigned to the wrong cluster, or perhaps that they are simply outlying cases, the importance of which is overstated by the density plot.

**Listing 16.2 Predicting cluster membership of new data**

```r
newCell <- tibble(CD4 = 510,
                  CD8b = 26,
                  CD3 = 500,
                  CD8 = 122) %>%
  scale(center = attr(gvhdScaled, "scaled:center"),
        scale = attr(gvhdScaled, "scaled:scale")) %>%
  as_tibble()

predict(tunedKMeansModel, newdata = newCell)
```

```
Prediction: 1 observations
predict.type: response
threshold:
time: 0.01
  response
1       2
```

So we’ve learned how to apply k-means clustering to our data. In the next chapter, I’ll introduce you to *hierarchical clustering*, a set of clustering methods that help reveal a hierarchy in our data. I suggest you save your .R file, as we’re going to continue using the same dataset in the next chapter. This is so we can compare the performance of k-means and hierarchical clustering on the same dataset.

## 16.3 Strengths and weaknesses of k-means clustering

While it often isn’t easy to tell which algorithms will perform well for a given task, here are some strengths and weaknesses that will help you decide whether the k-means clustering will perform well for your task.

The strengths of k-means clustering are:

- Cases can move between clusters at each iteration until a stable result is found.
- It may be faster to compute than other algorithms when there are many variables.
- It is quite simple to implement.

The weaknesses of k-means clustering are:

- It cannot natively handle categorical variables. This is because calculating the Euclidean distance on a categorical feature space isn’t meaningful.
- It cannot select the optimal number of clusters.
- It is sensitive to data on different scales.
- Due to the randomness of the initial centroids, clusters may vary slightly between runs.
- It is sensitive to outliers.
- It preferentially finds spherical clusters of equal diameter, even if the underlying data don’t fit this description.

## 16.5 Solutions to exercises

1. Increase the `iter.max` of our k-means learner to 200.

```r
kMeans <- makeLearner("cluster.kmeans",
                      par.vals = list(iter.max = 200, nstart = 10))

tunedK <- tuneParams(kMeans, task = gvhdTask,
                     resampling = kFold,
                     par.set = kMeansParamSpace,
                     control = gridSearch,
                     measures = list(db, dunn, G1))

# the error about not converging disappears when we set iter.max to 200
```

2. Use k-means to cluster the GvHD.pos dataset.

```r
gvhdPosTib <- as_tibble(GvHD.pos)

gvhdPosScaled <- scale(gvhdPosTib)

gvhdPosTask <- makeClusterTask(data = gvhdPosScaled)

tunedKPos <- tuneParams(kMeans, task = gvhdPosTask,
                        resampling = kFold,
                        par.set = kMeansParamSpace,
                        control = gridSearch,
                        measures = list(db, dunn, G1))

kMeansTuningDataPos <- generateHyperParsEffectData(tunedKPos)

gatheredTuningDataPos <- gather(kMeansTuningDataPos$data,
                                key = "Metric",
                                value = "Value",
                                c(-centers, -iteration, -algorithm))

ggplot(gatheredTuningDataPos, aes(centers, Value, col = algorithm)) +
  facet_wrap(~ Metric, scales = "free_y") +
  geom_line() +
  geom_point() +
  theme_bw()

tunedKMeansPos <- setHyperPars(kMeans, par.vals = list("centers" = 4))

tunedKMeansModelPos <- train(tunedKMeansPos, gvhdPosTask)

kMeansModelDataPos <- getLearnerModel(tunedKMeansModelPos)

mutate(gvhdPosTib,
       kMeansCluster = as.factor(kMeansModelDataPos$cluster)) %>%
  ggpairs(mapping = aes(col = kMeansCluster),
          upper = list(continuous = "density")) +
  theme_bw()

# the optimal number of clusters is less clear than for GvHD.control
```
