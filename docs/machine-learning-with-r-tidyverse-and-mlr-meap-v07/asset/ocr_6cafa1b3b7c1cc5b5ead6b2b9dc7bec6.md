# 19.2 Building our first Gaussian mixture model for clustering

In this section, I’ll show you how to build a Gaussian mixture model for clustering. We’ll continue using the swiss banknote dataset so you can compare the results to the DBSCAN and OPTICS clustering results. An immediate advantage of mixture model clustering over DBSCAN and OPTICS is that it is invariant to variables on different scales, and so there’s no need to scale our data first.

> **NOTE**
> 
> For correctness, I should say that there’s no need to scale our data as long as we make no prior specification of the covariances of the model components. It’s possible to specify our prior beliefs of the means and covariances of the components, though we won’t do that here. If we were to do this, it would be important the covariances consider the scale of the data.

The mlr package doesn’t have an implementation of the mixture modeling algorithm we’re going to use, so instead we’re going to use functions from the mclust package. Let’s start by loading this.

```
```r
library(mclust)
```
```

There are a few things I particularly like about using the mclust package for clustering. The first is that it’s the only R package I know of that prints a cool logo to the console when you load it. The second is that it displays a progress bar to indicate how much longer your clustering will take (very important for judging whether there’s time for a cup of tea). The third thing I like is that its function for fitting the model will automatically try a range of cluster numbers, and try to select the best fitting number. We can also manually specify the number of clusters if we think we know better.

Let’s use the `Mclust()` function to perform the clustering, then call `plot()` on the results. Plotting the `Mclust()` output does something a little odd (and irritating as far as I’m concerned). It prompts us to enter a number from one to four corresponding to one of the following options:

+   1. BIC
+   2. classification
+   3. uncertainty
+   4. density

Entering the number will draw the corresponding plot, each of which contains useful information. Let’s look at each of these plots in turn.