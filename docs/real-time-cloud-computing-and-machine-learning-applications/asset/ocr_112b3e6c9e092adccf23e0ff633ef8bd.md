158 T. P. Fowder, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondonman

linear regression model may be modified by adding polynomial terms to obtain the polynomial regression model as follows [25]:

```
$y = eta_0 + \beta_1x + \beta_2x^2 + \beta_3x^3 + \dots + \beta_nx^k + \varepsilon \quad (3.15)$
```

Where,

+   - $y$ - Response variable
- $\beta_0$ - Y-intercept
- $k$ -Highest degree
- $\beta_1, \beta_2, \beta_3, \dots, \beta_n$ - Coefficients
- $x$ - Predictor variable
- $\varepsilon$ - Error

# Short-hand Example 5

In this example, the weight and the mileage of a set of six cars are related to each other using polynomial regression with a degree of two (quadratic). The recorded data is given in Table 3.11:

# Table 3.11. Polynomial regression- Recorded data

| Weight (Pounds), x | Mileage (Miles per Gallon), y |
|---|--|\||1835 | 26 |
| 1970 | 31 |
| 2372 | 24 |
| 3086 | 14 |
| 3504 | 18 |
| 4341 | 15 |

The regression line can be obtained using the least square method which solving a system of linear equations in the form $Ma = b$ as follows [29]:

```
$$\begin{bmatrix} \sum_{i=1}^{N} x_i & \sum_{i=1}^{N} x_i^2 & \dots & \sum_{i=1}^{N} x_i^k \ \sum_{i=1}^{N} 1 & \sum_{i=1}^{N} x_i & \dots & \sum_{i=1}^{N} x_i^k \ \vdots \ \sum_{i=1}^{N} x_i^k & \sum_{i=1}^{N} x_i^{k+1} & \dots & \sum_{i=1}^{N} x_i^{2k} \end{bmatrix} \begin{bmatrix} \beta_0 \ \beta_1 \ \vdots \ \beta_k \end{bmatrix} = \begin{bmatrix} y_i \ y_i \ \vdots \ y_i \end{bmatrix}$
```