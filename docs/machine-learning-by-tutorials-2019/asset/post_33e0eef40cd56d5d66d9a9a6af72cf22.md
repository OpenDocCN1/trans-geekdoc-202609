
# A quick refresher

Logistic regression is a statistical model used in machine learning that tries to find a straight line between your data points that best separates the classes.

![](img/5720be5c3cca252e12448e68d25607b5_202_0.png)

Of course, this only works if these data points can be separated by a straight line, or by what is known as a hyperplane in higher dimensions.

Just to give you an idea of what is going on under the hood when you apply a logistic regression, let's dive into the math a little. It's OK if you're not a fan of math, free to just skim this and skip the bits that make your head spin. Knowing the math is not a prerequisite, but it can be helpful to understand what is going on — and it shows that these models are not really magical at all.

# Let’s talk math

In the illustration, data points are two dimensional: They have two coordinates, x[0] and x[1]. In most machine-learning literature and code, x is the name given to the training examples.

In practice, your data points will often be placed in much higher-dimensional spaces. Recall that for an image of size 227×227, the number of dimensions is over 150,000. But for the purpose of explanation, imagine that each data point is made up of two values.

Hopefully, you will still remember from high school math that the algebraic formula for a straight line is:

```
y = a*x + b
```

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

It's a little tricky to draw the value of y on top of a flat picture, but it looks something like this:

![](img/5720be5c3cca252e12448e68d25607b5_204_0.png)

# The values of y

Note that y is no longer on the vertical axis. In the above example, the vertical axis is used for x[1], the second coordinate of the data points. Since the data points use two coordinates, the formula is no longer the equation for a line but for a plane in a three-dimensional coordinate space. a[0] and a[1] are still slopes, but now of a plane instead of a simple line, and b is the height of this plane at the origin.

The data points from class A are in the area where y is negative and the data points from class B are in the area where y is positive. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

The coefficients a[0] and a[1] are parameters that the model learns, and the b is the bias. The decision boundary that separates the two classes is exactly where y = 0. The further away you go from the decision boundary, the larger the value of y (positive or negative).

# From linear to logistic

To turn the linear regression formula into a classifier, you extend the formula to make it a logistic regression:

```
probability = sigmoid(dot(a, x) + b)
```

The sigmoid function, also known as the logistic sigmoid, takes the decision boundary and looks at which side of the line point x is. The formula for sigmoid is:

```
sigmoid(x) = 1 / (1 + exp(-x))
```
