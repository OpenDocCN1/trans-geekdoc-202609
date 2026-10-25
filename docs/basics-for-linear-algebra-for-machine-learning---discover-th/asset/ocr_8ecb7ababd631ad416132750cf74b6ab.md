```
[ 0. 0. 0. 0. 0. 0.]
[ 1.87082869 1.87082869]
```

Listing 17.10: Sample output from calculating matrix standard deviations.

# 17.4 Covariance and Correlation

In probability, covariance is the measure of the joint probability for two random variables. It describes how the two variables change together. It is denoted as the function cov(X, Y), where X and Y are the two random variables being considered.

cov(X, Y) (17.13)

Covariance is calculated as expected value or average of the product of the differences of each random variable from their expected values, where E[X] is the expected value for X and E[Y] is the expected value of y.

cov(X, Y) = E[(X - E[X] x (Y - E[Y])] (17.14)

Assuming the expected values for X and Y have been calculated, the covariance can be calculated as the sum of the difference of x values from their expected value multiplied by the difference of the y values from their expected values multiplied by the reciprocal of the number of examples in the population.

cov(X, Y) = 1/n x sum(x - E[X]) x (y - E[Y]) (17.15)

In statistics, the sample covariance can be calculated in the same way, although with a bias correction, the same as with the variance.

cov(X, Y) = 1/(n-1) x sum(x - E[X]) x (y - E[Y]) (17.16)

The sign of the covariance can be interpreted as whether the two variables increase together (positive) or decrease together (negative). The magnitude of the covariance is not easily interpreted. A covariance value of zero indicates that both variables are completely independent. NumPy does not have a function to calculate the covariance between two variables directly. Instead, it has a function for calculating a covariance matrix called cov() that we can use to retrieve the covariance. By default, the cov() function will calculate the unbiased or sample covariance between the provided random variables.

The example below defines two vectors of equal length with one increasing and one decreasing. We would expect the covariance between these variables to be negative. We access just the covariance for the two variables as the [0, 1] element of the square covariance matrix returned.

```
# vector covariance
from numpy import array
from numpy import cov
# define first vector
x = array([1,2,3,4,5,6,7,8,9])
```