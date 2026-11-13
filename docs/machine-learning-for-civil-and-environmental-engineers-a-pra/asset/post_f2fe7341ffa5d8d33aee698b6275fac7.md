

Step 2: Visit the Summary to examine statistical insights of each variable tab and then navigate to the Charts tab.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_73_0.png)

Step 3: Select Histogram and plot a feature.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_73_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_74_0.png)

Step 4: You can select to color the histogram with the failure Mode.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_74_1.png)

Step 5: Change the chart type into Scatter. Select a feature to plot on the horizontal axis and plot the axial capacity on the vertical axis.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_75_0.png)

Step 6: Format your chart as you can see below. Notice the Size effect.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_75_1.png)

Step 7: You can repeat the plot for multiple cases.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_76_0.png)

Step 8: Please try other plots. A variety is provided below.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_76_1.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_77_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_77_1.png)

Note that you can update the Orientation and Bar Chart Type.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_78_0.png)

Note that you can select a Pie or Ring style.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_78_1.png)

## 3.6 Exploring Data70

Once the data is visualized, we then turn gears to further explore this data. Our goal is to go past the above simple visualization tools and toward quantifying relationships71 between features, as well as features and the target. There are a few techniques that we can use to explore relationships.

### 3.6.1 Correlation-based and Information-based Methods

Let us start with Pearson’s correlation coefficient ($r_{xy}$).72 This coefficient measures the *linear*73 relationship between two numerical variables (say, x and y). This linear relationship is described in terms of strength and direction by:

```
$r_{xy} = \frac{\sum_{i=1}^n (X_i - \mu_X)(Y_i - \mu_Y)}{\sigma_X \sigma_Y}$ (3.1)
```

This coefficient has a range from −1.0 to +1.0. The larger the absolute value of the Pearson correlation coefficient, the stronger the linear relationship between the two variables. A value of zero indicates no linear relationship. Positive and negative values to this coefficient indicate a linear relationship with a positive and negative slope, respectively.74 For example, a Pearson correlation coefficient of +0.9 implies a positive correlation with a strength magnitude of 0.9.

This correlation can be calculated for any two variables as well as multiple variables. In the latter, the results can be fitted into a matrix. You can easily calculate Pearson’s correlation coefficient using Excel, as you can see in Figure 3.8.

Step 1: Select the data. Navigate to the *Data* tab and then pick *Data Analysis*75 and *Correlation*.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_79_0.png)

70 In some sources, this step could be merged with visualizing the data. I chose to present this as a separate section since I believe *visualizing* the data is a *qualitative* exercise and *exploring* the data is a *quantitative* exercise.
71 For example, if a scatter chart indicates the presence of a linear relationship between a feature and the target, here we are trying to estimate how linear is this relationship.
72 Or simply, R (not to be confused with the programming language, R).
73 While this may seem self-explanatory, I am afraid that it can be overlooked. This coefficient assumes that the relationship is linear and quantifies such a relationship. This does not mean that the relationship is indeed linear, nor that there is a linear relationship at all. Further, this does not also mean that one of the variables causes the other (this may or may not be true). In reality, a good portion of relationships are likely to have some form of nonlinearity. Be careful when interpreting such coefficients. *Additional note*: we will re-visit this coefficient and its usefulness as a performance metric in Chapter 5.
74 Up to 0.19 can be considered a very weak correlation. 0.2–0.39 weak correlation. 0.4–0.59 moderate correlation. 0.6–0.79 strong correlation and 0.8–1.0 as a very strong correlation.
75 If you cannot access this tool, then you may add it from the *Analysis ToolPak* under the *Excel Add-ins* within the *Manage* feature in Excel’s *Options*.

Step 2: Choose the Input Range. Check the Labels in first row box. Choose a cell to Output the correlation matrix.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_80_0.png)

Figure 3.8 Correlation analysis using Excel.

The outcome of this analysis is listed in Table 3.3. As you can see, the diagonal of this table (matrix) is unity since the correlation of each variable with itself return 1.0. This matrix is also symmetric along its diagonal, and hence only one-half of this matrix is usually presented. Let us decode this matrix.

I would like to focus on the last row. This row lists the Pearson's correlation coefficients for all features against the target. To be more specific, this row lists the strength of the assumed linear relationship between all features against the target. As you can see, there is a very strong correlation (> +0.90) between the diameter and the axial capacity. This is followed by a moderate correlation between the tube thickness and the axial capacity. The correlation between the rest of the features and the axial capacity is weak.

Table 3.3 Results of Pearson's correlation analysis.

| Variable | Diameter (mm) | Tube thickness (mm) | Effective length (mm) | Yield strength (MPa) | Compressive strength of concrete (MPa) | Axial capacity (kN) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Diameter (mm) | 1.00 | | | | | |
| Tube thickness (mm) | 0.48 | 1.00 | | | | |
| Effective length (mm) | 0.20 | 0.22 | 1.00 | | | |
| Yield strength (MPa) | 0.07 | 0.24 | 0.08 | 1.00 | | |
| Compressive strength of concrete (MPa) | 0.00 | -0.02 | -0.15 | 0.03 | 1.00 | |
| Axial capacity (kN) | 0.91 | 0.55 | 0.11 | 0.15 | 0.13 | 1.00 |

76 This information is helpful as it tells us that the linear correlation is weak. However, domain knowledge and mechanics note that there is some form of strong relationship between these features and axial strength. If this was a purely data-based problem where these features represent data (without any physical essence), then we might be able to justify dropping the features with low correlation.

Once you have examined the last row, now is a good time to explore the correlation between the features themselves. As you can see, the linear correlation between the features varies between weak and moderate. There seems to be a negative correlation between tube thickness and effective length and the compressive strength of concrete. In all cases, please remember that correlation (in any strength or magnitude) may not imply causation.

You can use Exploratory77 to calculate and plot the Pearson correlation coefficient. Here is how:

Step 1: Navigate to the Analytics tab and then select Correlation.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_81_0.png)

Step 2: Select the features and target. Run the analysis.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_81_1.png)

Step 3: Visualize the results.

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_82_0.png)

![](img/23c6d1a5d7ecadcf23ddf7b48d3476fc_82_1.png)

Table 3.4 Results of Spearman's correlation analysis.

| Variable | Diameter (mm) | Tube thickness (mm) | Effective length (mm) | Yield strength (MPa) | Compressive strength of concrete (MPa) | Axial capacity (kN) |
|---|---|---|---|---|---|---|
| Diameter (mm) | 1.00 | | | | | |
| Tube thickness (mm) | 0.53 | 1.00 | | | | |
| Effective length (mm) | -0.07 | 0.01 | 1.00 | | | |
| Yield strength (MPa) | -0.40 | -0.04 | -0.20 | 1.00 | | |
| Compressive strength of concrete (MPa) | -0.35 | -0.55 | -0.63 | -0.25 | 1.00 | |
| Axial capacity (kN) | 0.57 | 0.57 | 0.24 | -0.34 | -0.24 | 1.00 |

Pearson correlation coefficient is a neat and simple technique; however, it is limited to describing linear relationships. To overcome this limitation, we can use other measures, such as Spearman’s rank correlation coefficient, which describes the _monotonic_<sup>78</sup> relationship between variables.

Similar to the Pearson correlation coefficient, Spearman’s coefficient (\(\rho_{xy}\)) also ranges from –1.0 to +1.0. A positive coefficient means that as one variable increases, the other tends to increase (and vice versa for a negative coefficient). Unfortunately, the procedure to calculate Spearman’s coefficient using _Excel_ is lengthy, and hence I am providing the outcome in Table 3.4. The formula to calculate this coefficient is:

```
\(\rho_{xy} = 1 - 6 \frac{\sum_{i=1}^n (\text{rank}(x_i) - \text{rank}(y_i))^2}{n(n^2 - 1)}\) (3.2)
```

where rank: ranking/ordering the data in ascending order.<sup>79</sup>

A look at Table 3.4 shows that the calculated coefficients are different from those in Table 3.3. However, it is clear that the diameter and tube thickness remain the largest two variables.

### 3.6.1.1 A Note on Pearson and Spearman Correlation Coefficients

It is worth noting to remember that Pearson correlation assumes features to be normally distributed and to satisfy homoscedasticity (i.e., equally distributed about the regression line). On the other hand, the Spearman correlation does not carry any assumptions with regard to the distribution of the data [1]. You can carry out a correlation analysis in _Python_ or _R_ using the following packages (`x.corr(y, method='spearman')` and `x.corr(y, method='spearman')`) and (`cor(x, y, "pearson")`, `cor(x, y, "spearman")`), respectively.

The third technique, that is independent of correlation, that we can use to explore the relationship within our dataset is that known as _mutual information_ (MI).<sup>80</sup> Mutual information measures the nonlinear relations between two variables of any type and tells us the amount of information<sup>81</sup> one variable reveals about another variable.<sup>82</sup> This measure ranges from 0 to \(\infty\) and does not depend on the functional form of the true relationship between variables. The mutual information between two variables can be calculated as:

78 Meaning that as one variable increases, the other variable either increases or decreases (not both). For example, data plotted in a pattern that resembles a happy or sad smile is not monotonic (nor linear). Data plotted in a pattern that resembles a straight lines at 45 degrees is monotonic (with strong linear correlation).
79 Additional notes: another difference between Pearson’s coefficient and Spearman’s coefficient is that the former works with raw data whereas the latter works with ranked data. Other forms of correlations include, Chatterjee correlation coefficient, etc.
80 In _Python_, from `sklearn.feature_selection import mutual_info_regression` (from `sklearn.feature_selection import mutual_info_classif` as `MIC`). In _R_, (`mutinformation(X, Y, method="emp"`) other “methods” can be found under [29]).
81 You can think of mutual information as the reduction in uncertainty about one variable given our knowledge of another variable. For example, there is a high mutual information between timber construction and corrosion; since timber is not known to corrode!
82 Mutual information between two discrete variables is calculated through their joint probabilities as estimated from the frequency of the number of observed samples in each combination of variable categories [30].
