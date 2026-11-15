will have to run commands in R and write some simple R code to complete this problem11.

+   (a) Run the following lines of code in R to obtain LS estimates. Compare your results with the values obtained in the previous problem.

```
x<-cbind(c(11.7,17.9,21.1,14.7,7.7,8.4,32.8),
c(132.2,501.5,904.0,227.6,66.6,43.4,1253.0))
y<-c(40.6,1180.6,1807.5,470.0,
151.4,93.8,3293.4)
lmfit <- lm(y ~ x)
summary(lmfit)
```

+   (b) To obtain R-estimates, run the `rfit()` function. You may have to install the Rfit library in order to run the commands below.

```
library("Rfit")
fit <- rfit(y ~ x)
summary(fit)
```

How do your results compare with part (a). That is, are they almost the same or somewhat different?

+   (c) In this step you will enter R code to obtain the same results as in part (b). For this purpose, write a routine to perform the following operation:

![](bbox=[0.23, 0.5, 0.68, 0.55])

The `rank()` and `optim()` functions of R will be needed. You may find this starter R code below useful. It requires `x_centered` and `y_centered` to use this code. The results in `betaR` should match the output of `rfit()`.

```
minimize.DnB <- function(par, X, y) {
    n <- length(y)
    diff <- y-(X %*% par)
    Rni <- rank(diff,ties.method = "random")
    u <- Rni/(n+1.)
    an <- sqrt(12.)*(u-0.5)
    Dnsum <- sum(diff*an) #Estimator line
    return( Dnsum )
}
a <- t(x)-colMeans(x)
x_centered <- t(a)
```