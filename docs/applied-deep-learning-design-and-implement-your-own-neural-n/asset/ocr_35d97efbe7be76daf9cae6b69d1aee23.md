Activation function output at \( y_2(a_2) \):

```
\( y_2(a_2) = \frac{1}{1 + e^{-z4}} \)
\( = \frac{1}{1 + e^{-0.635}} \)
\( = 0.65 \)
```

# Loss calculation

The error is calculated as the difference between the predicted and actual output. Here, we have used the squared error loss function, which can be defined as follows:

```
\( L = -\frac{1}{N} \sum_i [y_i log(a_i) + (1 - y_i) log(1 - a_i)] \quad (3.38) \)
```

```
\( L = -0.5 [0 * log(0.661) + (1 - 0) * log(1 - 0.661)] - 0.5 [1 * log(0.65) \)
\( + (1 - 1) log(1 - 0.65)] \)
\( L = 0.23 + 0.09 \)
\( L = 0.32 \)
```

# Backpropagation of error

Weights and bias are the parameters of the loss function. The goal of parameter update is to minimize the value of the loss function to 0 by changing the values of weights and bias. Accordingly, what must be the value of W5 if L(W,B) tends to 0, which can be written in terms of the partial derivative as follows:

```
\( \frac{\partial L(W,B)}{\partial w_5} = \frac{\partial L(W,B)}{\partial a_1} * \frac{\partial a_1}{\partial z_3} * \frac{\partial z_2}{\partial w_5} \quad (3.39) \)
```

As we know that:

```
\( \frac{\partial L}{\partial w} = \frac{1}{N} \sum_i x_i * (a_i - y_i) \)
```

Therefore,

```
\( \frac{\partial L(W,B)}{\partial W_5} = \frac{1}{N} \sum_i x_1 * (a_1 - y_1) \)
\( = \frac{1}{N} * x_1 * (a_1 - y_1) \)
\( = \frac{1}{2} * 0 * (a_1 - y_1) \)
\( = 0 \)
```