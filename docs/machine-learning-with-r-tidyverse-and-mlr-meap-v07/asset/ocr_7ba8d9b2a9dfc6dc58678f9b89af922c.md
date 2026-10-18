Let's remind ourselves what the L2 norm looks like in equation 11.3. Recall that we square the value of each of the slope parameters, and add them all up. We then multiply this L2 norm by lambda to get the penalty we add to the sum of squares loss function.



```
L2 norm = \sum_{j=1}^p \beta_j^2
```

The L1 norm is only slightly different to the L2 norm. Instead of squaring the parameter values, we take their absolute value instead, and then sum them. This is shown in equation 11.4 by the vertical lines around \(\beta_j\).



```
L1 norm = \sum_{j=1}^p |\beta_j|
```

We then create the loss function for LASSO (the L1-penalized loss function) in exactly the same way as we did for ridge regression: we multiply the L1 norm by lambda (which has exactly the same meaning), and add it to the sum of squares. The L1-penalized loss function is shown in equation 11.5. Notice the only difference between this equation and equation 11.2 is that we take the absolute value of the parameters before summing them, instead of squaring them. Say we had three slopes, one of which is negative: 2.2, -3.1, 0.8. The L1 norm of these three slopes would be 2.2 + 3.1 + 0.8 = 6.1.



```
loss function_L1 = \sum_{i=1}^n (y_i - \hat{y}_i) + \lambda \sum_{j=1}^p |\beta_j|
```

So I can already hear you thinking: "so what?", "what's the benefit/difference of using the L1 norm instead of the L2 norm?" Well, ridge regression can shrink parameter estimates towards zero, but they will never actually be zero (unless the OLS estimate is zero to begin with). So if you have a machine learning task where you believe all the variables should have some degree of