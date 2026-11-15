
resulting boundary. Use the codes given in the above to construct a plot of the nonlinear decision boundary similar to Figure 12.8. (Hint: R code is shown in Problem 12.10(f).)

- (f) Add code to the program to implement LNN-ridge. This involves changing the code for the loss function and modifying the derivatives to add the penalty term. First, comment out the loss statement in the original R code. Then, for the loss function and the ridge penalty for the gradients, insert the following R code above the commented loss statement and re-run from the beginning. Try different values of $\lambda_2$ such as 0, 1.0 and 10.0 to see what values produce acceptable results.

```
# Add the penalty term to Bmatrix
# after unpenalized gradients are computed
ridgeBmatrix <- Bmatrix
ridgeBmatrix[,1] <- 0
ridgeBmatrix <- -2.*lambda2*ridgeBmatrix/n
delBmatrix <- delBmatrix + ridgeBmatrix
```

```
#Add the penalty term to Bvector
# after unpenalized gradients are computed
ridgeBvector <- Bvector
ridgeBvector[5] <- 0
ridgeBvector <- -2.*lambda2*ridgeBvector/n
delBvector <- delBvector + ridgeBvector
```

```
#Calculate penalized loss function
#loss <- -(1/n)*sum(y*log(yF)+(1-y)*log(1-yF))
ridge <- sum(ridgeBvector*ridgeBvector)+
sum(ridgeBmatrix*ridgeBmatrix)
loss <- -(1/n)*sum(y*log(yF)+
(1-y)*log(1-yF))+lambda2*ridge/n
```

- (g) The last (optional) step is to add momentum to the gradient descent process. This capability should not be needed in this small example, but it is useful to see how it is implemented. Prior to the update of the parameters, the following code should be added. Note that some of previous lines must be removed as well as shown below. Try different values of gamma to see if it has any effect (mainly used in deep NNs).

```
#Initialize momentum matrix and vector
# PRIOR to entering main loop
vdBV <- rnorm(5)*0.0
vdBM <- matrix(rnorm(12),nrow=4,ncol=3)*0.0
```

```
#At the end of the main loop
# REPLACE lines as follows
vdBV <- gamma*vdBV + (1.0-gamma)*delBvector
vdBM <- gamma*vdBM + (1.0-gamma)*delBmatrix

Bvector <- Bvector - learning_rate * vdBV/n
Bmatrix <- Bmatrix - learning_rate * vdBM/n
#Remove these lines
#Bvector <- Bvector -
#learning_rate * delBvector/n
#Bmatrix <- Bmatrix -
#learning_rate * delBmatrix/n
```

## 12.10. FINAL PROJECT: Part 2 – RNN program

In this problem, you will replace parts of the LNN program to produce an RNN program, optionally with ridge and momentum if you have completed those portions of the final project part 1. Make sure you study the LNN code in detail before proceeding. To begin the conversion to RNN, it is best to increase the learning rate 0.1 and the number of iterations to 25000 to produce a solution quickly.

```
learning_rate = 0.1
maxIter <- 25000
```

- (a) In this part, your task is to replace the loss function of the LNN code with the dispersion function. First, we need to define a scoring function at the beginning of the program (after the sigmoid function is defined). The R code below will be useful for this purpose.

```
phi <- function(u) {
  result <- sqrt(12.)*(u-0.5)
  return(result)
}
an <- rep(0,n)
Dn <- rep(0,n)
```

- (b) Next you need to INSERT the terms of the dispersion function AFTER step 4 of the forward propagation step.

```
diff <- y-yF
Rn <- rank(diff,ties.method = "first")
for (i in 1:n) {
an[i] <- phi(Rn[i]/(n+1.))
Dn[i] <- diff[i]*an[i]
}
```

- (c) The loss function is computed by simply adding up the Dn quantities. This should REPLACE the log-likelihood line of code.

```
#loss <- -(1/n)*sum(y*log(yF)+(1-y)*log(1-yF))+
#lambda2*ridge/n
loss <- (1/n)*sum(Dn)+lambda2*ridge/n
```

- (d) Next, you will need to carefully REPLACE the gradient matrix and vector codes for LNN with the following R code. It is based on the gradients derived earlier in this problem set. You should end up with something similar to the following R code.

```
#REPLACE
#fullmatrix <- -((bvec) %*% t(X[i,])) *
#(yF[i]-y[i])
#WITH
fullmatrix <- -((bvec) %*% t(X[i,])) *
(yF[i])*(1.0-yF[i])*an[i]
```

Note the sign change in the gradient matrix and the replacement of one term with the other. Next, carefully REPLACE the lines as follows.

```
#REPLACE
#delBvector <- delBvector + a1[,i]*
#(yF[i]-y[i])
#WITH
delBvector <- delBvector - a1[,i]*
(yF[i])*(1.0-yF[i])*an[i]
```

Again, there is a sign change in the gradient vector and the replacement of one term with the other. From these changes, we see that only a few lines of code separate RNN from LNN. Therefore, existing programs can easily be modified to include rank-based methods.

- (e) If you have placed the given code in the appropriate places in the original code, you should be able to run the RNN program at this point. Remember to start at the beginning and also reset lambda2 and gamma to 0.0. Once completed, you can check the convergence plot, and the logic plot. To examine the results of RNN, the color-coded predicted values can be checked using the following code.

```
yP <- rep(0,n)
for (i in 1:n) {
if (yF[i] >0.5) {
yP[i] <- 1
} else {
yP[i] <- 0
}
}
```

```
circle$yP <- yP
set1 <-circle[circle$yP == 1,]
plot(set1$x1,set1$x2,col="red")
set2 <-circle[circle$yP == 0,]
points(set2$x1,set2$x2,ylim=c(-2,2) ,
xlim=c(-2,2) ,col="blue")
```

- (f) Finally, if you want to observe the nonlinear decision boundary, this can be accomplished using the following code fragment, which is also useful for the LNN decision boundary.

```
xt1 <- runif(4000, min = -2, max=2)
xt2 <- runif(4000, min = -2, max=2)
ones <- c(rep(1,4000))
yt <- c(rep(1,4000))
circle3 <- data.frame("x1"=xt1, "x2"=xt2, "ones"=ones, "yt"=yt)
Xtest <- model.matrix(yt~xt1+xt2,circle3)
z <- Bmatrix %*% t(Xtest) #Step 1
a <- z * (z>0) #Step 2
ones <- matrix(1,nrow=1,ncol=4000)
a1 <- rbind(a,ones)
zout <- Bvector %*% a1 #Step 3
test <- sigmoid(zout) #Step 4
yP <- rnorm(4000)*0.0
for (i in 1:4000) {
if (test[i] >0.5) {
yP[i] <- 1
} else {
yP[i] <- 0
}
}
```

```
circle3$yP <- yP
sett1 <-circle3[circle3$yP == 1,]
plot(sett1$x1,sett1$x2,ylim=c(-2,2) ,
xlim=c(-2,2) ,col="red")
sett2 <-circle3[circle3$yP == 0,]
points(sett2$x1,sett2$x2,ylim=c(-2,2),
xlim=c(-2,2),col="blue")
```

Assuming the code ran successfully, you have now completed the final project and you can now begin to run your own experiments to compare LNN and RNN. You can also run any two-dimensional binary classification problem to further your understanding and start your research in this area. Greatness awaits.

## Bibliography

Adichie, J. N. (1967). Estimates of regression parameters based on rank tests, _The Annals of Mathematical Statistics_, **38**(3), 897–904.

Akdeniz, F., and Kaciranlar, S. (1995). On the almost unbiased generalized Liu estimator and unbiased estimation of the bias and mse, _Communications in Statistics-Theory and Methods_, 24(7), 1789–1797.

Akdeniz, F., and Kaciranlar, S. (2001). More on the new biased estimator in linear regression, _Sankhya_, **63**, 321–325.

Akdeniz, F., and Ozturk, F. (2005). The distribution of stochastic shrinkage biasing parameters of the Liu type estimator, _Applied Mathematics and Computation_, **163**(1): 29–38.

Akdeniz, F., Akdeniz Duran, E., Roozbeh, M., and Arashi, M. (2015). Efficiency of the generalized difference-based Liu estimators in semiparametric regression models with correlated errors, _Journal of Statistical Computation and Simulation_, **85**(1), 147–165.

Akritas, M. G., and Johnson, R. A. (1982). Efficiencies of tests and estimators for p-order autoregressive processes when the error distribution is nonnormal, _Annals of the Institute of Statistical Mathematics_, **34**(1), 579–589.

Anderson, T. W. (2003). _An Introduction to Multivariate Statistical Analysis_ (Third Edition), John Wiley & Sons.

Anderson, T. W., and Gill, R. D. (1982). Cox’s regression model for counting processes: a large sample study, _The Annals of Statistics_, **10**(4), 1100–1120.

Arashi, M., Kibria, B. M. G., Norouzirad, M., and Nadarajah, S. (2014). Improved preliminary test and Stein-rule Liu estimators for the ill-conditioned elliptical linear regression model, _Journal of Multivariate Analysis_, **124**, 53–74.

Arashi, M., Asar, Y., and Yuzbasi, B. (2017). LLASSO: A linear unified LASSO for multicollinear situations, _arXiv:1710.04795 [stat.ME]_.
