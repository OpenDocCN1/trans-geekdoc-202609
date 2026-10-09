regression model is then

log(sales) = $\alpha+\beta \log(price)+\varepsilon$.            (2.10)

This says that, regardless of brand, log sales increase by $\beta$ for every unit increase in log price.

Conveniently, log-log models have a much more intuitive interpretation: sales increase by $\beta$% for every 1% increase in price. To see this, write $y=\exp [\alpha+\beta \log(x)+\varepsilon]$ and differentiate against $x$:

$\frac{d y}{d x}=\frac{\beta}{x} e^{\alpha+\beta \log(x)+\varepsilon} \Longrightarrow \beta=\frac{d y / y}{d x / x}$.             (2.11)

Here, $\beta$ is the proportional change in $y$ over the proportional change in $x$. In economics there is a special name for such $\beta$: elasticity. The concept of elasticity will play an important role in many of our analyses.

If you take a look at the right panel of Figure 2.3, it seems clear that the three brands have log-log sales-price distributions that are concentrated around three separate lines. If you suspect that each brand has the same $\beta$ elasticity but a different intercept $\alpha$ then you would use a slightly more complex model:

log(sales) $=\alpha_{b r a n d}+\beta \log(price)+\varepsilon$.           (2.12)

Here, $\alpha_{b r a n d}$ is shorthand for a separate indicator for each OJ brand, which we could write out more fully as

$\boldsymbol{\alpha}_{b r a n d}=\boldsymbol{\alpha}_{d} \mathbb{I}_{\left[b r a n d=d o m i n i c k s\right]}+\boldsymbol{\alpha}_{m} \mathbb{I}_{\left[b r a n d=m i n u t e m a i d\right]}+\boldsymbol{\alpha}_{t} \mathbb{I}_{\left[b r a n d=t r o p i c a n a\right]}$.

Hence, Equation 2.12 says even through all brand sales have the same elasticity to price, at the same price they will have different expected sales.

To run this regression in $\mathrm{R}$, we can use the glm command. 1 As mentioned earlier, glm stands for “generalized linear model,” and we will use it for linear and logistic regression. The command is straightforward to use: you give it a data frame with the data argument and provide a formula that defines your regression.

```
> reg <- glm(y ~ var1 + ... + varP, data=mydata)
```