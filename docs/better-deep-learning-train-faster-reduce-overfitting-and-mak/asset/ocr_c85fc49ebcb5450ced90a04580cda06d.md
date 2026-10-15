```
# scatter plot for points with a different color
pyplot.scatter(X[row_ix, 0], X[row_ix, 1])
# show plot
pyplot.show()
```

Listing 2.8: Example of plotting samples from the blobs problem.

Running the example creates a scatter plot of the entire dataset. We can see that the chosen standard deviation of 2.0 means that the classes are not linearly separable (separable by a line), causing many ambiguous points. This is desirable as it means that the problem is non-trivial and will allow a neural network model to find many different good enough candidate solutions.

![](bbox=[0.16, 0.33, 0.8, 0.66])

Figure 2.1: Scatter Plot of Blobs Dataset With Three Classes and Points Colored by Class Value.

In order to explore model capacity, we need more complexity in the problem than three classes and two variables. For the purposes of the following experiments, we will use 100 input features and 20 classes; for example:

```
...
# generate 2d classification dataset
X, y = make_blobs(n_samples=1000, centers=20, n_features=100, cluster_std=2, random_state=2)
```

Listing 2.9: Example of creating a large number of samples for the blobs problem.