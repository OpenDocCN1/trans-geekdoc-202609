
We can identify the features which don’t want as independent features in model building. Three such features are `PLAYER_NAME`, `TEAM`, and `AUCTION_YEAR`. We will also keep `BASE PRICE` outside the feature list. The below code chunk removes these features from the predictor list.
![](images/page233-01.png)![](images/page233-02.png)
### Encoding Categorical Features
In this section, we will discuss encoding categorical features without the use of the `caret` package. Note that the numeric features are also being standardized for `GD` to converge faster.
![](images/page233-03.png)![](images/page234-01.png)
### Set `x` and `y` Variable
The `processed_df` contains the standardized and dummy variable coded features which will be used for regression modelling. Separating the features as `X` (predictor) and `Y` (outcome) feature. The predictors are shown in **[Table 7.2](#15_Chapter07.xhtml#tab7.2).**
![](images/page234-02.png)
The first five records and first 10 features in `X` are as follows **([Table 7.2](#15_Chapter07.xhtml#tab7.2)):**
![](images/page234-03.png)
The first six records of `SOLD PRICE` (`Y`) are shown in **[Table 7.3](#15_Chapter07.xhtml#tab7.3):**
![](images/page234-04.png)![](images/page234-05.png)
**TABLE 7.3** | `Y` **features**
| `SOLD_PRICE` |
| --- |
| −1.1583445 |
| --- |
| −1.1583445 |
| −0.4208947 |
| 0.8081883 |
| 0.6852800 |
| −1.1583445 |
### Implementing the GD Algorithm
To implement the steps explained in [Section 7.3](#15_Chapter07.xhtml#sec7.3), a set of following user-defined functions need to be implemented.
**Step 1:** Function to randomly initialize the beta coefficients.
![](images/page235-01.png)
`x` represents the features in the dataset. In the above function, we will initialize `betas` to zero for all features in the dataset.
**Step 2:** Function to calculate the predicted value of `Y`, that is, `Y` given the bias and weights
![](images/page235-02.png)
`%*%` represents matrix multiplication. Thus, the above code is implementing the equation `h(x^(i)) = β[0] + β[1] * X¹ + … + β[m] * X^(m)` for all the `m` features in the dataset (`X^m` is the `m^(th)` feature).
**Step 3:** Function to calculate the cost function from predicted and actual values of `Y`. Let us put equation ** in implementation and define the Mean Squared Error function, that is, Compute Mean Squared Error (`MSE`) by
**1.** Calculating differences between the calculated `Y` and actual `Y`
**2.** Calculating the square of the above residuals and summing it up
**3.** Dividing it with a number of observations
![](images/page235-03.png)
**Step 4:** Function to calculate the gradients and adjust the bias and weights
This is the most important method, where the bias and weights get adjusted based on the gradient of the cost function. Equations (7.5) and (7.6) are implemented in the `update_beta()` as `beta = beta – alpha * delta`.
![](images/page235-04.png)
**Step 5:** Updates to the `betas` need to be done iteratively, until the cost is minimum. It can take several iterations and be time-consuming. There are two approaches to stop the iterations.
**1.** Run a fixed number of iterations and use the `betas` as optimal values at the end of these iterations.
**2.** Run iterations until the `δ` change in `MSE` or cost is small, that is, less than the predefined value, for example 0.001.
![](images/page235-05.png)
We will illustrate the first approach to find the optimal `beta` coefficients. Let us initialize the learning rate, that is, `alpha` to 0.01. Iteration “`iter`” is the number of loops defined for the descent.
![](images/page236-01.png)
Later on, we will use the `caret` package `glmnet()` function to find the best `beta` coefficients which minimize the `MSE` or the cost function.
#### Plot Cost Value
We can plot cost as a function of number of iterations to converge.
![](images/page236-02.png)
In **[Figure 7.2](#15_Chapter07.xhtml#fig7.2)**, we can see that the `MSE` or the cost does not seem to change as the number of iteration crosses 1,000. By analyzing the `cost_history`, we can see that the convergence, that is, `δ` change in `MSE` has been reached in 1,488 iterations. One can use the above code using do while or while loop rather than restricting the number of iterations. The final weights are stored in `beta` coefficients.
![](images/page236-03.png)![](images/page237-01.png)
**Gradient descent** is a popular optimization algorithm and is at the core of many advanced Machine Learning algorithm, including neural networks. Gradient descent is used for finding the feature weights in AI and ML algorithms.
The weights are standardized values as we have used standardized values of `Y` and `X`. So, the interpretation the `beta` coefficients for `ODI_RUNS_S` will change in terms of standard deviations, that is, for one standard deviation change in `ODI_RUNS_S`, the `SOLD_PRICE` changes by 0.43 standard deviations.
The above implementation of machine learning algorithm using `GD` algorithms is important for understanding the estimation of feature weights. In the above implementation, we have not taken care of regularization. Intuitively, we can think of regularization as a technique for performing a trade-off between model overfitting (variance) and model underfitting (bias). The regularization term is added to the `MSE` or the cost function to penalize the `beta` coefficients in order to tackle the overfitting issue.
![](images/page237-02.png)
## 7.4 | Bias-Variance Trade-off
Model errors can be decomposed into two components called bias and variance. Understanding these two components is the key to diagnosing model accuracies and avoid model overfitting or underfitting. High bias can lead to building underfitting models, whereas high variance can lead to overfitting models, and thus can result in generalization errors. **[Table 7.4](#15_Chapter07.xhtml#tab7.4)** shows two specific features from a patient’s dataset, that is, weight (`X`) and height of the patients (`Y`).
**TABLE 7.4** | Patient data
| `BODY_WEIGHT` || `BODY_HEIGHT` |
| --- | --- |
| 49 || 160 |
| --- | --- |
| 41 || 155 |
| 47 || 164 |
| 80 || 173 |
| 58 || 175 |
| 45 || 140 |
![](images/page238-01.png)
Assume that we want to build a regression model to predict the height of the person given the weight. As there are only two variables, we can observe the relationship by plotting them using scatter plot.
![](images/page238-02.png)
It can be observed from **[Figure 7.3](#15_Chapter07.xhtml#fig7.3)** that the relation between `Y` and `X` is not linear and looks polynomial. But we are not sure of the degree of the polynomial form. We need to try various polynomial forms of `X` and verify which model is the best fit to the data. The `poly()` function from stats package can be used to create features with varying degrees, that is, 2, 3, 4, etc. If we create a second degree feature using the `poly()` function, the data will look like what is shown in **[Table 7.5](#15_Chapter07.xhtml#tab7.5):**
**TABLE 7.5** | Polynomial feature
| 1 || 2 |
| --- | --- |
| 49 || 2,401 |
| --- | --- |
| 41 || 1,681 |
| 47 || 2,209 |
| 80 || 6,400 |
| 58 || 3,364 |
| 45 || 2,025 |
![](images/page239-01.png)![](images/page239-02.png)
The first column of **[Table 7.5](#15_Chapter07.xhtml#tab7.5)** is the actual body weight and the second column represents the square of body weight. Using the values in **[Table 7.5](#15_Chapter07.xhtml#tab7.5)** as predictors, the functional form of regression model will be ![](images/pageIn_ch7-01.png). However, before proceeding with model building, let us split the `raw_df` to training and test data. We will also write a user-defined function `fit_ploy()` to build a polynomial regression model with any degree `n`.
![](images/page239-03.png)
