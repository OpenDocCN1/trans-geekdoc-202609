# 6.7 Numerical Examples

**Fig. 6.17** Illustration of a single neuron with inputs $x_1$ and $x_2$ and output $\hat{y}$

![](bbox=[0.595, 0.095, 0.863, 0.206])

can be obtained, among others, by solving the least squares problem

```
$\min_{w_1, w_2, b \in \mathbb{R}}^4 (q(x_1w_1 + x_2w_2 + b) - y_i)^2. \quad (6.19)$
```

Here, $x_i$ (for $i=1, \dots, 4$) are the numbers from the first column of Table 6.7, $x_{ij}$ are the numbers from the second column, and $y_i$ are to be replaced by the numbers from the third column. There are special numerical methods for solving squares problems. We work with a quasi-Newton method known from unconstrained optimization. For this, we use the program `fminunc` of MATLAB R2021a. For the activation function $q := tanh$ and the starting point $(w_1, w_2, b) := (1,1,1)$, we get the minimal point $(\tilde{w}_1, \tilde{w}_2, \tilde{b}) := (-4.5504, -1.7752, 3.7752)$ and the minimal value $1.4132 - 10^{-25}$ of the objective function. Thus, we use the formula

```
$y \approx \tanh(-4.5504x_1 - 1.7752x_2 + 3.7752) \quad (6.20)$
```

to predict the gender $y$ as a function of the shifted body weight $x_1$ and the shifted body height $x_2$. This is not the only formula for predicting $y$. Another formula is obtained by choosing the softsign function $q$ in the least squares problem (6.19). Again, using the program `fminunc` of MATLAB R2021a and the starting point $(w_1, w_2, b) := (-4.55, -1.77, 3.77)$, we get the minimal point $(\tilde{w}_1, \tilde{w}_2, \tilde{b}) := (-55.543, -26.3397, 27.0645)$ and the minimal value $3.8838-10^{-5}$ of the objective function. In this case, a predictive formula for gender can be written as

```
$y \approx \frac{-55.543x_1 - 26.3397x_2 + 27.0645}{1 + |-55.543x_1 - 26.3397x_2 + 27.0645|}$
```

This formula is completely different from formula (6.20). However, it gives similarly good results for the data from Table 6.7.

Example 6.7 provides good results because one works with the data of only a few persons. If one were to look at the data of thousands of people, a single neuron would certainly not be sufficient. For this, one would then have to examine a more complex deep learning network. The next simple example gives an insight into this topic.