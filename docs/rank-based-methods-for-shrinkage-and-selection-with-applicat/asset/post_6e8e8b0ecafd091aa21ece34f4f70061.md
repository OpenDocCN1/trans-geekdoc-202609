
(Adjust the scatter plot to show 1 and 0 with different colors, if desired.)

- (c) Using the coefficients from the summary(), plot a line representing the decision boundary on the previous plot. You will only need two points to construct the line. Note that the estimates define the boundary as \(\beta_0 + \beta_1 wt + \beta_2 hp = 0\). This can be used to create two points to draw a line. Here is an example of a possible pair of coordinates.

```r
xwt <- c(2.5,4.0)
yhp <- c(37, 370)
lines(xwt, yhp, col="black", lty=3)
```

Compare your results with the results shown in Figure 11.3(a).

## 11.6. (PROJECT) In this problem, you will write a simple program in R for rank-based logistic regression (RLR) and test it using the data from the last problem (assumes you ran the code shown above) to reproduce the results shown in Figure 11.3(b). Note that to compute \(D_n(\boldsymbol{\beta})\), you will need to compute \(a_n(R(\boldsymbol{\beta}))\) which requires ranking the residuals and applying the scoring function as described in this chapter. In particular, the equation below will prove to be very useful,

\(\hat{\boldsymbol{\beta}}_n^{RLR} = \underset{\boldsymbol{\beta}}{\text{argmin}} \left\{ \sum_{i=1}^n (Y_i - f(\boldsymbol{\beta}^T \boldsymbol{x}_i)) \sqrt{12 \left( \frac{R_n(\boldsymbol{\beta})}{n+1} - \frac{1}{2} \right)} \right\}\).

- (a) The first step is to write a routine for the sigmoid function and then test it to ensure that it operates properly. Enter and plot this function in R.

```r
sigmoid <- function(z){
  p = 1/(1+exp(-z))
  return(p)
}
```

- (b) Implement, test and plot the scoring function for \(0 < u < 1\) as follows:

```r
phi <- function(u){
  result <- sqrt(12) * (u - 0.5)
  return(result)
}
```

- (c) Next, insert a column of 1s into the data for the intercept term \(\beta_0\), and then define the needed matrix and vector quantities.

```r
mtcars$ones <- rep(1,32)
x <- model.matrix(am~hp+wt+ones, mtcars)[,-1]
y <- mtcars$am
n <- length(y)
an <- rep(0,n)
Dn <- rep(0,n)
```

- (d) Finally, construct the function to minimize the dispersion function.

```r
minimize.RLR <- function(par, X, Y) {
  diff <- Y-sigmoid(X %*% par)
  Rn <- rank(diff,ties.method = "first")
  for ( i in 1:n) {
    an[i] <- phi(Rn[i]/(n+1))
    Dn[i] <- diff[i]*an[i]
  }
  Dnsum <- sum(Dn)
  return(Dnsum)
}
```

Test this function with an initial guess as the first parameter. What is your resulting value?

```r
minimize.RLR(c( 0.05,-10. ,20. ),x,y)
```

- (e) Compare the RLR boundary line with that of the previous problem.

Use

```r
op.result <- optim(c( 0.05,-10. ,20. ),
  fn = minimize.RLR, method = "BFGS",
  X = x, Y = y)
betaR <- op.result$par
```

What are the estimates when the R optimizer is used on minimize.RLR? Plot the boundary line using the estimates. Here is an example of a possible pair of coordinates.

```r
xwt <- c(2.5,4.0)
yhp <- c(-50, 420)
lines(xwt, yhp, col="red", lty=3)
```

## 11.7. (PROJECT) Modify the minimize.RLR routine to include ridge regression.

- (a) Update your R program to minimize $D_n(\boldsymbol{\beta}) + \lambda_2 \sum_{j=1}^p \beta_j^2$ and ensure that $\beta_0$ is not included as follows:

```r
lambda2 <- 0.0
Dnsum <- sum(Dn) +
lambda2*(par[1]*par[1]+par[2]*par[2])
```

- (b) Plot a ridge trace on a log(λ2) scale by choosing λ2 values from 0 to 1.0 such as 0.001, 0.01, 0.1, 1.0.

## 11.8. (PROJECT) Update your program to use LASSO regularization and generate the plot for LASSO trace on a log(λ1) scale.

- (a) Minimize D_n(β) + λ1 Σ_{j=1}^p |β_j|. Here, you can use:

```r
lambda1 <- 0.0
Dnsum <- sum(Dn) +
lambda1*(abs(par[1])+abs(par[2]))
```

- (b) Choose λ1 = 0 to 10, with values such as 0.01, 0.1, 1.0, and plot the results.

- (c) What is the most important feature based on your RLR-LASSO plot, hp or wt?

## 11.9. (PROJECT) Update your program to use aLASSO regularization and generate the plot for the aLASSO trace.

- (a) First the unpenalized estimates must be captured. Execute the following two lines once:

```r
bR1 <- betaR[1]
bR2 <- betaR[2]
```

Note that bR1 = β̂_1^RLR and bR2 = β̂_2^RLR. These are the rank estimates for λ1 = 0.

- (b) Next, to minimize D_n(β) + λ1 Σ_{j=1}^p |β_j| / |β_j^RLR|, the minimize.RLR routine must be modified as follows:

```r
lambda1 <- 0.0
Dnsum <- sum(Dn) +
lambda1*(abs(par[1]/bR1)+abs(par[2]/bR2))
```

- (c) Re-run the optimization multiple times with different lambda1 values. Use the range given by λ1 = 0 to 100, using values such as 0.01, 0.1, 1.0, 10.0. Plot the results on a log(λ1) scale.

- (d) What is the most important feature based on your RLR-aLASSO plot: hp or wt?

## 11.10. Examine the ridge, LASSO and aLASSO traces of the Titanic data set of Figures 11.13–11.15.

- (a) Qualitatively speaking, which provides the smoothest shrinkage characteristics.

- (b) Which one provides the most accurate variable ordering?

- (c) Which one appears to be a combination of the two?

## 11.11. For logistic regression, it is not possible to use the adjusted $R^2$ for subset selection as presented in Chapter 2. Describe how a 5-fold or 10-fold cross-validation scheme can be used to select the “optimal” size of the model for the Titanic data set. In particular, consider the test set MSE as a criterion for model selection.

## 12

## Rank-based Neural Networks

### 12.1 Introduction

Our objective in this chapter is to build upon Chapter 11, which covered rank-based logistic regression, and investigate the feasibility of applying rank-based methods to neural networks. The question here becomes, can rank-based methods be effectively used in conjunction with neural networks? Since we already know that rank-based methods are applicable to logistic regression, it follows naturally that it should be applicable to neural networks. Then the issue at hand is to determine what are the advantages of rank-based neural networks over log-likelihood neural networks for machine learning. This is the main question we will explore in this chapter. The advanced nature of the this topic requires that the reader have some degree of familiarity with neural networks and how they operate. An excellent book to consult for details on the subject is Haykin (2009). We strongly urge the novice reader to consult with this reference, or perhaps any other suitable book, as needed.

Work on neural networks (NNs) began in earnest by computer scientists in the mid-to-late 1980s and early 1990s in the pursuit of artificial intelligence systems. Neural networks were initially touted as a way to mimic the behavior and operation of the brain, although that connection is not completely embraced today. There was much excitement at the time regarding the potential of NNs to solve many unsolvable problems due to breakthroughs such as the use of the sigmoid function for activation in conjunction with development of efficient methods for back propagation. But there were technological barriers to its success at that time. In particular, computers were slow and the era of big data had not arrived and so NNs were relegated to being a niche technology and lay dormant for many years. In the intervening years, computer power increased significantly, new and efficient algorithms for neural networks were developed, and the Internet emerged to provide easy access to large data sets for users around the world.

Around 2010, the neural network emerged from its dormant state and made an impact in many important applications, most notably speech recognition, image processing and natural language processing. In medical applications, image recognition was able to quickly and accurately identify cancerous tissue and, as a result, NNs gained a strong foothold in radiology. Other advancements in supervised and unsupervised learning (James et al., 2013) were developed in the same period. Collectively, these methods were re-branded as “machine learning”. This term caught the attention of the media and is used to describe almost all applied statistical methods in use today.

Our purpose in this chapter is rather limited to a comparison of new rank-based NNs (RNNs)<sup>1</sup> against traditional log-likelihood neural networks (LNNs) for the application of image recognition. Here, we view NNs as simply multiple layers of logistic regression. If we have only one layer, it is standard logistic regression. If we have two or three layers it is a shallow NN. If there are many layers of logistic regression, it is called a deep NN, which is used for deep learning. The key difference between the early work on NNs and its ubiquitous presence today is the availability of big data. Images, video files, audio files, etc., are well-known forms of data for deep learning, but there are an uncountable number of other data sets that are also being processed using deep NNs.

Today, when the term “deep learning” is used, it refers to, for example, advanced convolutional NNs (CNNs) where the first few layers involve convolutional and maxpool layers, and the last layers are fully connected. The architecture of CNNs can be quite complex. These and other aspects of neural networks are well beyond the scope of this book. Fortunately, there are an unlimited number of resources for readers who seek an in-depth study of neural networks. Here, we focus on fully connected layers in order to compare RNNs with LNNs. It is tempting to use the term “multi-level logistic regression” to describe the fully connected architecture. However, the terms neural networks and deep learning are much more provocative and captivating than multi-level logistic regression, so they are now commonly used to describe work in this area. The meaning of layers and networks will become clear later in this chapter but the basic idea is that complex relationships between the independent variables can be realized by increasing the feature space of the problem.

Like logistic regression, neural networks are well-suited to binary classification problems and probability prediction, i.e. the likelihood that an event will

1 The acronym RNN is commonly used for recurrent neural networks. However, here we use it exclusively for rank-based neural networks.
