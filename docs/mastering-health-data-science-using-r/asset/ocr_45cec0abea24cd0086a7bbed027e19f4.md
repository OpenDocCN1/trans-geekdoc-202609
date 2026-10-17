# ### 15.3 Best Subset

The second package we introduce in this chapter is one that allows us to fit models with an L0 penalty term. The package **L0learn** considers penalties of the following forms.

+   - L0 only: λ‖β‖₀
+   - L0L1: λ‖β‖₀ + γ‖β‖₁
+   - L0L2: λ‖β‖₀ + γ‖β‖₂²

To fit a model with an L0 penalty term, we use the `L0learn.fit()` function. Similar to `glmnet()`, we need to specify our input matrix x and response vector y as well as our penalty using the `penalty` argument. We can also specify a number of λ values to consider `nLambda` and specify the family through the loss function `loss`.

```
```r
mod_l0 <- L0learn.fit(x, y, penalty = "L0", loss = "SquaredError",
                     nLambda = 20)
```
```

Plotting the returned object also shows how the coefficients for each variable change with the penalty term, given by the support size or number of non-zero coefficients in this case. We can also print the returned object to see the different values of λ used and the corresponding number of included variables.

```
```r
plot(mod_l0)
```
```