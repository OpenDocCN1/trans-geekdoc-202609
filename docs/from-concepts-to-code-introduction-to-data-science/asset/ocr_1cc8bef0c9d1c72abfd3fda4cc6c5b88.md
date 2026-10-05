The 25th percentile forms the bottom of the box (value: 4.45)

The minimum appears at bottom as a horizontal line (value: 2.91)

![](bbox=[0.338, 0.237, 0.662, 0.4])

FIGURE 11.6: Boxplot of Happiness Scores

A boxplot provides less detail than the histogram, but it can be easier to interpret. Additionally, several boxplots can be easily compared together.

```
sns.boxplot(data=df['Happiness score'], width=0.4)
```

Next, let's look at bivariate plots of the data to understand the relationships between the factors and the target. We create a scatter plot of happiness versus social support:

```
sns.scatterplot(xe='Explained by: Social support', ye='Happiness score', data=df)
```

![](bbox=[0.338, 0.656, 0.662, 0.806])

FIGURE 11.7: Happiness Scores versus Social Support