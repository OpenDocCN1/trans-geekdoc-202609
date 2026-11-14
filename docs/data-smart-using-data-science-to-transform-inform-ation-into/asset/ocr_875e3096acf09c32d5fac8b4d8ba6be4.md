# WAIT . . THE FEMALE VARIABLE ISN'T STATISTICALLY SIGNIFICANT?

This fact should give you pause. We’re dealing with pregnancy after all. So what do you think is happening in this case? It’s because “Female” is already encoded in the Male column, when the result is 0. That makes “not male” the statistically significant driver.

| | Male | Female | Home | Apt | Pregnancy Test | Birth Control | Feminine Hygiene | Folic Acid | Prenatal Vitamins | Pregnancy Yoga | Body Pillow | Ginger Ale | Sea Bands | Stopped Smoking Eligibility | Cigarettes | Smoking Cessation | Stopped Smoking during wife | Wine | Maternity Clothes | Intercept |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Coefficients | -0.098 | -0.027 | -0.028 | -0.013 | 0.216 | -0.274 | -0.238 | 0.046 | 0.294 | 0.325 | 0.194 | 0.190 | 0.146 | 0.161 | -0.159 | 0.165 | 0.188 | -0.027 | 0.240 | 0.484 |
| Standard Error | 0.041 | 0.040 | 0.043 | 0.043 | 0.046 | 0.035 | 0.054 | 0.059 | 0.036 | 0.089 | 0.089 | 0.047 | 0.070 | 0.042 | 0.040 | 0.052 | 0.036 | 0.037 | 0.016 | 0.055 |
| t Statistic | 2.390 | 0.665 | 0.652 | 0.307 | 4.654 | 7.874 | 5.939 | 0.827 | 8.160 | 3.645 | 2.166 | 4.082 | 2.088 | 3.850 | 3.942 | 3.192 | 5.231 | 5.662 | 6.715 | 8.752 |
| P-value | 0.017 | 0.506 | 0.515 | 0.759 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.031 | 0.011 | 0.037 | 0.000 | 0.000 | 0.001 | 0.000 | 0.000 | 0.000 | 0.000 |

Figure 6.21: Female, Home, and Apt are insignificant predictors according to the t-test.

# Making Predictions on Some New Data and Measuring Performance

That last section was all statistics. Lab work you could say. It’s the part that always sounds fun on paper but gets complicated once you dig in. But now it’s time to take this model to the racetrack and have some fun!

How do you know your linear model actually will predict well in the real world? After all, your training set does not encapsulate every possible customer record, and your coefficients have been purpose-built to fit the training set (although if you’ve done your job right, the training set, very nearly, resembles the world at large).

To get a better sense of how the model will perform in the real world, you should run some customers through the model that were not used in the training process. You’ll see this separate set of examples used for testing a model often called a validation set, test set, or holdout set.

To assemble your test set, you can just return to the customer database and select another set of data from random customers (paying special attention to not pull the same customers used in training). Now, as noted earlier, 6 percent of RetailMart’s customers are pregnant, so if you randomly selected 1,000 customers from the database, roughly 60 of them would be pregnant.

While you oversampled the pregnant class in training the model, for testing you’ll leave the ratio of pregnant households at 6 percent so that our measurements of the precision of the model are accurate for how the model would perform in a live setting.