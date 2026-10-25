```
left <- node[node[[x]] >= xvals[i], y, drop = TRUE] # left child
right <- node[node[[x]] < xvals[i], y, drop = TRUE] # right child
p <- c(nrow(node), length(left), length(right)) / n # proportions
gain <- c(p[1L] * gini(node[[y]]) - # Equation (2.3)
          p[2L] * gini(left) - p[3L] * gini(right))
res[i, ] <- c(c(xvals[i], gain) # store split point and gain
}
res # return matrix of results
}
```

Let's test this function out on the full data set (i.e., A is the root node) and find the optimal split point for bottom. To start, we'll find the gain that is associated with each possible split point and plot the results:

```
res <- splits(bn, x = "bottom", y = "y", n = nrow(bn))
head(res, n = 5) # peek at first five rows
```

| | cutpoint | gain |
|---|---|---|
| [1,] | 7.25 | 0.00761 |
| [2,] | 7.35 | 0.01020 |
| [3,] | 7.45 | 0.01948 |
| [4,] | 7.55 | 0.03045 |
| [5,] | 7.65 | 0.03616 |

```
plot(res, type = "b", col = 2, las = 1,
     xlab = "Split value for bottom edge length (mm)",
     ylab = "Gain") # Figure 2.5
```

![](bbox=[0.18, 0.54, 0.88, 0.8])

FIGURE 2.5: Reduction to the root node impurity as a function of the split value c for the bottom edge length (mm).