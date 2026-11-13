![](bbox=[0.107, 0.093, 0.553, 0.445])

Figure 4.16 (Cont'd) Illustration of the KNN (from [39]).

# 4.1.1.12.2 Programming This Algorithm

The Python and R codes for the KNN algorithm are provided below:

# Python Package

```
import sklearn
from sklearn.neighbors import NearestNeighbors
model = NearestNeighbors()
```

# R Package:

```
>install.packages("class")
>library(class)
>knn(train, test, cl, k = 1, l = 0, prob = FALSE, use.all = TRUE)
```

# 4.1.1.13 Linear Regression (LiR)

This is perhaps one of the simplest supervised ML algorithms. Linear regression (LiR) is applied in regression problems to tie a target with one or more independent variables.64

# How does it work?

In LiR, the coefficients of the linear form are estimated using the least-squares criterion, which minimizes the sum of squared residuals. In this process, the LiR tries to find the weights (namely, slope and y-intercept) that lead to the best-fitting line for the input data.