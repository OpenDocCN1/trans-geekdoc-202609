```
y_val_predict = model.predict(X_val)
train_errors.append(mean_squared_error(y_train[:], y_train_predict))
val_errors.append(mean_squared_error(y_val, y_val_predict))
plt.plot(np.sqrt(train_errors), "r-", linewidth=2, label="train")
plt.plot(np.sqrt(val_errors), "b-", linewidth=3, label="val")
```

Let's look at the learning curves of the Linear Regression model (a straight line: **Figure 4-15):

```
lin_reg = LinearRegression()
plot_learning_curves(lin_reg, X, y)
```

![](bbox=[0.216, 0.252, 0.753, 0.506])

**Figure 4-15.** Learning curves

This is a bit of explanation. First, let's look at the performance on the training data: when there are just one or two instances in the training set, the model can fit them perfectly, which is why the curve starts at zero. As new instances are added to the training set, it becomes impossible for the model to fit the training data perfectly, because both the data is noisy and it is not linear at all. So the error on the training data goes up until it reaches a plateau, at which adding new instances to the training set doesn't make the error much better or worse. Now lets look at the performance of the model on the validation data. When the model is trained on very few training instances, it is incapable of generalizing properly, which is why the validation error is initially quite big. Then as the model shows more training examples, it learns and the validation error goes down. However, once again a straight line cannot do a good job modeling the data, so the error ends up at a plateau, very close to the other curve.

These learning curves are typical of an underfitting model. Both curves have reached a plateau; they are close and fairly high.