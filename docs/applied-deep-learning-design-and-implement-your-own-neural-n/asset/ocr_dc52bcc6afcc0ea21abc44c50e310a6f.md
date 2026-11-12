Similarly,
$$
\frac{\partial L(W,B)}{\partial W_6} = \frac{1}{N} \sum_{i} x_2 * (a_1 - y_2)
$$
$$
= \frac{1}{N} * x_2 * (a_1 - y_2)
$$
$$
= \frac{1}{2} * 1 * (0.661 - 1)
$$
$$
= -0.1675
$$

$$
\frac{\partial L(W,B)}{\partial W_7} = \frac{1}{N} \sum_{i} x_1 * (a_2 - y_1)
$$
$$
= \frac{1}{N} * x_1 * (a_1 - y_1)
$$
$$
= \frac{1}{2} * 0 * (a_1 - y_1)
$$
$$
= 0
$$

$$
\frac{\partial L(W,B)}{\partial W_8} = \frac{1}{N} \sum_{i} x_2 * (a_2 - y_2)
$$
$$
= \frac{1}{2} * 1 * (0.65 - 1)
$$
$$
= -0.175
$$

Now, the updated weight can be given as follows:
$$
new_{weight} = old_{weight} - learning_{rate} * \Delta W
$$

Therefore,
$$
W_5 = W_5 - 0.1 * 0
$$
$$
W_5 = 0.3
$$

Similarly, we can find the remaining updated weights as shown in table 3.6:

| Weights | Updated weight value using gradient descent |
|---|---|
| $W_5$ | $W_5 = W_5 - learning_{rate} * \Delta W_5$
$= 0.3 - 0.1 * 0$
$= 0.3$ |