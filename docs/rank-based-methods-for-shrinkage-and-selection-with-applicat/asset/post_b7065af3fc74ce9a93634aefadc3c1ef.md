
- 12.2. In this chapter, we discussed the sigmoid and relu activation functions. The function, tanh(z), is another often-used activation function and is the subject of this problem.

  (a) Write the equation for this function and construct one plot that includes tanh(z) with the sigmoid and relu functions of Figure 12.2.
  (b) Specify the domain and range of z and tanh(z), respectively.
  (c) Determine the partial derivative of tanh(z) with respect to z.
  (d) Explain why this is a valid activation function and its advantages or disadvantages relative to the sigmoid and relu activation functions.

- 12.3. Find the expression for ∂D_n(β)/∂β_0 of Figure 12.4 for the rank objective function of Eq. (12.2.8). (Hint: derive Eq. (12.5.17) noting that the bias term is fixed at 1.)

- 12.4. Apply the chain rule as in Eq. (12.5.21) to find the complete expression for β_3 of Figure 12.4 for the rank dispersion loss function with a ridge penalty applied. (Hint: derive Eq. (12.5.18) and include the ridge gradient term)

- 12.5. Apply the chain rule as in Eq. (12.5.21) to find the complete expression for β_23 of Figure 12.4 for the rank objective function of Eq. (12.2.8). (Hint: you will need to use the indicator function since the relu function is involved.)

- 12.6. Consider Table 12.16 of true responses, predicted probabilities and quantized probabilities from a binary classifier. Compute the accuracy, recall, precision and F_1 score based on this data. Set undefined values to 0. Why is the accuracy so high relative to the other metrics? What is your assessment of this classifier?

Table 12.16 Table of responses and probability outputs.

| i | y_i | p̂_i | quantized p̂_i |
|---|---|---|---|
| 1 | 0 | 0.37 | 0 |
| 2 | 0 | 0.37 | 0 |
| 3 | 1 | 0.37 | 0 |
| 4 | 0 | 0.37 | 0 |
| 5 | 0 | 0.37 | 0 |
| 6 | 0 | 0.37 | 0 |
| 7 | 1 | 0.37 | 0 |
| 8 | 0 | 0.37 | 0 |
| 9 | 0 | 0.37 | 0 |
| 10 | 0 | 0.37 | 0 |

- 12.7. Gradient descent with momentum is important for RNN. It uses an exponential weighting of previous derivative terms using a momentum factor which is typically set to \(\gamma = 0.9\). The update equation is given by

  \(\mathbf{v}_{\text{db}}^{(t+1)} = \gamma \mathbf{v}_{\text{db}}^{(t)} + (1 - \gamma) \left( \frac{\partial D_n(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}} \right)^{(t+1)}\) (12.11.1)

  Initially, \(\mathbf{v}_{\text{db}}^{(0)} = 0\). Compute this term for ten iterations and plot the effective weights on the previous 10 derivatives as a function of iteration number. First, set \((\frac{\partial D_n(\boldsymbol{\beta})}{\partial \boldsymbol{\beta}})^{(t+1)} = \Delta^{(t+1)}\) to make it easier to work out the recursion formula. (Hint: the weight on each new derivative is \(1 - \gamma = 0.1\). Then, our first iteration would be \(\mathbf{v}_{\text{db}}^{(1)} = 0.9 \times 0 + 0.1 \Delta^{(1)} = 0.1 \Delta^{(1)}\). Now let \(t = 1\) and continue the recursion from there. You will end up with \(\Delta^{(1)}\) to \(\Delta^{(10)}\) in the final iteration.)

- 12.8. This problem concerns some of the applications used in this chapter.
  - (a) Assume that you have 42,000 images of cats and dogs. How would you set up the training, cross-validation and test sets for this problem to obtain results that generalize to the test set. What actual numbers of images would you use in each data set? Explain why.
  - (b) The MNIST data set is typically addressed using mini-batch gradient descent but could also be done using stochastic gradient descent where only one image is processed at a time. What potential problem/solution do you foresee using rank-based neural networks with stochastic gradient descent?
  - (c) How many parameters are actually used in the digit recognizer neural network if there is one hidden layer with 25 units as used in this chapter? What if the number of units in the hidden layer were increased to 35?

## 12.9. FINAL PROJECT: Part 1 – LNN program

### (a) Build a circular data set similar to Figure 12.8(a) using R. Assign six data points to be outliers as shown in the upper region of the figure. The R code below is suitable for this purpose. Enter this R code and check the results.

```r
set.seed(123)
#Pick 400 random points
n <- 400
x1 <- runif(n, min = -2, max=2)
x2 <- runif(n, min = -2, max=2)
plot(x1,x2)
#Cut out a circular region and
# apply y labels. Add 6 outliers
y <- rep(0,n)
cnt <- 0
for (i in 1:n) {
if ((x1[i]^2 + x2[i]^2) < 0.8) {
y[i] = 0
} else if ((x1[i]^2 + x2[i]^2) > 1.5) {
if ((x2[i]>1.8) & (cnt<6)) {
y[i]=0
cnt <- cnt + 1
} else {
y[i] = 1
}
} else {
y[i] = -1
}
}

#Make a circle dataframe
ones <- c(rep(1,n))
circle <- data.frame("x1"= x1, "x2"=x2,
"ones"=1,"y"=y)

circle <- circle[circle$y>-1,]
#Plot the data with color-coding
set1 <-circle[circle$y == 1,]
plot(set1$x1,set1$x2,col="red")
set2 <-circle[circle$y == 0,]
points(set1$x1,set1$x2,ylim=c(-2,2),
xlim=c(-2,2),col="blue")
```

### (b) Next, define the sigmoid function in R as done in the chapter problems in Chapter 11 using the follow R code.

```r
sigmoid <- function(z ) {
p <- 1.0/(1.0+exp(-z))
return(p)
}
```

### (c) Write R code for a neural network code that performs LNN using the information in this chapter. The architecture of the NN is given in Figure 12.7. The forward propagation step should implement what is shown in Figure 12.5. The log-likelihood loss function should be computed using the results. The backward propagation step should use the partial derivatives to compute the matrix and vector gradients. In each step, the gradient matrix and vector for one observation should be computed and added to the full gradient matrix and vector. Then the learning rate should be applied to obtain the new estimates. The R code below should be useful for this purpose if you have trouble writing your own code. If you are well-versed in R, you could improve the code by writing it in a form that is easier to follow. Enter the code and run it on the circular data set just created. It will take a few minutes to produce the estimates.

```r
# 2-layer neural network (NN) using
# log-likelihood loss
# Build X and y data set from circle data
y <- circle$y
X <- model.matrix(y~x1+x2,circle)
n <- length(y)

# NN Architecture L=2, U1=4, U2=1

#Initialize parameters, vector, matrix
set.seed(123) #Start ALL run from here
lambda2 = 0.0 #ridge regularization factor
gamma = 0.0 #momentum factor
learning_rate = 0.02
Bvector <- rnorm(5)*0.01
Bmatrix <- matrix(rnorm(12),nrow=4,ncol=3)*0.01
maxIter <- 20000
iterations <- rep(0,maxIter)

#MAIN LOOP
for (iter in 1:maxIter){

#FWD PROP
z <- Bmatrix %*% t(X) #Step 1
a <- z * (z>0) #Step 2
ones <- matrix(1,nrow=1,ncol=n)
a1 <- rbind(a, ones)
zout <- Bvector %*% a1 #Step 3
yF <- sigmoid(zout) #Step 4

#Back prop
delBmatrix <- matrix(0,nrow=4,ncol=3)
bvec <- Bvector[1:4]
for (i in 1:n) { #Create gradient matrix
d <- z[,i]>0
d2 <- rbind(d,d)
Indicator <- rbind(d2,d) # Indicator matrix
fullmatrix <- - ((bvec) %*% t(X[i,])) *
(yF[i]-y[i])
delBmatrix <- delBmatrix +
fullmatrix * t(Indicator)
}
delBvector <- rnorm(5)*0.0
for (i in 1:n) { #Create gradient vector
delBvector <- delBvector +
a1[,i]*(yF[i]-y[i])
}

#Calculate loss function
loss <- -(1/n)*sum(y*log(yF)+(1-y)*log(1-yF))
if (iter %% 1000 == 1) {
print(iter)
print(loss)
}
iterations[iter] <- loss

#Parameter update using learning rate
Bvector <- Bvector -
learning_rate * delBvector/n
Bmatrix <- Bmatrix -
learning_rate * delBmatrix/n
}
```

### (d) Plot the values of the loss function as a function of the iteration count to ensure proper convergence. Then plot the predicted probabilities y_F vs. y to get a sense of the quality of the solution. Explain this plot and categorize regions as tp, tn, fp, or fn using a threshold of 0.5.

```r
plot(1:maxIter,iterations,type = "l",
ylim=c(0,0.7), ylab = "Loss function",
xlab = "iteration count")
plot(yF,y)
```

### (e) In order to obtain the nonlinear decision boundary, one option is to create thousands of points in the space (either a grid or random) and then run the resulting X matrix through the forward propagation steps to get the predicted values. These can be color-coded to obtain the
