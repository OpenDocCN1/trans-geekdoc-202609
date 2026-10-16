```
```python
sns.pairplot(diabetes_df[['age', 'sex', 'bmi', 'bp', 's1']],
    size=1.5, hue='sex', plot_kws={'alpha':.2});
```
```

![](bbox=[0.17, 0.24, 0.88, 0.6])

# 4.2 Nearest-Neighbors Regression and Summary Statistics

We discussed nearest-neighbor classification in the previous chapter and we came up with the following sequence of steps:

+   1. Describe similarity between pairs of examples.
+   2. Pick several of the most-similar examples.
+   3. Combine the picked examples into a single answer.

As we shift our focus from predicting a class or category to predicting a numerical value, steps 1 and 2 can stay the same. Everything that we said about them still applies. However, when we get to step 3, we have to make adjustments. Instead of simply voting for candidate answers, we now need to take into account the quantities represented by the outputs. To do this, we need to combine the numerical values into a single, representative answer. Fortunately, there are several handy techniques for calculating a single summary value from a set of values. Values computed from a set of data are called statistics. If we are trying to represent—to summarize, if you will—the overall dataset with one of these, we call it a summary statistic. Let's turn our attention to two of these: the median and the mean.