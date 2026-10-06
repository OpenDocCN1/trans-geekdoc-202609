# CHAPTER 4. EXPLORING AND VISUALIZING BEHAVIORAL DATA 126

ones like sitting or standing. With boxplots we can inspect one feature at a time. If you want to visualize the relationship between predictors, correlation plots can be used instead.
Correlation plots will be presented in the next subsection.

# 4.6 Correlation Plots

This type of plot allows us to look at relationships between pairs of variables. The most common type of relationship is the **Pearson correlation**. The Pearson correlation measures the degree of **linear** association between two variables. It takes values between −1 and 1. A correlation of 1 means that as one of the variables increases, the other one does too. A value of -1 means that as one of the variables increases, the other decreases. A value of 0 means that there is no association between variables. The Figure 4.4 shows several examples of correlation values. Note that the correlations of the examples at the bottom are all 0. Even though there are some noticeable patterns in some of the examples, their correlation is 0 because these relationships are not linear.

The Pearson correlation (denoted by $r$) between two variables $x$ and $y$ can be calculated as follows:

```
$r = \frac{\sum_{i=1}^{n}(x_i - \bar{x})(y_i - \bar{y})}{\sqrt{\sum_{i=1}^{n}(x_i - \bar{x})^2}\sqrt{\sum_{i=1}^{n}(y_i - \bar{y})^2}} (4.1)
```

The following code snippet uses the **corrplot** library to generate a correlation plot for the HOME TASKS dataset. Remember that this dataset contains two sets of features. One

![](bbox=[0.173, 0.622, 0.826, 0.866])

Figure 4.4: Pearson correlation examples. Source: wikipedia