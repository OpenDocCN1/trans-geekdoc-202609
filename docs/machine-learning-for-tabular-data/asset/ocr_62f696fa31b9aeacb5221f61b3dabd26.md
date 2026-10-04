![](bbox=[0.195, 0.08, 0.671, 0.365])

**Figure 7.9** Boxplot of winsorized number_of_reviews

Having completed checking and remediating for missing values and extreme values in our dataset of predictors, we can proceed in the next subsection to look at the target itself.

#  7.1.6 Exploring your target

When dealing with exploratory data analysis (EDA), it is critical to examine the predictors and the target, and sometimes both predictors and target together and how they relate to each other. For our example, by a regression problem, we simply start by figuring out the mean and the range of the target:

```
print(f'minimum: {y.min()()}')
print(f'average: {y.mean().round(2)}')
print(f'maximum: {y.max()()}')
```

These commands will print the minimum, the average, and the maximum values in the target variable y:

+   minimum: 1450.0
average: 36573.1
maximum: 1306500.0

We immediately notice that the maximum is on a quite different scale than the average and the minimum. Estimating percentiles can be helpful to understand better if there is a problem with extreme values or skewed distribution in the target. The presence of extreme values can be better understood by requiring a range of percentiles focusing on the extremities of the distribution: