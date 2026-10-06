framework to promote learning and adaptation. The fuzzy inference applied in this study has four inputs and one output for Model 1 (M1), three inputs and one-output for Model 2 (M2). ANFIS architecture can be described by assuming that there are two inputs assigned as x and y. The two fuzzy if-then rules for a first-order Sugeno fuzzy model can be expressed as follows:

```
Rule 1: If ($x$ is $A_1$) and ($y$ is $B_1$), ($f_1 = p_1x + q_1y + r_1$), (10.8)
```

```
Rule 2: If ($x$ is $A_2$) and ($y$ is $B_2$), ($f_2 = p_2x + q_2y + r_2$), (10.9)
```

$A_i$ and $B_i$ are fuzzy sets, $f_i$ is the output, $p_i, q_i,$ and $r_i$ are the design parameters that are determined during the training process. The ANFIS architecture used to implement the two rules is shown below:

```
Layer 1: $Q_i^1 = \mu_{Ai}(x)$ for $i=1,2$ or $Q_i^1 = \mu_{Bi}(x)$ for $i=3,4$ (10.10)
```

```
Layer 2: $Q_i^2 = w_i \mu_{Ai}(x) \mu_{Bi}(y)$ for $i=1,2$ (10.11)
```

```
Layer 3: $Q_i^3 = \frac{W_i}{W_1 + W_2} i = 1,2$ (10.12)
```

```
Layer 4: $Q_i^4 = w_i(p_ix + q_iy + r_i) = ar{w}_i f_i$ (10.13)
```

$p_i, q_i,$ and $r_i$ are irregular parameters consequent parameters.

```
Layer 5: $Q_i^5 = w_i(p_ix + q_iy + r_i) = \frac{\sum w_i f_i}{\sum w_i}$ (10.14)
```

For the purpose of this study, the optimum hyperparameter tuning for developing the ANFIS model especially the membership functions (MF) (Gaussian, trapezoidal, sigmoid and triangular) was selected using trial-and-error techniques. The choice of the best training algorithms between backpropagation and hybrid learning algorithms was both employed for optimizing the parameters of the MFs; subsequently, hybrid emerged as the merit training algorithm. The error tuning was set to 0.005 and the iterations were between the range of 30 and 70 for both the training and testing phase.