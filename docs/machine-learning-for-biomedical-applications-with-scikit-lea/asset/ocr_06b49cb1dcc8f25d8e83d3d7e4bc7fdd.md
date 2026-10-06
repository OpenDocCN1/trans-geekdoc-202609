# 2.3.1 Underfitting and overfitting

In the case of simple models, as univariate polynomial regression, we can assess the model visually. We can see in Fig. 2.6 that a polynomial of degree 1 does not capture the quadratic trend in the data and is therefore underfitting the data. On the other hand, a polynomial of degree 20 varies too much, seems to fit the noise in the data, and is therefore overfitting. Finally, the polynomial of degree 2 seems to work very well. This is expected because the underlying true is quadratic.

# 2.3.2 Training, validation, and testing

To be able to tune the learning models automatically, we need a quantitative measure of how well the model fits. In Sect. 2.2.1 we have seen that $R^2$ score is a suitable measure for regression models and it measures the proportion of variance in the data explained by the model. If we plot $R^2$ scores for polynomial fits to the training data (Fig. 2.7), we can see that it increases with the degree of the polynomial. We can clearly identify overfitting for the polynomial of degree 1 (linear regression). However, we cannot identify overfitting because the polynomial degree always increases the $R^2$ score. The solution is to have a separate validation set on which we can evaluate the model for each polynomial degree. If we fit the model using the original data (training set) but evaluate it using the validation set, the model will overfit to the noise in the training set but not in the validation set. That way we can identify overfitting. In Fig. 2.7 we can see that the $R^2$ score on the validation set first increases just as the training set, but starts decreasing as the polynomial degree becomes higher. We chose

![](bbox=[0.141, 0.558, 0.803, 0.762])

Figure 2.7 Performance of polynomial regression models of various degrees measured by $R^2$ score on training set and test set.

the hyperparameters (e.g., polynomial degree) by selecting the model that performs best on the validation set. However, there would still be a possibility that the model is overfitted to the validation set as this set was used to choose the hyperparameters and the final performance is overestimated. It is therefore necessary to create a third set,