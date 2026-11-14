
| | Female | Male | Apartment | Home | Pregnancy Test | Birth Control | Feminine Hygiene | Folic Acid | Prenatal Vitamins | Pregnancy Yoga | Body Pillow | Ginger Ale | Sea Band | Swollen Tingly Breasts | Cigarette Cessation | Smoking Hotline | Maternity Clothes | Intercept |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Coefficient | -0.098 | -0.027 | -0.028 | -0.013 | 0.216 | -0.274 | -0.236 | 0.146 | 0.294 | 0.325 | 0.194 | 0.130 | 0.146 | 0.161 | -0.159 | 0.165 | 0.188 | -0.207 | 0.240 | 0.486 |
| Standard Error | 0.041 | 0.040 | 0.048 | 0.043 | 0.046 | 0.015 | 0.034 | 0.039 | 0.036 | 0.069 | 0.089 | 0.047 | 0.070 | 0.042 | 0.040 | 0.052 | 0.036 | 0.037 | 0.036 | 0.055 |

Figure 6.20: The coefficient standard error on the linear model

Phew! It's downhill from here. No more matrix math for the rest of the chapter. I swear.

Now you have everything you need to calculate each coefficient's t statistic (similar to the entire model's F statistic from the previous section). You will be performing what's called a two-tailed t-test, meaning that you'll be calculating the probability of obtaining a coefficient at least as large in either the positive or negative direction if in reality there's no relationship between the feature and the dependent variable.

The t statistic for the test can be calculated in row 5 as the absolute value of the coefficient normalized by the coefficient's standard error. For the Male feature this is as follows:

```
=ABS(C3/C4)
```

Drag this through column V to capture all the variables. Label row 5 then as t statistic.

The t-test can then be called by evaluating the t distribution at the value of the t statistic for your particular degrees of freedom value. Insert a new row here and then row 6 then as t Test p Value, and in C6 use the formula T.DIST.2T to calculate the probability of a coefficient at least this large given the null hypothesis.

```
=T.DIST.2T(C5, $AF$3)
```

The .2T in the function indicates we're performing the two-tailed t-test. Copying this formula across to all variables and applying conditional formatting to cells over 0.05 (5 percent probability), you can see which features are not statistically significant. While your results may vary based on the fit of your model, in the workbook shown in Figure 6.21, the Female (see side box), Home, and Apt columns are shown to be insignificant.

You could remove these features from your model and train again if you wanted.

Now that you've learned how to evaluate the model using statistical tests, let's change gears and look at measuring the model's performance by making actual predictions on a test set.

## WAIT... THE FEMALE VARIABLE ISN'T STATISTICALLY SIGNIFICANT?

This fact should give you pause. We’re dealing with pregnancy after all. So what do you think is happening in this case? It’s because “Female” is already encoded in the Male column, when the result is 0. That makes “not male” the statistically significant driver.

| | Male | Female | Home | Apt | Pregnancy Test | Birth Control | Feminine Hygiene | Folic Acid | Prenatal Vitamins | Pregnancy Yoga | Body Pillow | Ginger Ale | Sea Bands | Stopped Smoking Eligibility | Cigarettes | Smoking Cessation | Stopped Smoking during wife | Wine | Maternity Clothes | Intercept |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Coefficients | -0.098 | -0.027 | -0.028 | -0.013 | 0.216 | -0.274 | -0.238 | 0.046 | 0.294 | 0.325 | 0.194 | 0.190 | 0.146 | 0.161 | -0.159 | 0.165 | 0.188 | -0.027 | 0.240 | 0.484 |
| Standard Error | 0.041 | 0.040 | 0.043 | 0.043 | 0.046 | 0.035 | 0.054 | 0.059 | 0.036 | 0.089 | 0.089 | 0.047 | 0.070 | 0.042 | 0.040 | 0.052 | 0.036 | 0.037 | 0.016 | 0.055 |
| t Statistic | 2.390 | 0.665 | 0.652 | 0.307 | 4.654 | 7.874 | 5.939 | 0.827 | 8.160 | 3.645 | 2.166 | 4.082 | 2.088 | 3.850 | 3.942 | 3.192 | 5.231 | 5.662 | 6.715 | 8.752 |
| P-value | 0.017 | 0.506 | 0.515 | 0.759 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.031 | 0.011 | 0.037 | 0.000 | 0.000 | 0.001 | 0.000 | 0.000 | 0.000 | 0.000 |

Figure 6.21: Female, Home, and Apt are insignificant predictors according to the t-test.

## Making Predictions on Some New Data and Measuring Performance

That last section was all statistics. Lab work you could say. It’s the part that always sounds fun on paper but gets complicated once you dig in. But now it’s time to take this model to the racetrack and have some fun!

How do you know your linear model actually will predict well in the real world? After all, your training set does not encapsulate every possible customer record, and your coefficients have been purpose-built to fit the training set (although if you’ve done your job right, the training set, very nearly, resembles the world at large).

To get a better sense of how the model will perform in the real world, you should run some customers through the model that were not used in the training process. You’ll see this separate set of examples used for testing a model often called a validation set, test set, or holdout set.

To assemble your test set, you can just return to the customer database and select another set of data from random customers (paying special attention to not pull the same customers used in training). Now, as noted earlier, 6 percent of RetailMart’s customers are pregnant, so if you randomly selected 1,000 customers from the database, roughly 60 of them would be pregnant.

While you oversampled the pregnant class in training the model, for testing you’ll leave the ratio of pregnant households at 6 percent so that our measurements of the precision of the model are accurate for how the model would perform in a live setting.

In the RetailMart spreadsheet, you'll find a tab called Test Set (which contains a table eponymously named TestSet), populated with 1,000 rows of data identical to the training data. The first 60 customers are pregnant, while the other 940 are not (see Figure 6.22).

| Male | Female | Home | Apt | Pregnancy Test | Birth Control | Feminine Hygiene | Folic Acid | Prenatal Vitamins | Prenatal Yoga |
|---|---|---|---|---|---|---|---|---|---|
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 0 |
| 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 0 | 1 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 |
| 0 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 1 | 0 | 0 | 0 | 0 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 0 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | 0 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 1 |
| 0 | 0 | 0 | 1 | 0 | 0 | 0 | 0 | 1 | 0 |

Figure 6.22: Test set data

Just as you did on the Linear Model tab, run this new data through the model by taking a linear combination of customer data and coefficients, and adding in the intercept.
