# 8.2.2 Univariate feature selection

# Pearson's correlation coefficient

Pearson's correlation coefficient measures the strength of the linear relationship between two variables. If there is a strong linear relationship, the correlation coefficient is close to 1 or -1, and 0 means no linear relationship. In the case of univariate feature selection, these variables are the feature x<sub>i</sub> and the target value y.

In 8.6 we generated five features with different levels of noise and nonlinearity, but the feature 0 has significantly more noise than the feature 1, and consequently lower correlation coefficient C. The feature 2 has the same amount of noise as the feature 1 but is slightly nonlinear. In this case the correlation coefficient is still high, though lower than for the feature 1. The feature 3 is highly nonlinear and not unique (e.g., there in this case the correlation coefficient is close to 0). Finally, the feature 4 is only noisy, resulting in C=0.

| Noisy linear (0) | Linear (1) | Non-linear (2) | Not unique (3) | Noise (4) |
|---|---|---|---|---||
| C=0.7 MI=0.55 | C=0.98 MI=1.65 | C=0.89 MI=1.06 | C=0.09 MI=1.38 | C=-0.0 MI=0.0 |

> Figure 8.6 Simulated features with various levels of nonlinearity and noise. The correlation (C) and mutual information (MI) between each feature and the target value is given. High values are highlighted in red.

Scikit-learn implements feature selection using the F-value, which is closely related to Pearson's correlation coefficient. The F-value is a statistic that measures whether the slope of the univariate linear regression is different from zero. It is positive for positive and negative linear relationships. The F-value can be calculated in scikit-learn using the function f_regression. The features with the highest F-values can be selected using a selector SelectKBest:

The selector that we created selects three features that are highly correlated with the target values. It is a transformer object, and we can fit it and transform the feature matrix using fit_transform:

```
X_selected = selector.fit_transform(X, y)
```

We can access the indices of the selected features using