# 4.3 GLM, GAM AND MORE

| (Intercept) | s(temp).1 | s(temp).2 | s(temp).3 | s(temp).4 |
|---|---|---|---|--|
| 1 | 0.93 | -0.14 | 0.21 | -0.83 |
| 1 | 0.83 | -0.27 | 0.27 | -0.72 |
| 1 | 1.32 | 0.71 | -0.39 | -1.63 |
| 1 | 1.32 | 0.70 | -0.38 | -1.61 |
| 1 | 1.29 | 0.58 | -0.26 | -1.47 |
| 1 | 1.32 | 0.68 | -0.36 | -1.59 |

tuned via cross-validation. Ignoring the penalty term, nonlinear modeling with splines is fancy feature engineering.

In the example where we are predicting the number of bicycles with a GAM using only the temperature, the model feature matrix looks like this:

Each row represents an individual instance from the data (one day). Each spline basis column contains the value of the spline basis function at the particular temperature values. The following figure shows how these spline basis functions look like:

![](bbox=[0.238, 0.463, 0.813, 0.766])

Figure 4.14: To smoothly model the temperature effect, we use 4 spline basis functions. Each temperature value is mapped to (here) 4 spline basis values. If an instance has a temperature of 30 °C, the value for the first spline basis feature is -1, for the second 0.7, for the third -0.8 and for the fourth 1.7.

The GAM assigns weights to each temperature spline basis feature: