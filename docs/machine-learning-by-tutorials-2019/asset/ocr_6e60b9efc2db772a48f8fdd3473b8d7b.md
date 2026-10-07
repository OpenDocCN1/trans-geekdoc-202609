# Machine Learning Chapter 6: Taking Control of Training with Keras

Here, x is a coordinate in the first dimension, a is the slope of the line — how steep it is, also known as the coefficient — b is the y-intercept. You've probably seen this formula before. This is the formula that is learned by linear regression, which tries to find a line that fits best between the data points.

Logistic regression is a small modification of linear regression, so it makes sense that we look at the linear regression formula.

The above formula is for one-dimensional data, i.e., for data points that consist of a single x value. In the illustration above, the data points are two dimensional and therefore have two values, x[0] and x[1]. You can easily extend the line formula to the following:

```
y = a[0]*x[0] + a[1]*x[1] + b
```

In general, y is the name for the predictions made by the model, as well as the labels that the model is trained on.

Since there are two values in each data point, there are also two coefficients or slopes, a[0] and a[1]. Here, a[0] is the slope of the line for the data point's first coordinate, x[0]. In other words, a[0] is how much y increases as x[0] becomes larger.

Likewise, a[1] is the slope for the second coordinate, or how much y increases as x[1] becomes larger.

The b is still the y-intercept — the value of y at the origin of the coordinate system — although in machine learning it is called the bias. This is the value of y when both x[0] and x[1] are 0.