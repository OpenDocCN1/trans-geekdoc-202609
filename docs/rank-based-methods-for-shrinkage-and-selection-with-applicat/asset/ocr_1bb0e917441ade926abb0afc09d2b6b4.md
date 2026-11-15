(Adjust the scatter plot to show 1 and 0 with different colors, if desired.)

+   (c) Using the coefficients from the summary(), plot a line representing the decision boundary on the previous plot. You will only need two points to construct the line. Note that the estimates define the boundary as \(\beta_0 + \beta_1 wt + \beta_2 hp = 0\). This can be used to create two points to draw a line. Here is an example of a possible pair of coordinates.
+   
+   ```r
+   xwt <- c(2.5,4.0)
+   yhp <- c(37, 370)
+   lines(xwt, yhp, col="black", lty=3)
+   ```

Compare your results with the results shown in Figure 11.3(a).

# 11.6. (PROJECT) In this problem, you will write a simple program in R for rank-based logistic regression (RLR) and test it using the data from the last problem (assumes you ran the code shown above) to reproduce the results shown in Figure 11.3(b). Note that to compute \(D_n(\boldsymbol{\beta})\), you will need to compute \(a_n(R(\boldsymbol{\beta}))\) which requires ranking the residuals and applying the scoring function as described in this chapter. In particular, the equation below will prove to be very useful,

\(\hat{\boldsymbol{\beta}}_n^{RLR} = \underset{\boldsymbol{\beta}}{\text{argmin}} \left\{ \sum_{i=1}^n (Y_i - f(\boldsymbol{\beta}^T \boldsymbol{x}_i)) \sqrt{12 \left( \frac{R_n(\boldsymbol{\beta})}{n+1} - \frac{1}{2} \right)} \right\}\).

+   (a) The first step is to write a routine for the sigmoid function and then test it to ensure that it operates properly. Enter and plot this function in R.
+   
+   ```r
+   sigmoid <- function(z){
+     p = 1/(1+exp(-z))
+     return(p)
+   }
+   ```

+   (b) Implement, test and plot the scoring function for \(0 < u < 1\) as follows:
+   
+   ```r
+   phi <- function(u){
+     result <- sqrt(12).*(u-0.5)
+     return(result)
+   }
+   ```

+   (c) Next, insert a column of 1s into the data for the intercept term \(\beta_0\), and then define the needed matrix and vector quantities.
+   
+   ```r
+   mtcars$ones <- rep(1,32)
+   ```