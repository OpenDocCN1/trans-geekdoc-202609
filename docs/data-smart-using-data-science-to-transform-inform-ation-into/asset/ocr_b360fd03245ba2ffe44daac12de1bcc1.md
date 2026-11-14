You now have the data in and the packages loaded. It's time to get model building! Start with a logistic regression.

```
> Pregnancy.lm <-glm(PREGNANT ~ .,data=PregnancyData,family=binomial("logit"))
```

The glm() function builds the linear model that you've specified as a logistic regression using the family=binomial("logit") option. You supply data to the function using the data=PregnancyData field.

Now, you're probably wondering what PREGNANT ~ . means. This is a formula in R. It means "train my model to predict the PREGNANT column using all the other columns." The ~ means "using," and the period means "all the other columns."

You can also specify a subset of columns as well by typing their column names.

```
Pregnancy.lm <-glm(PREGNANT ~ Implied.Gender + Home.Apt..PO.Box + Pregnancy.Test + Birth.Control, data=PregnancyData, family=binomial("logit"))
```

Once the linear model is built, you can view the coefficients and analyze which variables are statistically significant by summarizing the model.

```
> summary(Pregnancy.lm)
```

Call:
glm(formula = PREGNANT ~ ., family = binomial("logit"), data = PregnancyData)

Coefficients:

| Variable | Estimate | Std. Error | z value | Pr(>|z|) |
|---|---|---|---|---|
| (Intercept) | -0.343597 | 0.180755 | -1.901 | 0.057315 . |
| Implied.GenderM | -0.453880 | 0.197566 | -2.297 | 0.021599 * |
| Implied.GenderU | 0.141939 | 0.307588 | 0.461 | 0.644469 |
| Home.Apt..PO.BoxH | -0.172927 | 0.194591 | -0.889 | 0.374180 |
| Home.Apt..PO.BoxP | -0.002813 | 0.336432 | -0.008 | 0.993329 |
| Pregnancy.Test | 2.370554 | 0.521781 | 4.543 | 5.54e-06 *** |
| Birth.Control | -2.300272 | 0.365270 | -6.297 | 3.03e-10 *** |
| Feminine.Hygiene | -2.028558 | 0.342398 | -5.925 | 3.13e-09 *** |
| Folic.Acid | 4.077666 | 0.761888 | 5.352 | 8.70e-08 *** |
| Prenatal.Vitamins | 2.479469 | 0.369063 | 6.718 | 1.84e-11 *** |
| Prenatal.Yoga | 2.922974 | 1.146990 | 2.548 | 0.010822 * |
| Body.Pillow | 1.261037 | 0.860617 | 1.465 | 0.142847 |
| Ginger.Ale | 1.938502 | 0.426733 | 4.543 | 5.55e-06 *** |
| Sea.Bands | 1.107530 | 0.673435 | 1.645 | 0.100053 |
| Stopped.buying.ciggies | 1.302222 | 0.342347 | 3.804 | 0.000142 *** |
| Cigarettes | -1.443022 | 0.370120 | -3.899 | 9.67e-05 *** |
| Smoking.Cessation | 1.790779 | 0.512610 | 3.493 | 0.000477 *** |
| Stopped.buying.wine | 1.383888 | 0.305883 | 4.524 | 6.06e-06 *** |
| Wine | -1.565539 | 0.348910 | -4.487 | 7.23e-06 *** |
| Maternity.Clothes | 2.078202 | 0.329432 | 6.308 | 2.82e-10 *** |
| --- | | | | |
| Signif. codes: | 0 '***' | 0.001 '**' | 0.01 '*' | 0.05 '.' | 0.1 ' ' 1 |