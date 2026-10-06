# 250 Machine Learning: Concepts, Tools and Data Visualization

![](bbox=[0.136, 0.085, 0.862, 0.353])

**Figure 12-11** ToothGrowth histogram

Figure 12-12 shows a successful histogram having been drawn.

![](bbox=[0.136, 0.471, 0.862, 0.74])

**Figure 12-12** ToothGrowth histogram

Source (12-12)

```
# dataset <- data.frame(len, supp, dose)
# dataset <- unique(dataset)

hist(dataset$len, col = "blue", main = "Tooth length", xlab = "length")
```