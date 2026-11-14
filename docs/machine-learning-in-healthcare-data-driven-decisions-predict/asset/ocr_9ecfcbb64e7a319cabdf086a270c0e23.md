```
\hat{y}^{(t)} = \sum_{k=1}^t f_k(x_i), f_k \in F
```

where $f_k$ is the prediction function and $t$ is the current iteration. The objective function to minimize the regularized loss is as follows:

```
L^{(t)} = \sum_{i=1}^n l(y_i, \hat{y}_i^{(t)}) + \sum_{k=1}^t \Omega(f_k)
```

where $l$ is a differentiable loss function and $\Omega(f_k) = \gamma T + \frac{1}{2} \lambda ||w||^2$ is the regular term to penalize complexity. The regularization parameters are $\gamma$ and $\lambda$, the leaf weights are $w$, and the number of leaves is $T$. XGBoost approximates the loss in each iteration using second order Taylor expansion:

```
L^{(t)} \approx \sum_{i=1}^n \left[ g_i f_t(x_i) + \frac{1}{2} h_i f_t(x_i)^2 \right] + \Omega(f_t)
```

Here, $g_i$ and $h_i$ are given as follows:

```
g_i = \frac{\partial (y_i, \hat{y}_i)}{\partial \hat{y}_i} \quad h_i = \frac{\partial^2 (y_i, \hat{y}_i)}{\partial \hat{y}_i^2}
```

Next, the model determines the $f_t$ that minimizes this estimated goal.

# 4 Results and Findings

After data preprocessing and FS have been done, model training and validation are performed. Data are divided first into test and training sets. The 80/20 split, in which 80% of the data is used for training the model and 20% is used for testing, is probably the method that is most commonly employed. To improve the model, hyperparameter tuning is conducted using GridSearchCV or RandomSearchCV techniques. GridSearchCV iterates over a fixed list of hyperparameters, and RandomSearchCV samples hyperparameters randomly from a given range. Both the procedures help to determine the optimal model parameters and thereby the overall improvement. Some of the most important evaluation criteria are used to assess the model's performance after it has been trained are as follows.

Accuracy: True predicted divided by all predicted. It is a simple measure but misleading in imbalanced datasets:

```
\text{Accuracy} = \frac{(TP + TN)}{(TP + FP + TN + FN)}
```