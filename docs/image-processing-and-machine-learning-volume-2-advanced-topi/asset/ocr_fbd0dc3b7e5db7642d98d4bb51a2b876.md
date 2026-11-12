# TABLE 6.1 Data to Calculate the Principal Component Analysis

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