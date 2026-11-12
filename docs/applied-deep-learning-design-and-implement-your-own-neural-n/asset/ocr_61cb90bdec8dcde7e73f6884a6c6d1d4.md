![](bbox=[0.31, 0.1, 0.69, 0.36])

# Figure 3.16: Process of gradient descent

It is an iterative process that takes the minimization of the function (the global minima). The following formula shows the gradient descent to update the weight factor to achieve local /global minima.

```
w' = w - \eta * \frac{\partial L}{\partial w} (3.3)
```

Where,
w' is the updated weight factor,
'w' is the current weight factor,
"-" sign denotes subtraction,
"\eta", is the small step towards global minima, that is, the learning rate,
\frac{\partial L}{\partial w}, is the direction of the fastest increase (rate of change).

The idea of gradient descent is described as follows.

Let us take a machine learning model in which a group of data points is located in a 2D space. Also, consider that the information is associated with the weight and height of a cluster of students. We want to forecast the relationship among these variables such that we can forecast the height or weight of new students. This is a simple case of a supervised deep-learning method.

Now, draw a subjective line in the space which passes over some of the plotted data points. The equation for the straight line is written as follows:

```
Y = wX + b (3.4)
```