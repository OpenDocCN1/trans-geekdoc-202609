
```python
n_samples = 100
x, y = sample(n_samples)
# x = np.sort(np.random.uniform(0, 1, n_samples))
# y = np.sin(2 * np.pi * x) + np.random.normal(scale=0.25, size=x.shape)

K = 9

X = np.array([np.power(x, k) for k in range(K + 1)])
X = X.transpose()

# w, history = gradient_descent_vec(X, y, lr, iterations)
XT = X.transpose()
XTy = XT @ y
w = np.linalg.inv(XT @ X) @ XTy
# w = np.linalg.pinv(X) @ y
print("w=:", w)

y_predict = 0  # np.zeros(x_test.shape)
for i, wi in enumerate(w):
    y_predict += wi * np.power(x_test, i)

plt.plot(x_test, y_test, c="g", label="$\sin(2\pi x)$")
plt.scatter(x, y, facecolor="none", edgecolor="b", s=50, label="training data")

y_test = np.sin(2 * np.pi * x_test)
plt.plot(x_test, y_test, c="g", label="$\sin(2\pi x)$")
plt.plot(x_test, y_predict, c="r", label="fitting")
plt.ylim(-1.5, 1.5)

plt.show()
```

```
w=: [ 1.22951941e-01 -3.80763635e-01 1.47730348e+02 -1.56658147e+03
      7.96745758e+03 -2.30639208e+04 3.91473296e+04 -3.84418223e+04
      2.02211373e+04 -4.41100990e+03]
```

![](EPUB/media/file56.png)

**Figure 3-19** The fitting situation of the 9th degree polynomial function with increasing training samples

**Figure 3-20** The left, middle, and right are underfitting, optimal fitting, and overfitting respectively

As shown in **Figure 3-20**, there is a group of two-dimensional coordinate points on the plane. Using a linear function (straight line), a quadratic function (parabola), and a high-degree polynomial as the model function of linear regression, it can be clearly seen that the left, middle, and right are respectively underfitting, optimal fitting, and overfitting. If the model is too simple, it will be underfitting; if it is too complex, it will be overfitting; and only when the complexity is appropriate can it produce an optimized fitting effect.

According to the analysis of the causes of underfitting and overfitting, the underfitting problem can be alleviated by the following methods:

*   **Add more sample features.** For example, by adding more sample features such as `x**2` and `x**3` from a sample feature `x`, it actually increases the complexity of the data and alleviates the underfitting problem.
*   **Increase model complexity:** such as choosing a more expressive hypothesis function (model) or reducing the degree of regularization.

The solution to the overfitting problem can be solved by the following methods:

*   **Add more training samples** to increase the amount of training data.
*   **Reduce the complexity of the model:** Limit the complexity of the hypothesis function (model) with a low-complexity hypothesis function (model) or through regularization.

### 3.2.2 Validation Set, Test Set

By visually displaying the training model function and real sample data, you can observe whether the model function is underfitting or overfitting, so that you can directly judge whether the model function fits well or not visually. However, this method is only suitable for very simple hypothetical functions that can be represented by curves and surfaces. Many practical problems have complex hypothetical functions and a large number of data features. For example, an image can have millions of features. The neural network function in deep learning has thousands of parameters. Such data samples and hypothetical functions cannot be visualized.

As can be seen from the previous examples, for such problems, it is often impossible to judge whether the final model function fits the data only based on the declining loss function curve. Even if a function has a small loss for the training sample, it may produce a large error for other samples that are not in the training set; that is, an overfitting problem will occur. In other words, the "generalization ability" of the model function is insufficient, and it cannot better express the relationship between the data characteristics of the actual sample and the target value. "Overfitting" occurs because the training model pays too much attention to how to better fit the training set, so the trained model will produce larger errors for data different from the training set. Of course, it is difficult to judge whether the model function is overfitting or underfitting only based on the value of the loss function. In some cases, even if the value of the loss function is small, it may be underfitting.

The purpose of training the model is to use the model to predict new data. Even if the model can fit the training data well, it is useless if the prediction effect on the new data is poor. Just as an athlete trains to be at the top of his team, there is no guarantee that he will perform as well against others.

In order to help judge whether a model function is overfitting or underfitting, in addition to the loss function curve, the quality of the model function is usually evaluated with the help of a sample set different from the training set.

Therefore, in machine learning, in addition to the training set used to train the model, a separate test set is generally used to evaluate the trained model. For a model function, the prediction error of the samples in the test set (that is, the error between the predicted value and the target value) can be calculated. If the error of the samples in the test set is similar to the error of the samples in the training set, it can be preliminarily judged that the model function has better generalization ability. The test set should cover a variety of different data as much as possible, so as to evaluate whether the trained model has good generalization ability.

In addition to the training set and the algorithm of the training model, the performance of different hypothetical function models is different. For example, in the previous problem of polynomial fitting of two-dimensional data points, the performance of the training model function obtained by polynomial functions of different degrees is different; some are underfitting and some are overfitting. In addition, the hyperparameters in the training algorithm (such as learning rate, batch size, number of iterations, etc.) also have a great impact on the training results. For example, when other conditions remain unchanged, the number of iterations directly affects the training error; a small number of iterations may lead to underfitting, and a large number of iterations may lead to overfitting.

Evaluating the prediction errors of different models through the validation set can help to select an appropriate hypothesis function and train hyperparameters, so as to obtain a training model with better generalization ability.

For example, when training the model, the loss (error) of the training set and the validation set can be calculated at the same time. When the training iteration starts, the validation error and the training error will continue to decrease from high to low. As the number of iterations increases, the validation set error, on the contrary, becomes larger, indicating that the generalization ability becomes worse. At this time, the iteration can be stopped as soon as possible. This method is called **early stopping**. That is, the validation set can be used to prevent too many iterations during training. For another example, for the previous polynomial fitting, if there is no visual help, the training error and validation error of the training set and the validation set on the polynomial model function of different degrees can be used to help select a polynomial function of an appropriate degree.

Thus, a training set is used to train the model, a validation set is used to evaluate and select the model, and sometimes a separate test set is used to test the resulting model. Sometimes the test and validation sets are not distinguished.

For the fitting problem of the previous sinusoidal sampling points, the following code samples a total of three sample sets: training set, validation set, and test set.
