![](bbox=[0.206, 0.153, 0.806, 0.472])

Figure 19.4: Scatter Plot of SVD Solution to the Linear Regression Problem.

# 19.8 Solve via Convenience Function

The pseudoinverse via SVD approach to solving linear least squares is the de facto standard. This is because it is stable and works with most datasets. NumPy provides a convenience function named `lstsq()` that solves the linear least squares function using the SVD approach. The function takes as input the $X$ matrix and $y$ vector and returns the $b$ coefficients as well as residual errors, the rank of the provided $X$ matrix and the singular values. The example below demonstrate the `lstsq()` function on the test dataset.

```
# least squares via convenience function
from numpy import array
from numpy.linalg import lstsq
from matplotlib import pyplot
# define dataset
data = array([
[0.05, 0.12],
[0.18, 0.22],
[0.31, 0.35],
[0.42, 0.38],
[0.5, 0.49]])
# split into inputs and outputs
X, y = data[:,0], data[:,1]
```