# House prices in Seattle

![](bbox=[0.112, 0.131, 0.803, 0.442])

FIGURE 11.8: Interaction model with prediction.

Eyeballing, it seems the predicted log10_price seems to be around 5.75. Let’s now find the exact numerical value for the prediction using the equation of the regression line for the condition = 5 houses, being sure to log10() the square footage first.

```
2.45 + 1 * log10(1900)
```

[1] 5.73

This value is very close to our earlier visually made prediction of 5.75. But wait! Is our prediction for the price of this house $5.75? No, because we are using log10_price as our outcome variable! If we want a prediction in dollar units of price, we need to un-log this by taking a power of 10.

```
10^(2.45 + 1 * log10(1900))
```

[1] 535493

Our predicted price for this home of condition 5 and of size 1900 square feet is $535,493.