
## Application

You can now apply this trained and validated model to predict normalized closing prices on new, unseen data. This capability can be a powerful tool in forecasting future price movements and making strategic decisions.

By shifting from classification to regression, we move beyond identifying whether prices fall within a normal range to predicting the magnitude of their deviation. This approach provides a detailed and actionable understanding of price movements in relation to market volatility, enabling more precise trading decisions.

## LASSO method

Since we have already done steps 1 to 4 for classification in the previous section on Achieving high accuracy with boosting, these steps will be significantly abbreviated.

We start by scaling the features as follows:

```python
from sklearn.preprocessing import StandardScaler

scl = StandardScaler().set_output(transform="pandas")

X_train = scl.fit_transform(X_train)
X_test = scl.transform(X_test)
```

Next, invoke Sklearn to import the required models:

```python
from sklearn.linear_model import Lasso, Ridge
```

In the following code, we fine-tune the regression model to achieve our objective of quantifying price deviations within the volatility range:

```python
# hyperparameter search space
space = {
    'alpha': Real(0.001, 10, prior='log-uniform'), 
    # log scale for regularization
}

opt = BayesSearchCV(
    Lasso(),
    space,
    n_iter=30,
    cv=5,
    scoring="neg_mean_squared_error",
    n_jobs=-1,
    verbose=0
)

# optimize hyper parameters
opt.fit(X_train, y_train) 
print("best params: ")
pprint(opt.best_params_)
```

Output:
```text
best params: 
OrderedDict([('alpha', 0.001)])
```

Let us keep track of the best model to use it as of now:

```python
rgr = opt.best_estimator_
```

The following graph represents the predictions made by the optimized model on the test set, alongside realizations of the spread values (normalized closing price):

![](images/fig-7-6.png)

We check the goodness of fit with a scatterplot of predictions versus actuals. The proximity of the data points to the diagonal dashed line measures the accuracy of the model. The closer the points are to this line, the more accurate the model is:

![](images/fig-7-7.png)

In this case, the points cluster near the diagonal, suggesting that the optimized model provides a good fit. To quantify this observation, in the following code, we compute the regression score, which is normalized between `[-1, 1]`, and obtain a score of 0.8.

This score, being closer to maximum value 1, indicates a strong predictive performance by the model as follows:

```python
print(rgr.score(X_test, y_test))
```

Output:
```text
0.8
```

As mentioned in the introduction, LASSO has a strong feature selection capability by setting the coefficients of less relevant features to zero. To identify which features LASSO considers significant for our model, we can inspect (through the variable `rgr.coef_`) the non-zero coefficients assigned after model training:

```python
lst_coef = np.argwhere(rgr.coef_ != 0).reshape(1, -1)[0]
print("columns of interest :", list(X_test.iloc[:, lst_coef].columns))
```

Output:
```text
columns of interest : ['Close_diff_frac_0.2_4', 'Close_diff_frac_0.25_4', 'Close_diff_frac_0.3_4', 'Close_diff_frac_0.35_1', 'Close_diff_frac_0.35_2', 'Close_diff_frac_0.35_3', 'Close_diff_frac_0.35_4', 'Close_diff_frac_0.35_5', 'Volatility', 'Closing_Position', 'Gap_Previous_Close', 'Normalized_High', 'Relative_Change_Open_Close', 'High_Low_Clustering', 'SMA_30', 'SMA_35', 'MACD', 'MACD_Histogram', 'RSI', 'STOCHk_14_3_3', 'STOCHd_14_3_3', 'CCI', 'BBB_20_2.0', 'BBP_20_2.0', 'ATR', 'TR']
```

Out of the hundreds of features given to the LASSO model, it selects only this list of relevant features.

The coefficient assigned to each of these features gives us information about the influence of this feature on the prediction.

This is very important information, as shown:

```python
print("coef values :")
dict(zip(list(X_test.iloc[:, lst_coef].columns), rgr.coef_[lst_coef]))
```

Output:
```text
coef values :
{'Close_diff_frac_0.2_4': 0.0017052507726205356,
 'Close_diff_frac_0.25_4': 0.03357515414777998,
 'Close_diff_frac_0.3_4': 0.013239358125294583,
 'Close_diff_frac_0.35_1': 0.08641385813114096,
 …
 'CCI': -0.055638867385273676,
 'BBB_20_2.0': 0.06799642558179593,
 'BBP_20_2.0': 0.34890179044959546,
 'ATR': -0.008401739981565862,
 'TR': -0.1300218401488396}
```

The application of the ridge method gives us a close result. As a good exercise, you can verify this statement without any difficulties with ridge implementation in the Scikit-Learn API:

```python
from sklearn.linear_model import Ridge
```

With this ridge regression method, we obtain a regression score of 0.7, which is not as good as the previous LASSO method but still correct.

Now, transition to the kernel method to discover if this non-linear method improves the result given by LASSO.

## Kernel methods

Kernel methods allow us to find patterns in data that is not linearly separable—that is, when you cannot draw a straight line to separate different classes. It relies on a trick[^1] that transforms the data into a higher-dimensional space where these classes can be separated by a hyperplane. It is like viewing the data through a set of new lenses that reveal structures not visible in the original dimensions, allowing for accurate classifications.

Having already addressed the labor-intensive tasks of data preparation and feature engineering, we can now proceed directly to the task at hand, optimizing the hyperparameters of our model to fine-tune its performance:

```python
from sklearn.kernel_ridge import KernelRidge

# hyperparameter search space
space = {
    # log scale for regularization strength
    'alpha': Real(0.001, 10, prior='log-uniform'), 
    'kernel': Categorical(['linear', 'rbf', 'polynomial', 'sigmoid']), 
    # kernel coefficient
    'gamma': Real(0.001, 10, prior='log-uniform'), 
    # Extended range for 'polynomial' kernel degree
    'degree': Integer(2, 10), 
    # 'coef0', a parameter for 'polynomial' and 'sigmoid' kernels
    'coef0': Real(0, 10, prior='uniform'),
}
```

Next, we print the result of the optimization (characteristics of the model, choice of the kernel, and coefficients):

```python
print("best params: ")
pprint(opt.best_params_)
```

Output:
```text
best params: 
OrderedDict([('alpha', 1.3324499412363422),
 ('coef0', 10.0),
 ('degree', 2),
 ('gamma', 0.0016201598106302523),
 ('kernel', 'polynomial')])
```

```python
best_model = opt.best_estimator_
accuracy = best_model.score(X_test, y_test)
print(f"score:", accuracy * 100.0)
```

Output:
```text
score: 80.30608312013042
```

The fact that both non-linear kernel methods and LASSO yield similar results after hyperparameter optimization suggests that computing the normalized spread may fundamentally be a linear problem. This implies that the underlying relationship between the features and the target variable can be effectively captured through linear models, which LASSO is specifically designed to optimize.

The final section of this chapter explores online learning, a method specifically developed to apply machine learning techniques to streaming data. This approach updates the model incrementally as new data arrives, making it ideal for situations where it is impractical to store or reprocess large volumes of data.

## Online learning methods

Online machine learning is an adaptive strategy where the model is trained incrementally, processing individual samples or small batches of data sequentially as they become available. This method is particularly useful in environments where data is continuously generated, making it infeasible to retrain a model from scratch with every new piece of information.

[^1]: Reference to footnote 17 in original text.
