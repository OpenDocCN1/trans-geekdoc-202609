Now we can visualize our dataset using the scatter plot

```
In [5]: X1 = X[:, 0]
X2 = X[:, 1]
plt.scatter(X1,X2)
```

Out[5]: <matplotlib.collections.PathCollection object at 0x1043f478>

![](bbox=[0.237, 0.258, 0.818, 0.503])

As you can see we have the datapoints concentrated in two places or formed 2 clusters. We can draw lines to separate them like:

![](bbox=[0.237, 0.617, 0.818, 0.862])

Using numpy to create the line and matplotlib to plot the lines in the graph we can visualize the same