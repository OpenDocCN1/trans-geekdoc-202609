To calculate the eigenvalues and eigenvectors of \(\Sigma\) in MATLAB, you can use the `eig` function to compute the eigenvalues of a matrix.

```
A = [3 1 1; 1 3 1; 1 1 5];
eig_values = eig(A) ;
```

The eigenvalues of \(\Sigma\), ordered from highest to lowest, are \(\lambda_1 = 6, \lambda_2 = 3\) and \(\lambda_3 = 2\). The corresponding normalized eigenvectors are \(\mathbf{e}_1 = (1,1,2)'/\sqrt{6}, \mathbf{e}_2 = (1,1,-1)'/\sqrt{3}, \mathbf{e}_3 = (1,-1,0)'/\sqrt{2}\).

The proportion that explains the total variance of each component is specified by the vector \(\mathbf{Y} = (Y_1, Y_2, Y_3)'\). Its main components are as follows:

+   \(Y_1 = \mathbf{e_1}'\mathbf{X} = \frac{1}{\sqrt{6}}(X_1 + X_2 + 2X_3)\)
+   \(Y_2 = \mathbf{e_2}'\mathbf{X} = \frac{1}{\sqrt{3}}(X_1 + X_2 - X_3)\) (6.11)
+   \(Y_3 = \mathbf{e_3}'\mathbf{X} = \frac{1}{\sqrt{2}}(X_1 - X_2)\)

The total variance is determined by:

\(VT(\Sigma) = \text{tr}(\Sigma) = 11\) (6.12)

The proportion of \(VT(\Sigma)\) explained by the first principal component is defined by:

\(\frac{\text{var}(Y_1)}{VT(\Sigma)} = \frac{\lambda_1}{11} \simeq 54.5\%.\) (6.13)

Similarly, that explained proportions by \(Y_2\) and \(Y_3\) are \(27.3\%\) and \(18.2\%\), respectively.

The representation of data from the original vector \(\mathbf{X}\) in the plane of the first two principal components, particularly in the observation \(\mathbf{x} = (2,2,1)'\). To express \(\mathbf{X}\) in the plane of \(Y_1\) and \(Y_2\), the scalar product of \(\mathbf{X}\) must be made by the directions given by \(\mathbf{e}_1\) and \(\mathbf{e}_2\). For \(\mathbf{x}\), the result is the point \((y_1, y_2) = (\sqrt{6}, \sqrt{3})\)

Given the data in Table 6.1, consider the variables \(X_1 =\) duration of the mortgage and \(X_2 =\) price and denote by \(\mathbf{X}\) the vector \((X_1, X_2)'\).

In MATLAB, you can use the `cov()` function to compute the covariance matrix of a set of data. The function takes two inputs: the data, which should be in the form of an \(n \times p\) matrix, where \(n\) is the number of observations and \(p\) is the number of variables and an optional parameter that specifies how the data should be scaled (default is ‘unbiased’).