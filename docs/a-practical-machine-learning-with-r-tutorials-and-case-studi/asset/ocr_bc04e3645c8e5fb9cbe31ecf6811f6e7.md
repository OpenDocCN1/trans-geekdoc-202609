# 8 Logistic Regression — Handling Imbalanced Data

Now that you know odds are, we can show you what makes the Logistic function so special. We start with the Logistic function from Equation (8.2):

```
$p_{rob,yes,i} = \frac{1}{1 + e^{-(\eta_1 x_i + \beta_2)}}$
```

and take the reciprocal on both sides of the equation:

```
$p_{rob,yes,i} = 1 + e^{-(\eta_1 x_i + \beta_2)}$
```

Then we subtract 1 from both sides:

```
$\frac{1}{p_{rob,yes,i}} - 1 = e^{-(\eta_1 x_i + \beta_2)}$
```

When we consider that $-1 = \frac{p_{rob,yes,i}}$ and substitute $-1$ accordingly, we get (after simplification):

```
$\frac{1 - p_{rob,yes,i}}{p_{rob,yes,i}} = e^{-(\eta_1 x_i + \beta_2)}$
```

Now we take the reciprocal on both sides and get:

```
$\frac{p_{rob,yes,i}}{1 - p_{rob,yes,i}} = e^{\betabeta_1 x_i + \beta_2}$
```

According to Equation (8.6) in the yellow box above, $\frac{p_{rob,yes,i}}{1 - p_{rob,yes,i}} = O^{odds}_{yes,i}$. If we substitute accordingly, we get:

```
$O^{odds}_{yes,i} = e^{\beta_1 x_i + \beta_2}$  (8.7)
```

Equation (8.7) is the prediction equation for *odds* rather than *probabilities* in Equation (8.2).

But there is another benefit from all the transformations. We can show this when we take the logarithm on both sides of Equation (8.8), resulting in Equation (8.8):

```
$ln(O^{odds}_{yes,(n_i)}) = \betabeta_1 x_i + \beta_2$  (8.8)
```

The right-hand side of Equation (8.8) now shows a typical linear regression equation with one predictor variable. This allows us to interpret the coefficients, in our case $\beta_1$, in a familiar way: We can say if $x$ increases by one unit, the log odds on the left-hand side of Equation (8.8) increase by $\beta_1$ units.