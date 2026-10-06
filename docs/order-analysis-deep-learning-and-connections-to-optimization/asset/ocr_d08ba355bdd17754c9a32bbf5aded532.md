# 6.6 Gradient Methods

**Table 6.1** Iteration points of Example 6.2

| i | $x_1^i$ | $x_2^i$ | $\|
abla f(x_1^i, x_2^i)\|_2$ |
|---|---|---|--|
| 1 | 1.5965 | 0.8772 | 4.4934 |
| 2 | 2.4684 | -0.1217 | 1.3616 |
| 3 | 2.8508 | 0.0933 | 0.4778 |
| 4 | 2.9435 | -0.0226 | 0.1448 |
| 5 | 2.9841 | 0.0099 | 0.0508 |
| 6 | 2.9940 | -0.0024 | 0.0154 |
| 7 | 2.9983 | 0.0011 | 0.0054 |
| 8 | 2.9994 | -0.0003 | 0.0016 |
| 9 | 2.9998 | 0.0001 | 0.0006 |
| 10 | 2.9999 | -0.00003 | 0.0002 |

![](bbox=[0.218, 0.305, 0.782, 0.593])

90 degrees between the difference vectors $x^1 - x^0, x^2 - x^1$ etc. or in other words

$\lambda_0 d^0 \perp \lambda_1 d^1 \perp \lambda_2 d^2 \perp \lambda_3 d^3$

or simply written as

$d^0 \perp d^1 \perp d^2 \perp d^3$.

It will be shown that this is a general property of Algorithm 6.1. In the research literature, this behavior is also called zigzagging.

The zigzagging behavior shown in Fig. 6.8 is now proven analytically.

**Proposition 6.2** (Zigzagging Behavior of the Gradient Descent Method in Algorithm 6.1) Let the objective function $f : \mathbb{R}^n \to \mathbb{R}$ be differentiable, and let Algorithm 6.1 generate the iteration points $x^1, x^2, \dots$ For an arbitrary iteration