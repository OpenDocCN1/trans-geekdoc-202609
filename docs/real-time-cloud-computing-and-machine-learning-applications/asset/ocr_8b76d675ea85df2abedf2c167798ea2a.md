# Machine Learning Algorithms

The linear system in this example is as follows:

```
$$\begin{bmatrix} 6 & 1.71 \times 10^4 & 5.35 \times 10^7 \ 1.71 \times 10^4 & 5.35 \times 10^7 & 1.81 \times 10^{11} \ 5.35 \times 10^7 & 1.81 \times 10^{11} & 6.54 \times 10^{14} \end{bmatrix} \eta_0 = \begin{bmatrix} 128 \ 3.37 \times 10^5 \ 9.79 \times 10^8 \end{bmatrix}$
```

Each of the coefficients may then be calculated using determinants as follows:

```
$$\beta_i = \frac{det(M_i)}{det(M)}$
```

Where, $M_i$ is built by replacing the $i^{th}$ column in matrix $M$ with the column vector $b$. In this, $M_0, M_1$ and $M_2$ are as follows:

```
$M_0 = \begin{bmatrix} 128 & 1.71 \ \times 10^4 & 5.35 \ \times 10^7 \ 3.37 \ \times 10^5 & 5.35 \ \times 10^7 & 1.81 \ \times 10^{11} \ 9.79 \ \times 10^8 & 1.81 \ \times 10^{11} & 6.54 \ \times 10^{14} \\end{bmatrix}$
$M_1 = \begin{bmatrix} 6 & 128 \ 1.71 \ \times 10^4 & 3.37 \ \times 10^5 & 5.35 \ \times 10^7 & 1.81 \ \times 10^{11} \ 5.35 \ \times 10^7 & 9.79 \ \times 10^8 & 6.54 \ \times 10^{14} \\end{bmatrix}$
$M_2 = \begin{bmatrix} 6 & 128 \ 1.71 \ \times 10^4 & 5.35 \ \times 10^7 & 3.37 \ \times 10^5 \ 5.35 \ \times 10^7 & 1.81 \ \times 10^{11} & 9.79 \ \times 10^8 \\end{bmatrix}$
```

Using the determinants of the above matrices, the coefficients are calculated as follows:

```
$$\beta_0 = \frac{det(M_0)}{det(M)} = \frac{7.68 \times 10^{21}}{1.77 \times 10^{20}} = 43.33$\n$\beta_1 = \frac{det(M_1)}{det(M)} = \frac{-1.73 \times 10^{18}}{1.77 \times 10^{20}} = -0.0098$\n$\beta_2 = \frac{det(M_2)}{det(M)} = \frac{1.16 \times 10^{14}}{1.77 \times 10^{20}} = 6.59 \times 10^{-7}$
```

Hence the polynomial model can be written as:

```
$y = 43.33 - 0.0098x + (6.59 \times 10^{-7})x^2$
```

The mileage of a car with 3000 pounds ($x=3000$) can be estimated as follows:

```
$Y = 43.33 - 0.0098(3000) + (6.59 \times 10^{-7})(3000)^2 = 19.86 \ MPG$
```