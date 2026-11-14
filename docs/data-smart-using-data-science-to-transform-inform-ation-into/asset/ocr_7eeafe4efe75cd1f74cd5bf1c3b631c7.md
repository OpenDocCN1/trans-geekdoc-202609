On the Linear Model tab using formulas, you can link the Coefficient Standard Error values you just calculated to row 3. Figure 6.20 shows a formula link. You can also just copy and paste the values.

| | Female | Male | Apartment | Home | Pregnancy Test | Birth Control | Feminine Hygiene | Folic Acid | Prenatal Vitamins | Pregnancy Yoga | Body Pillow | Ginger Ale | Sea Band | Swollen Tingly Breasts | Cigarette Cessation | Smoking Hotline | Maternity Clothes | Intercept |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Coefficient | -0.098 | -0.027 | -0.028 | -0.013 | 0.216 | -0.274 | -0.236 | 0.146 | 0.294 | 0.325 | 0.194 | 0.130 | 0.146 | 0.161 | -0.159 | 0.165 | 0.188 | -0.207 | 0.240 | 0.486 |
| Standard Error | 0.041 | 0.040 | 0.048 | 0.043 | 0.046 | 0.015 | 0.034 | 0.039 | 0.036 | 0.069 | 0.089 | 0.047 | 0.070 | 0.042 | 0.040 | 0.052 | 0.036 | 0.037 | 0.036 | 0.055 |

# Figure 6.20: The coefficient standard error on the linear model

Phew! It's downhill from here. No more matrix math for the rest of the chapter. I swear.

Now you have everything you need to calculate each coefficient's t statistic (similar to the entire model's F statistic from the previous section). You will be performing what's called a two-tailed t-test, meaning that you'll be calculating the probability of obtaining a coefficient at least as large in either the positive or negative direction if in reality there's no relationship between the feature and the dependent variable.

The t statistic for the test can be calculated in row 5 as the absolute value of the coefficient normalized by the coefficient's standard error. For the Male feature this is as follows:

```
=ABS (C3 /C4)
```

Drag this through column V to capture all the variables. Label row 5 then as t statistic.

The t-test can then be called by evaluating the t distribution at the value of the t statistic for your particular degrees of freedom value. Insert a new row here and then row 6 then as t Test p Value, and in C6 use the formula T.DIST.2T to calculate the probability of a coefficient at least this large given the null hypothesis.

```
=T.DIST.2T (C5 , $AF$3)
```

The .2T in the function indicates we're performing the two-tailed t-test. Copying this formula across to all variables and applying conditional formatting to cells over 0.05 (5 percent probability), you can see which features are not statistically significant. While your results may vary based on the fit of your model, in the workbook shown in Figure 6.21, the Female (see side box), Home, and Apt columns are shown to be insignificant.

You could remove these features from your model and train again if you wanted.

Now that you've learned how to evaluate the model using statistical tests, let's change gears and look at measuring the model's performance by making actual predictions on a test set.