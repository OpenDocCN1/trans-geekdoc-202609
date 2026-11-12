Figure 3.23 shows a single-layered artificial neural network:

| Parameters | Values |
| :--- | :--- |
| W1 | −0.2 |
| W2 | 0.1 |
| W3 | 0.5 |
| W4 | −0.2 |
| W5 | 0.3 |
| W6 | 0.5 |
| W7 | 0.4 |
| W8 | −0.1 |
| B1 | −0.2 |
| B2 | 0.2 |
| B3 | 0.3 |
| B4 | 0.3 |

# Table 3.4: Parameters and values

The input and output vectors are given as follows:

| I/O State | Value |
| :--- | :--- |
| X1 | 0 |
| X2 | 1 |
| y1 | 0 |
| y2 | 1 |

# Table 3.5: Input/output state and corresponding values

# Hidden layer calculations

Net input to the hidden neuron $h_1(\unknown_1)$ is given as follows:

```
$h_1(z_1) = x_1w_1 + x_2w_3 + B_1$

$= (-0.2) * 0 + (0.5) * 1 - 0.2$

$h_1(z_1) = 0.3$
```

Activation function output at $h_1(\sigma_1)$:

```
$h_1(\sigma_1) = \frac{1}{1 + e^{-z_1}}$
```