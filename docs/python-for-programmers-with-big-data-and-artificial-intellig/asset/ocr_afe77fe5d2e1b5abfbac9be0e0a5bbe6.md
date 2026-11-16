![](bbox=[0.18, 0.02, 0.94, 0.42])

# Visualizing the Reduced Data with Different Colors for Each Digit

Though the preceding diagram shows clusters, we do not know whether all the items in each cluster represent the same digit. If they do not, then the clusters are not helpful. Let's use the known targets in the Digits dataset to color all the dots so we can see whether these clusters indeed represent specific digits:

lick here to view code image

```
In [9]: dots = plt.scatter(reduced_data[:, 0], reduced_data[:, 1],
....: c=digits.target, cmap=plt.cm.get_cmap('nipy_spectral_r', 10))
....:
....:
```

In this case, scatter's keyword argument c=digits.target specifies that the target values determine the dot colors. We also added the keyword argument

lick here to view code image

```
cmap=plt.cm.get_cmap('nipy_spectral_r', 10)
```