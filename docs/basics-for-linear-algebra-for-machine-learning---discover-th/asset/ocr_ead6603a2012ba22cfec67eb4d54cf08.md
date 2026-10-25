Listing 17.14: Sample output from calculating vector correlation.

# 17.5 Covariance Matrix

The covariance matrix is a square and symmetric matrix that describes the covariance between two or more random variables. The diagonal of the covariance matrix are the variances of each of the random variables, as such it is often called the variance-covariance matrix. A covariance matrix is a generalization of the covariance of two variables and captures the way in which all variables in the dataset may change together. The covariance matrix is denoted as the uppercase Greek letter Sigma, e.g. \(\Sigma\). The covariance for each pair of random variables is calculated as above.

\(\Sigma = E[(X - E[X] \times (Y - E[Y])]\) (17.18)

Where:

\(\Sigma_{i,j} = cov(X_i, X_j)\) (17.19)

And X is a matrix where each column represents a random variable. The covariance matrix provides a useful tool for separating the structured relationships in a matrix of random variables. This can be used to decorrelate variables or applied as a transform to other variables. It is a key element used in the Principal Component Analysis data reduction method, or PCA for short.

The covariance matrix can be calculated in NumPy using the cov() function. By default, this function will calculate the sample covariance matrix. The cov() function can be called with a single 2D array where each sub-array contains a feature (e.g. column). If this function is called with your data defined in a normal matrix format (rows then columns), then a transpose of the matrix will need to be provided to the function in order to correctly calculate the covariance of the columns. Below is an example that defines a dataset with 5 observations across 3 features and calculates the covariance matrix.

```
# covariance matrix
from numpy import array
from numpy import cov
# define matrix of observations
X = array([
[1, 5, 8],
[3, 5, 11],
[2, 4, 9],
[3, 6, 10],
[1, 5, 10]])
print(X)
# calculate covariance matrix
Sigma = cov(X.T)
print(Sigma)
```

Listing 17.15: Example of calculating a covariance matrix.

Running the example first prints the defined dataset and then the calculated covariance matrix.