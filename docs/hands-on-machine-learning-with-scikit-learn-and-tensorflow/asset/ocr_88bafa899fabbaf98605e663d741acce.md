![](bbox=[0.149, 0.77, 0.85, 0.275])

The CART algorithm works mostly the same way as earlier, except that instead of splitting the training set in a way that minimizes impurity, it now tries to split the training set in a way that minimizes the MSE. Equation 6-4 shows the cost function that the algorithm seeks to minimize.

Equation 6-4. CART cost function for regression

```
$J(k, t_k) = \frac{m_{left}}{m}MSE_{left} + \frac{m_{right}}{m}MSE_{right} \text{ where } MSE_{node} = \sum_{i \in node} (\hat{y}_{node} - y^{(i)})^2 \n\hat{y}_{node} = \frac{1}{m_{node}} \sum_{i \in node} y^{(i)}$
```

Just like for classification tasks, Decision Trees are prone to overfitting when dealing with regression tasks. Without any regularization (i.e., using the default hyperparameters), you get the predictions on the left of Figure 6-6. It is obviously overfitting the training set very badly. Just setting $min\_samples\_leaf=10$ results in a much more reasonable model, represented on the right of Figure 6-6.

![](bbox=[0.149, 0.67, 0.85, 0.856])