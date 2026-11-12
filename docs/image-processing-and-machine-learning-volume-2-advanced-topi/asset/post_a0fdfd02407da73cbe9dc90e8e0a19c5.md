
## TABLE 6.1 Data to Calculate the Principal Component Analysis

| Data | X1 | X2 |
| :--- | :--- | :--- |
| 1 | 8.7 | 0.3 |
| 2 | 14.3 | 0.9 |
| 3 | 18.9 | 1.8 |
| 4 | 19.0 | 0.8 |
| 5 | 20.5 | 0.9 |
| 6 | 14.7 | 1.1 |
| 7 | 18.8 | 2.5 |
| 8 | 37.3 | 2.7 |
| 9 | 12.6 | 1.3 |
| 10 | 25.7 | 3.4 |

Considering that the data in Table 6.1 are represented in the matrix X, you can compute the covariance matrix as follows:

```
S = cov(X) ;
```

This will return the covariance matrix S, which is a p x p matrix, where the i, j element is the covariance between the i-th and j-th variables in the data. From the data in Table 6.1, the covariance matrix is defined as follows:

$$\mathbf{S} = \begin{bmatrix} 56.97 & 5.17 \\ 5.17 & 0.89 \end{bmatrix} \quad (6.14)$$

On the other hand, correlation in data refers to the degree to which two or more variables are related to each other. It is a statistical measure that ranges from -1 to 1, where -1 indicates a perfect negative correlation, 0 indicates no correlation, and 1 indicates a perfect positive correlation. A positive correlation means that as one variable increases, the other variable also increases, and a negative correlation means that as one variable increases, the other variable decreases. Correlation can be used to identify patterns and relationships in data.

In MATLAB, you can calculate the correlation between two variables using the corr function. The function takes in two vectors or matrices as input and returns the correlation coefficient. For example, if you have two vectors x and y that you want to calculate the correlation for, you can use the following code:

```
r = corr(x, y) ;
```

This will return the correlation coefficient r between the two vectors x and y. You can also calculate the correlation matrix for a set of variables in a matrix.

For example, if you have a matrix A with several columns representing different variables, you can use the following code:

```
R = corr(A);
```

This will return a matrix R where the element in the i,j position gives the correlation between the i-th and j-th columns of A. Note that the corr function uses the Pearson correlation coefficient by default, which assumes that the data is normally distributed and linear relationship between the variables. If your data does not meet these assumptions, you may consider using other types of correlation.

Covariance and correlation are two concepts that are closely related. Covariance is a measure of the degree to which two variables vary together. A positive covariance indicates that the variables tend to increase or decrease together, while a negative covariance indicates that the variables tend to move in opposite directions. The unit of measurement for covariance is the product of the units of the two variables.

Correlation, on the other hand, is a standardized measure of the degree to which two variables are related. It is the ratio of the covariance of the two variables to the product of their standard deviations. Correlation takes on a value between -1 and 1, with -1 indicating a perfect negative linear relationship, 0 indicating no relationship, and 1 indicating a perfect positive linear relationship.

Both covariance and correlation are useful for understanding the relationship between two variables, but correlation is generally more useful for comparing the strength of the relationship between different pairs of variables because it is standardized and independent of the unit of measurement. You can compute the covariance matrix from a given correlation matrix by using the formula

```
S = D R D (6.15)
```

where R is the correlation matrix, D is a diagonal matrix of standard deviations, and C is the covariance matrix.

Considering that the mean X value of the elements in Table 6.1 are (19.05, 1.57)', the eigenvalues of S are defined as lambda1 = 57.44 and lambda2 = 0.42. The corresponding normalized eigenvectors are e1 ≈ (0.99, 0.09)' and e2 ≈ (0.09, -0.99)'. Therefore, the principal components of S have the following components:

```
Y1 = e1'(X - Xbar) = 0.99(X1 - 19.05) + 0.09(X2 - 0.42)
Y2 = e2'(X - Xbar) = 0.09(X1 - 19.05) - 0.99(X2 - 0.42). (6.16)
```

The variance of a principal component is defined by the eigenvalue of S.

```
var(Y1) = lambda1 = 57.44 and var(Y2) = lambda2 = 0.42. (6.17)
```

The proportion of variance explained by \(Y_1\) is \(\text{var}(Y_1) / VT(\mathbf{S}) \simeq 99\%\).

The correlation coefficients between \(Y_1\) and \(X_k\) as \(\text{corr}(Y_1, X_k)\), for \(k=1,2\), is computed as follows:

```
\(\text{corr}(Y_1, X_1) = \frac{e_{11}\sqrt{\lambda_1}}{\sqrt{s_{11}}} = \frac{0.99\sqrt{57.44}}{\sqrt{56.97}} \simeq 0.99\)
```

and

```
\(\text{corr}(Y_1, X_2) = \frac{e_{12}\sqrt{\lambda_1}}{\sqrt{s_{22}}} = 0.72.\)
```

The fact that the first principal component (which is essentially \(X_1\)) explains a large part of the variability of the system is due to the fact that the sample variance of \(X_1\) is much larger than that of \(X_2\) and that makes the variance considerably larger throughout the direction given by the vector \(\mathbf{e}_1\). In this case, it is convenient to standardize the data and perform a new PCA on the resulting matrix. This is equivalent to obtaining the principal components from the correlation matrix.

## 6.7 Principal Components through Correlation

It is also possible to calculate the principal components through the correlation matrix \(\mathbf{R}\). In order to exemplify this concept, consider the data in Table 6.1. Then, by using the function \(\text{corr}\), the following matrix is found:

```
\(\mathbf{R} = \begin{pmatrix} 1 & 0.72 \\ 0.72 & 1 \end{pmatrix}\)
```

\(\mathbf{R}\) has as eigenvalues \(\lambda_1 = 1.72\), \(\lambda_2 = 0.28\) and as eigenvectors

```
\(\mathbf{e}_1 = (0.71, 0.71)' \quad \text{and} \quad \mathbf{e}_2 = (-0.71, 0.71)'.\)
```

Therefore, the principal components from \(\mathbf{R}\) are calculated as follows:

```
\(Y_1 = \mathbf{e}_1'\mathbf{Z} = 0.71Z_1 + 0.71Z_2\)
\(Y_2 = \mathbf{e}_2'\mathbf{Z} = -0.71Z_1 + 0.71Z_2,\)
```

where \(Z_1 = (X_1 - 19.05) / 7.55\), \(Z_2 = (X_2 - 1.57) / 0.94\), and \(\mathbf{Z} = (Z_1, Z_2)'\) is the standardized vector \(\mathbf{X}\).

The total variability is measured by \(VT(\mathbf{R}) = \text{tr}(\mathbf{R}) = 2\), and the proportion of it is explained by \(Y_1\) is \(\lambda_1 / VT(\mathbf{R}) = 1.72/2 = 86\%\). The correlation coefficients between \(Y_1\) and the variables \(Z_i\) are:

\(\text{corr}(Y_1, Z_1) = \frac{e_{11}\sqrt{\lambda_1}}{\sqrt{r_{11}}} = 0.93, \text{corr}(Y_1, Z_2) = 0.93.\) (6.23)

The first principal component of \(\mathbf{R}\) now gives equal greater weight to the variables \(X_1\) and \(X_2\). As discussed in Problem 4.2, it would be more appropriate to calculate the principal components from \(\mathbf{R}\). The determination of the principal components can also be conducted through MATLAB functions. In order to calculate the principal components, the following procedure is applied (Algorithm 6.1).

## **ALGORITHM 6.1 DETERMINATION OF THE PRINCIPAL COMPONENTS**

- 1. Load the data into MATLAB.
- 2. Subtract the mean of each column of data from the corresponding column. This is done to ensure that the data is centered around the origin, which is a requirement for PCA.
- 3. Compute the covariance matrix of the data. This can be done using the cov function in MATLAB.
- 4. Compute the eigenvectors and eigenvalues of the covariance matrix. This can be done using the eig function in MATLAB. The eigenvectors are the principal components, and the eigenvalues are the variances of the data along each principal component.
- 5. Sort the eigenvectors and eigenvalues in descending order of eigenvalues. This will give you the principal components in order of importance, with the first component having the highest variance.
- 6. Project the data onto the principal components by multiplying the data matrix with the matrix of eigenvectors.
- 7. You can also visualize the data in the PCA space using the scatter function in MATLAB with the projected data.

Note: PCA is a powerful tool, but it should be used with caution. It is sensitive to the scale of the data, so it’s recommended to standardize the data before running PCA. Also, it can only be used on linear relationships, so it may not be appropriate for certain types of data or problems.

The code presented in Program 6.2 illustrates the necessary steps to perform the determination of the principal components from the data of matrix \(\mathbf{A}\).
