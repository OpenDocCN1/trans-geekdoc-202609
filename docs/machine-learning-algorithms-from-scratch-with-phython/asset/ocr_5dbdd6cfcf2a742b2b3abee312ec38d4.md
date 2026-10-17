```
return yhat
dataset = [[1, 1], [2, 3], [4, 3], [3, 2], [5, 5]]
coef = [0.4, 0.8]
for row in dataset:
    yhat = predict(row, coef)
    print("Expected=%.3f, Predicted=%.3f %%" % (row[-1], yhat))
```

Listing 8.3: Example of Making Predictions on the Contrived Dataset.

There is a single input value (x) and two coefficient values (b0 and b1). The prediction equation we have modeled for this problem is:

$y = b0 + b1 \times x$ (8.3)

Or, with the specific coefficient values we chose by hand as:

$y = 0.4 + 0.8 \times x$ (8.4)

Running this function we get predictions that are reasonably close to the expected output (y) values.

```
Expected=1.000, Predicted=1.200
Expected=3.000, Predicted=2.000
Expected=3.000, Predicted=3.600
Expected=2.000, Predicted=2.800
Expected=5.000, Predicted=4.400
```

Listing 8.4: Example Output of Predictions on Contrived Dataset.

Now we are ready to implement stochastic gradient descent to optimize our coefficient values.

# 8.2.2 Estimating Coefficients

We can estimate the coefficient values for our training data using stochastic gradient descent. Stochastic gradient descent requires two parameters:

+   - Learning Rate: Used to limit the amount that each coefficient is corrected each time it is updated.
+   - Epochs: The number of times to run through the training data while updating the coefficients.

These, along with the training data will be the arguments to the function. There are 3 loops we need to perform in the function:

+   1. Loop over each epoch.
+   2. Loop over each row in the training data for an epoch.
+   3. Loop over each coefficient and update it for a row in an epoch.