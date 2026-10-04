# 710 T. P. Fowder, L. Babooram, M. N-U-D-Ibn Nasir Rosun and M. Indoonondon

| 26.06 | 89 | 26.06 |
| 25.76 | 89 | 26.06 |
| 25.76 | 83 | 25.76 |
| 24.69 | 88 | 25.76 |
| 24.39 | 82 | 24.39 |
| 23.63 | 88 | 23.63 |
| 24.70 | 88 | 24.70 |
| 26.37 | 94 | 26.37 |
| 27.43 | 88 | 27.43 |
| 28.79 | 88 | |
= (β₁ + ε₁+₂)/β₃ (7.10)

# 2. Solve for the OLS solution using QR-Decomposition

After reshaping the data into the required form, the regression coefficient can be solved using Apache Math OLSMultipleLinearRegression. This class implements ordinary least squares (OLS) to estimate the parameters of a linear regression model. To solve for the regression coefficients using Equation (7.4), the QR decomposition of the design matrix X is first calculated as given in equation (7.11).

| 89 | 26.06 |
| 89 | 26.06 |
| 83 | 25.76 |
| 89 | 25.76 |
| 88 | 24.69 |
| 88 | 24.39 |
| 88 | 23.63 |
| 94 | 24.70 |
| 88 | 26.37 |
| 88 | 27.43 |

| -0.316 | -0.0760 | -0.1876 |
| -0.316 | -0.0760 | -0.1876 |
| -0.316 | 0.0683 | 0.0338 |
| -0.316 | -0.0968 | -0.0968 |
| -0.316 | 0.0506 | 0.2498 |
| -0.316 | 0.0506 | 0.3040 |
| -0.316 | -0.0789 | 0.5704 |
| -0.316 | 0.0506 | 0.1110 |
| -0.316 | 0.0506 | -0.2588 |
| -0.316 | 0.0506 | -0.5796 |
| | -3.162 | -279.545 | -80.591 |
| | | -7.8994 | +0.589 |
| | | -3.304 |
(7.11)

Given Q and R, the equation R = Qᵀy is solved by back-substitution to obtain the value of A = Qᵀy in equation (7.12).

| -0.316 | -0.316 | -0.316 | -0.316 | -0.316 | -0.316 | -0.316 | -0.316 | -0.316 | 26.06 |
| -0.0768 | -0.076 | 0.0683 | -0.076 | 0.0506 | 0.0506 | -0.0789 | 0.0506 | 0.0506 | 25.76 |
| -0.1876 | -0.1876 | 0.0388 | -0.0968 | 0.2496 | 0.3404 | 0.5704 | 0.110 | -0.2588 | -0.5796 | 24.69 |
| | | | | | | | | | 24.39 |
| | | | | | | | | | 23.63 |
| | | | | | | | | | 24.70 |
| | | | | | | | | | | 26.37 |
| | | | | | | | | | | 27.43 |
| | | | | | | | | | | 28.79 |
(7.12)

| -81.4539 |
| -0.3669 |
| -3.7450 |