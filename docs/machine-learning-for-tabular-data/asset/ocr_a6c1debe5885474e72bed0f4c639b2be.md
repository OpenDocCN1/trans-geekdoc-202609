![](bbox=[0.196, 0.098, 0.666, 0.319])

Figure 4.3 A histogram of the Price feature being more symmetrical after log transformation

![](bbox=[0.196, 0.423, 0.666, 0.673])

Figure 4.4 A boxplot of the Price feature after log transformation signaling the persistence of extreme values at both the tails of the distribution

Now the distribution, represented by both the new histogram and the boxplot, is more symmetric, though it is evident that there are outlying observations on both sides of the distribution. Since our aim is illustrative, we can ignore the original distribution and focus on a meaningful target. For instance, we can keep only the price values below 1,000 (see figure 4.5). In the following code snippet, we produce a histogram focused only on price values below 1,000:

```
data[["price\]][data.price <= 1000].hist(bins=20)
```