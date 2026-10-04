# Table 7.11. Data for Polynomial Regression Model

| Time | Temperature |
|---|---|
| 1 | 26.06 |
| 2 | 26.06 |
| 3 | 25.76 |
| 4 | 25.76 |
| 5 | 24.69 |
| 6 | 24.39 |
| 7 | 23.63 |
| 8 | 24.7 |
| 9 | 26.37 |
| 10 | 27.43 |
| 11 | 28.79 |

```
$$\begin{pmatrix} T_{t(1)} & t_{(1)}^{1)} & t_{(1)}^{2)} & t_{(1)}^{3)} \ T_{t(2)} & t_{(2)}^{1)} & t_{(2)}^{2)} & t_{(2)}^{3)} \ T_{t(3)} & t_{(3)}^{1)} & t_{(3)}^{2)} & t_{(3)}^{3)} \ \vdots & \vdots & \vdots & \vdots \ T_{t(n)} & t_{(n)}^{1)} & t_{(n)}^{2)} & t_{(n)}^{3)} \end{pmatrix} \begin{pmatrix} \beta_1 \ \beta_2 \ \beta_3 \ \vdots \ \beta_n \end{pmatrix} + \begin{pmatrix} \varepsilon_1 \ \varepsilon_2 \ \varepsilon_3 \ \vdots \ \varepsilon_n \end{pmatrix} \quad (7.14)$
```

```
$$\begin{pmatrix} 26.06 & 1 & 1 & 8 \ 25.76 & 2 & 4 & 8 \ 25.76 & 3 & 9 & 27 \ 24.69 & 4 & 16 & 64 \ 24.39 & 5 & 25 & 125 \ 23.63 & 6 & 36 & 216 \ 24.70 & 7 & 49 & 343 \ 26.37 & 8 & 64 & 512 \ 27.43 & 9 & 81 & 729 \ 28.79 & 10 & 100 & 1000 \end{pmatrix} + \begin{pmatrix} \beta_1 \ \beta_2 \ \beta_3 \ \beta_4 \end{pmatrix} \quad (7.15)$
```

+   2. Solve for the OLS solution using QR-Decomposition

After reshaping the data into the required form, the regression coefficient can be solved using Apache Math OLSMultipleRegression class. This class implements ordinary least squares (OLS) to estimate the parameters of a multiple linear regression model. To solve for the regression coefficients using Equation (7.4), first the QR decomposition of the design matrix $\mathbf{X}$ is calculated. The QR-Decomposition is shown in equation (7.16).