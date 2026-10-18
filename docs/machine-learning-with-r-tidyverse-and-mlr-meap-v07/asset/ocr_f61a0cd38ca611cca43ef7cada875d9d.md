In this section, I'm going to show you what mixture model clustering is, and how it uses an algorithm called expectation-maximization to iteratively improve the fit of the clustering model.

The clustering algorithms we've met so far are all considered hard clustering methods. This is because each case is assigned wholly to one cluster, and not to another. One of the strengths of mixture model clustering is that it is a soft clustering method. This is because mixture model clustering fits a set of probabilistic models to the data and assigns each case a probability of belonging to each model. This allows us to quantify the probability of each case, belonging to each cluster. In this way, we say "this case has 90% probability of belonging to cluster A, 9% probability of belonging to cluster B, and 1% probability of belonging to cluster C." This is useful because it gives us the information we need to make better decisions. Say, for example, a case has 51% probability of belonging to one cluster, and 49% probability of belonging to the other, how happy are we to include this case in its most probable cluster? Perhaps we're not confident enough to include such cases in our final clustering model.

> NOTE Mixture model clustering doesn't, in of itself, identify outlying cases like DBSCAN and OPTICS do, but we can manually set a cut-off of probability if we like. For example, we could say that any case which has less than 60% probability of belonging to its most probable cluster should be considered an outlier.

So mixture model clustering fits a set of probabilistic models to the data. These models can be a variety of probability distributions, but are most commonly Gaussian (or normal) distributions. This clustering approach is called mixture modeling, because we fit multiple (a mixture of) probability distributions to the data. Therefore, a Gaussian mixture model is simply a model that fits multiple Gaussian distributions to a set of data.

Each Gaussian in the mixture represents a potential cluster. Once our mixture of Gaussians fits the data as well as possible, we can calculate the probability of each case belonging to each cluster, and assign them to the most probable cluster. But how do we find a mixture of Gaussians that fits the underlying data well? We can use the expectation-maximization (EM) algorithm.



In this section I'll take you through some prerequisite knowledge you'll need to know, in order to understand the EM algorithm. This focuses on how the algorithm calculates the probability that each case comes from each Gaussian.

Imagine we have a one-dimensional data set, a number line with cases distributed across it (see the top panel of figure 19.1). First, we must pre-define the number of clusters to look for in the