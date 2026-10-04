468 T. P. Fowdur, L. Babooram, M.N-U-D-Ibn Nazir Rosun and M. Indoonundan

possible. This is known as the "regression line." Regression uses the least square regression approach for fitting a regression line based on a particular dataset. The slope obtained, as well as the y-intercept, can be used to determine the value of the dependent variable at any point on the line [15,16].

On the same wavelength, MLR is used to determine one dependent variable based on several independent variables. With the two devices registering parameters such as network speeds and the number of packets sent and received, the most appropriate prediction with respect to time is to use the download speed and the upload speed over the independent variables, to predict the number of packets received per second, the latter being the dependent variable.

The steps below demonstrate how the regression coefficients are obtained for both SLR and MLR before being used to compute the predicted value.

+   1. For a set of values with a window size of W and prediction time of N in seconds, the following equation is followed to perform simple regression analysis.

```
$Y_t = \beta_1 X_t + \beta_0$\quad (5.2)
```

Where:

+   - $Y_t$ is the dependent variable
- $X_t$ is the independent variable

With the above notation and $Y_{t+N}$ being the desired variable, the value of $X_t$ must first be found using the following equation, which relates $X_t$ and time, t.

```
$X_t = C_1t + C_0$\quad (5.3)
```

Thus,

```
$X_{t+N} = C_1(t + N) + C_0$\quad (5.4)
```

4. To obtain $Y_{t+N}$, Equation 5.2 is used in the form:

```
$Y_{t+N} = \beta_1 X_{t+N} + \beta_0$\quad (5.5)
```

5. Equation 5.6 shows how the variable P, to be predicted at a time N, where U represents another variable, in this case the "Upload Speed":

```
$P_{t+N} = \beta_0 + \beta_1 U_{t+N-1} + \beta_2 P_{t+N-1}$\quad (5.6)
```