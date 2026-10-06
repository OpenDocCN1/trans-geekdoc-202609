# Derivation of gradient descent equation

The update equation for the gradient descent is derived from the first derivative of the loss function as

```
$$\hat{w}^{(n+1)} = \hat{w}^{(n)} - \eta \frac{\partial L(\\hat{w}^{(n)})}{\partial \hat{w}^{(n)}}$ (3.8)$
```

We have already derived the first derivative of the sum of squared errors loss $\frac{\partial L(w)}{\partial w}= -X^T(\mathbf{y}-X\mathbf{w})$ which results in Eq. (3.7).

# 3.1.3 Measuring performance of multivariate regression

The most intuitive measure of performance of the regression model is the **root squared error (RMSE)** defined as

```
$RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2}.$ (3.9)$
```

It is closely related to the sum of squared errors **L(w)**: $RMSE = \sqrt{\frac{2}{N}} L(w)$. Because it is normalized by the number of samples $N$ and the square root taken, it offers a meaningful measure of error in the units of the target value. For example, target values represent the GA of a baby in weeks, RMSE is also an average error in weeks. To achieve the best performance of the model, we need to minimize the RMSE and the best possible RMSE is zero. This is in contrast to $R^2$ score, which measures the proportion of variance in the data explained by the model (see Sect. 2.2.1) that we wish to maximize, and the best possible value is one. In scikit-learn we can calculate the RMSE of a regression model using the function `mean_squared_error`:

```
from sklearn.metrics import mean_squared_error
from sklearn.linear_model import LinearRegression
model = LinearRegression()
model.fit(X_train,y_train)
y_pred_train = model.predict(X_train)
RMSE_train = np.sqrt(mean_squared_error(y_train,y_pred_train))
```

This code calculates how well the model fits the training data, and therefore it measures bias. To identify overfitting, we can use cross-validation, but this time we define a scoring function `scoring=-neg_mean_squared_error`:

```
from sklearn.model_selection import cross_val_score
model = LinearRegression()
scores = cross_val_score(model,X_train,y_train,
  scoring='neg_mean_squared_error')
```

```
RMSE_CV = np.sqrt(-np.mean(scores))
```