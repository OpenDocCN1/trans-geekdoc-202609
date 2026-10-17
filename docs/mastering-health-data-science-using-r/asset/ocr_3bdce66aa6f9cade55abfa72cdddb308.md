```
#> 13 1.75e-05 0 14
#> 14 4.06e-07 0 15
#> 15 3.94e-07 0 15
#> 16 3.03e-08 0 15
#> 17 5.87e-09 0 15
#> 18 9.43e-10 0 15
#> 19 3.48e-10 0 15
#> 20 2.19e-10 0 15
```

To extract the model for a particular value, we can use the coef() function and specify the λ and γ values to use.

```
coef_l0 <- coef(mod_l0, lambda = 1.75475e-03, gamma = 0)
```

Unfortunately, this output doesn't include variable names so we add them manually.

```
rownames(coef_l0) <- c("Intercept", colnames(x))
coef_l0
#> 16 x 1 sparse Matrix of class "dgCMatrix"
#>
#> Intercept 4.63847
#> AGE 0.00379
#> SEXFemale -0.03130
#> RACEOther Hispanic .
#> RACENon-Hispanic White .
#> RACENon-Hispanic Black 0.03753
#> RACEOther Race .
#> EDUCATIONHS .
#> EDUCATIONMoreThanHS .
#> INCOME -0.00535
#> SMOKEQuitSmoke .
#> SMOKESstillSmoke .
#> LEAD .
#> BMI_CAT25<BMI<30 .
#> BMI_CATBMI>=30 0.02760
#> ALCYes .
```

If instead we want to include a penalty with an L0 and L2 norm term, we can change our penalty argument to penalty = L0L2 and specify a number of γ values to test.