```
ks = make_knn_statistic(diabetes_ft rs[-1].reshape(1,-1))
compute_bootstrap_statistic(diabetes_dataset, 100, ks)
```

Out[9]:

74.00666666666667

Just like computing the mean will give us different answers depending on the exact dataset we use, the returned value from knn_statistic will depend on the data we pass into it.

We can mimic that process and turn it into our basic algorithm for bagging:

+   1. Sample the data with replacement.
+   2. Create a model and train it on that data.
+   3. Repeat.

To predict, we feed an example into each of the trained models and combine their predictions. The process, using decision trees as the component models, is shown in Figure 12.5.

![](bbox=[0.18, 0.5, 0.85, 0.85])

Figure 12.5 As with the bootstrapped mean, we sample the dataset and generate a decision tree from each subdataset. Every tree has a say in the final prediction.

Here's some pseudocode for a classification bagging system: