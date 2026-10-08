# Application of U-Net in 3D Steady Heat Conduction Solver

0-1 loss function is the simplest loss function, which can be defined as

```
$L(y, f(x)) = \begin{cases} 1 & y \neq f(x) \ 0 & y = f(x) \end{cases} \quad (2.37)$
```

0-1 loss function is easy to calculate and hence commonly used in perceptrons. However, since it is not a convex function, it cannot be used directly in machine learning.

+   * B. Cross-entropy loss function

Cross entropy loss function is the most commonly used loss function in binary classification, which is defined

```
$L(y, f(x)) = \sum_{i=1}^{n} y_i \log(f(x_i)) + (1 - y_i) \log(1 - f(x_i)) \quad (2.38)$
```

This function is often combined with Sigmoid activation function to solve the gradient saturation problem.

+   * C. Hinge loss function

The standard form of the Hinge loss function is as follows:

```
$L(y, f(x)) = \max(0, 1 - y(x)) \quad (2.39)$
```

This function has good robustness and is insensitive to outliers and noise. However, the defect is the lack of theoretical support from probability.

+   * D. Exponential loss function

The definition of the exponential loss function is as follows

```
$L(y, f(x)) = \sum_{i=1}^{n} e^{-y_i f(x_i)} \quad (2.40)$
```

This function is adopted in Adaaboost. From the perspective of training, the function will be inclined to punish outliers and endow them with greater weight, which is at the expense of the prediction effect of normal data points and may reduce the overall performance of the model or reduce the robustness.

Figure 2.16 shows the curves of the four functions mentioned above, which are mainly used for classification problems. For regression problems, several commonly used loss functions are also listed below:

+   * A. Mean square loss