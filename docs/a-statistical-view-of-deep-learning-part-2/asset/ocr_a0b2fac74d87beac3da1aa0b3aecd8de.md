# Neural network model

Key idea: think of a neural network as a multiple regression model with transformed predictors

Example: One-layer neural network model with \( K \) hidden nodes \( \sigma_1(x), \sigma_2(x), \dots, \sigma_K(x) \) and 3 predictors \( (x_1, x_2, x_3) \)

```
y = \beta_0 + \beta_1 \sigma_1(\alpha_{10} + \alpha_{11}x_1 + \alpha_{12}x_2 + \alpha_{13}x_3)
+ \beta_2 \sigma_2(\alpha_{20} + \alpha_{21}x_1 + \alpha_{22}x_2 + \alpha_{23}x_3)
+ \quad \dots
+ \beta_K \sigma_K(\alpha_{K0} + \alpha_{K1}x_1 + \alpha_{K2}x_2 + \alpha_{K3}x_3) \quad \text{function of } x
```