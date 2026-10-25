![](bbox=[0.329, 0.104, 0.719, 0.317])

Figure 3.4: Plot of hyperbolic tangent activation function in between −5 to +5.

and

$\sigma'(z) = (1 - \sigma(z)^2).$  \tag{3.4}

This function performs better than the sigmoid function when the output is a large negative number. This function can also map numbers between −1 to +1. A plot of hyperbolic function in the range of −5 to 5 is given in Fig. 3.4.

# 3.3.3 RECTIFIED LINEAR UNITS (RELU) ACTIVATION

The Rectified Linear Units, also known as ReLU activation, and its derivatives are defined by Equations (3.5) and (3.6), respectively:

$$\sigma(z) = \begin{cases} 0 & \text{for } z \le 0 \\ z & \text{for } z > 0 \end{cases}$$  \tag{3.5}

and

$$\sigma'(z) = \begin{cases} 0 & \text{for } z < 0 \\ 1 & \text{for } z \ge 0 \end{cases}$$  \tag{3.6}

The ReLu function updates parameters faster as its gradient calculation is simpler compared to other activations. A plot of ReLU function in the range of −1 and +1 is given in Fig. 3.5.

# 3.3.4 LEAKY RECTIFIED LINEAR UNITS (LEAKY RELU) ACTIVATION

The Leaky Rectified Linear Units, also known as Leaky ReLU, is a type of improved ReLU activation that doesn’t have 0 slopes for negative values. Leaky ReLU and its derivatives can be