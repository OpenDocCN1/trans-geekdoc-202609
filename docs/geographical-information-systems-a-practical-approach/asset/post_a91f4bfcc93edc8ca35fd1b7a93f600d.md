
squared vertical distances from individual points to the line is smaller than those to any other line, that is, \(\sum_{i=1}^n e_i^2\) is minimised (Figure 6.16), where:

```
e_i = y_i - \hat{y}_i
```

$y_i$ is the measured $y$ value of the $i$th observation, and $\hat{y}_i$ is its $y$ value estimated or predicted by the straight line; $e_i$ is termed the **residual**. The straight line is called the **least-squares regression line**, or simply regression line. The regression coefficient $a$ is the intercept of the line on the $y$-axis (the value of $y$ at the point where $x = 0$), and $b$ is the slope of the regression line. They are determined using the sample data as follow:

```
b = \frac{n \sum_{i=1}^n x_i y_i - (\sum_{i=1}^n x_i) (\sum_{i=1}^n y_i)}{n \sum_{i=1}^n x_i^2 - (\sum_{i=1}^n x_i)^2}
```

```
a = \frac{\sum_{i=1}^n y_i}{n} - \frac{b \sum_{i=1}^n x_i}{n}
```

Predicted by the regression line, \(\hat{y} = \bar{y}\) when \(x = \bar{x}\), where \(\bar{x}\) and \(\bar{y}\) are the mean of $x$ and $y$, respectively. This means that the point \((\bar{x}, \bar{y})\) is on the regression line. This is true for all linear regression problems. The variation in the observed values of the dependent variable $y$ has two components: the residual that is unexplained or unaccounted for by the independent variable $x$, and the deviation of the predicted $y$ value from \(\bar{y}\) that is explained by $x$, as illustrated in Figure 6.16. The fraction of the total variation in $y$ that is explained by the regression is called the **coefficient of determination**. It is calculated by:

```
r^2 = \frac{\sum_{i=1}^n (\hat{y}_i - \bar{y})^2}{\sum_{i=1}^n (y_i - \bar{y})^2}
```

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_329_0.png)

The value of \( r^2 \) is in the range between 0 and 1. A value of 0 indicates that none of the variation in \( y \) is explained by \( x \), while a value of 1 suggests that all the residuals are zero – that is, all the observed or sample points fall exactly on the regression line. A value of 0.82 would mean that 82 per cent of the variation in \( y \) is explained by \( x \), and the other \( 100 - 0.82 = 18 \) per cent of the variation is explained by other variables that are not accounted for in the regression model.

The spread of sample points about the regression line is measured by the **standard error** of estimate, which is defined as:

```
\( s_e = \sqrt{\frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{n - 2}} \) (6.35)
```

\( s_e \) may be interpreted as the magnitude of a typical residual. It can be used to compare different samples with respect to the extent to which the observed points are dispersed about their regression line. It can also be used to compare distributions which share the same least-squares regression line.

### 6.6.1.1 Significance Testing of Simple Regression

The reliability or statistical significance of the linear relationship represented by a regression equation and the estimated regression coefficients needs to be tested because they are likely to be influenced by sampling errors.

The reliability or overall significance of the regression equation is tested using the **_F_ test statistic**. The _F_ test is used to compare variations in two samples and test whether a disparity between the two sample variances has arisen by chance. Here it is used to test whether the regression equation can explain a significant portion of the variation in \( y \) with the null hypothesis \( H_0 \) that the fraction of the variation in \( y \) explained by \( x \) is 0. The variance in \( y \) explained by the regression, called the regression variance, is:

```
\( s^2_{\hat{y}} = \frac{\sum_{i=1}^n (\hat{y}_i - \overline{y})^2}{k} \) (6.36)
```

where \( k \) is the number of independent variables. For simple regression, \( k = 1 \). The variance in \( y \) unexplained by the regression, called the residual variance, is:

```
\( s^2_e = \frac{\sum_{i=1}^n (y_i - \hat{y}_i)^2}{n - k - 1} \) (6.37)
```

The test statistic \( F \) for regression is given by

```
\( F = \frac{s^2_{\hat{y}}}{s^2_e} \) (6.38)
```

When a large proportion of the total variance is associated with the regression variance, a high \( F \) ratio is obtained, indicating that the regression equation provides a good prediction or estimation of \( y \). Conversely, a large residual variance may result in a low \( F \), suggesting that the regression equation may be unreliable, as other variables unaccounted for in the equation may play an important part in explaining the variation of \( y \). Therefore, the magnitude of the \( F \) test statistic helps determine whether the amount of the variability in \( y \) accounted for by the regression equation is significant compared to that associated with the residuals or errors. Regression analysis tools in GIS provide the _p_-value for the calculated _F_ ratio. If the _p_-value is equal to or less than the significance level \(\alpha\), _H_0_ is rejected and the regression equation is significant overall. Thus, the _p_-value associated with the _F_ ratio is usually used as a measure of how well the regression equation fits the sample data.

The significance of the regression coefficients is tested using the _t_ test statistic. The null hypothesis _H_0_ is that the true value of the regression coefficient is zero. So if the _t_ test for _b_ fails to reject _H_0_, then the independent variable _x_ has no significant influence on the dependent variable _y_, and thus _x_ is not important in understanding _y_. If the _t_ test for _a_ fails to reject _H_0_, we could conclude that _a_ generated from the sample data is the result of chance or sampling error; therefore, the predicted _y_ value by the regression equation is not reliable. The standard errors of _a_ and _b_ are used to carry out a _t_ test. The mathematical formulae for calculating the _t_ test statistics for _a_ and _b_ can be found in Rogerson (2015). We can use _p_-values associated with the _t_ test scores to make a decision on whether or not to reject _H_0_.

## 6.6.2 Multiple Regression

Many geographical problems are of a multivariate nature. For example, the concentration of fungal toxin in nuts at growing sites is dependent on rainfall, temperature and wind speed; the intensity of rainfall is related to sea surface temperature, sea level pressure, wind speed and other environmental factors. **Multiple regression** offers an extension to simple regression for addressing multivariate problems. It establishes a linear relationship between a dependent variable _y_ and two or more independent variables (_x_<sub>_1_</sub>, _x_<sub>_2_</sub>, _x_<sub>_3_</sub>, ..., _x_<sub>_k_</sub>). The general form of a multiple regression equation is:

```
\(\hat{y} = a + b_1x_1 + b_2x_2 + ... + b_kx_k\) (6.39)
```

where _k_ is the number of independent variables, \(\hat{y}\) is the predicted value of the dependent variable _y_ and _a_ and \(b_i\) (\(i = 1, 2, ..., k\)) are the regression coefficients estimated from sample data. As with simple regression, the regression coefficients are found by minimising the sum of the squared residuals. How well the multiple regression fits the sample data is measured by the **multiple coefficient of determination**, _R_<sup>2</sup>, which is the ratio of the explained variation and total variation in _y_, conceptually identical to _r_<sup>2</sup> in simple regression. However, _R_<sup>2</sup> increases as more variables are included, whereas the best multiple regression equation does not necessarily use all the available variables. To address this flaw, _R_<sup>2</sup> is adjusted according to the number of independent variables and the sample size as follows:

```
\(adjusted\ R^2 = 1 - \frac{n-1}{n-k-1}(1-R^2)\) (6.40)
```

where _n_ is the sample size. _R_<sup>2</sup> and adjusted _R_<sup>2</sup> are interpreted in the same way as _r_<sup>2</sup>. _F_ and _t_ tests are also used to assess the statistical significance of the multiple regression equation and individual regression coefficients. The _p_-value is used to determine the statistical significance according to the significance level \(\alpha\).

Both simple regression and multiple regression assume that the data are numerical;
