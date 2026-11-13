# 3.6 Exploring Data70

Once the data is visualized, we then turn gears to further explore this data. Our goal is to go past the above simple visualization tools and toward quantifying relationships71 between features, as well as features and the target. There are a few techniques that we can use to explore relationships.

# 3.6.1 Correlation-based and Information-based Methods

Let us start with Pearson’s correlation coefficient ($r_{xy}$).72 This coefficient measures the *linear*73 relationship between two numerical variables (say, x and y). This linear relationship is described in terms of strength and direction by:

```
$r_{xy} = \frac{\sum_{i=1}^n (X_i - \mu_X)(Y_i - \mu_Y)}{\sigma_X \sigma_Y}$ (3.1)
```

This coefficient has a range from −1.0 to +1.0. The larger the absolute value of the Pearson correlation coefficient, the stronger the linear relationship between the two variables. A value of zero indicates no linear relationship. Positive and negative values to this coefficient indicate a linear relationship with a positive and negative slope, respectively.74 For example, a Pearson correlation coefficient of +0.9 implies a positive correlation with a strength magnitude of 0.9.

This correlation can be calculated for any two variables as well as multiple variables. In the latter, the results can be fitted into a matrix. You can easily calculate Pearson’s correlation coefficient using Excel, as you can see in Figure 3.8.

Step 1: Select the data. Navigate to the *Data* tab and then pick *Data Analysis*75 and *Correlation*.

![](bbox=[0.106, 0.41, 0.826, 0.746])

70 In some sources, this step could be merged with visualizing the data. I chose to present this as a separate section since I believe *visualizing* the data is a *qualitative* exercise and *exploring* the data is a *quantitative* exercise.
71 For example, if a scatter chart indicates the presence of a linear relationship between a feature and the target, here we are trying to estimate how linear is this relationship.
72 Or simply, R (not to be confused with the programming language, R).
73 While this may seem self-explanatory, I am afraid that it can be overlooked. This coefficient assumes that the relationship is linear and quantifies such a relationship. This does not mean that the relationship is indeed linear, nor that there is a linear relationship at all. Further, this does not also mean that one of the variables causes the other (this may or may not be true). In reality, a good portion of relationships are likely to have some form of nonlinearity. Be careful when interpreting such coefficients. *Additional note*: we will re-visit this coefficient and its usefulness as a performance metric in Chapter 5.
74 Up to 0.19 can be considered a very weak correlation. 0.2–0.39 weak correlation. 0.4–0.59 moderate correlation. 0.6–0.79 strong correlation and 0.8–1.0 as a very strong correlation.
75 If you cannot access this tool, then you may add it from the *Analysis ToolPak* under the *Excel Add-ins* within the *Manage* feature in Excel’s *Options*.