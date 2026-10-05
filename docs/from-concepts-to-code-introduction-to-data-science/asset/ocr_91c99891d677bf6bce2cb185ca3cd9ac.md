# Loss Functions

```
mae = abs_error.mean()
if logging:
    print('error:', error)
    print('abs_error:', abs_error)
    print('mae:', mae)
return mae
```

Aside from variable names, the only meaningful difference is the line that computes the loss. Now let's see the output:

```
error: [-0.1 0.2 0.1]
abs_error: [0.1 0.2 0.1]
mae: 0.13333333333333333
0.13333333333333333
```

For this case, as the errors are fractions, MAE is larger than MSE. Let us compare squared error to absolute error loss across a range of errors. Figure 12.2 represents squared error with a solid curve and absolute error with a dotted curve. This confirms what was explained earlier: for fractional errors, absolute loss will be greater. Outside of this range, squared loss will dominate.

![](bbox=[0.265, 0.513, 0.735, 0.738])

Figure 12.2: Loss Functions: Squared Error versus Absolute Error

Next, let's turn to the binary classification task. Let $\hat{p}_i$ and $1-\hat{p}_i$ denote the predicted probability that observation $i$ has positive and negative label, respectively. The true label for this observation is $y_i$. The cross-entropy loss is defined as: