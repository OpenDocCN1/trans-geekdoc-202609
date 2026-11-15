![](bbox=[0.2, 0.09, 0.75, 0.38])

# FIGURE 3.5 Backward propagation.

```
\frac{\partial y_p}{\partial W_4} = \alpha x_4
```

$W_3, x_4, x_3, b_3$ are considered constants while doing partial derivative with $W_4$. Similarly we can calculate gradient of error due to bias.

```
\frac{\partial y_p}{\partial b_3} = a
```

Let's consider example of pink neuron with bias $b_2$. Let's consider it is sending $z_2$ as input then:

```
\frac{\partial E}{\partial b_2} = \frac{\partial E}{\partial z_2} * \frac{\partial z_2}{\partial b_2}
```

$z_2$ can be considered as $x_5$ sent as input which implies

```
\frac{\partial z_2}{\partial b_2} = a
```

```
\frac{\partial E}{\partial x_5} = \frac{\partial \{y_p - y_a\}^2}{\partial x_5}
```

```
\frac{\partial \{y_p - y_a\}^2}{\partial x_5} = 2 * \{y_p - y_a\} * \frac{\partial y_p}{\partial x_5}
```