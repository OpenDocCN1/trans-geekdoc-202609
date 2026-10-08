# Deep Learning-Based Forward Modeling and Inversion Techniques

![](bbox=[0.248, 0.091, 0.72, 0.255])

FIGURE 2.16
The curves of the four loss functions for classification problems.

The mean square loss is the most prevalent loss function in practice and is actually the-two norms of $y - f(x)$:

```
$L(y, f(x)) = rac{1}{n} \sum_{i=1}^{n} |y_i - f(x_i)|^2 \quad (2.41)$
```

+   - B. Mean absolute loss
The mean absolute loss calculates the average absolute value between the predicted value and the target value, that is, the I-norm of $y - f(x)$.

```
$L(y, f(x)) = rac{1}{n} \sum_{i=1}^{n} |y_i - f(x_i)| \quad (2.42)$
```

The absolute loss has the merits of high robustness, especially for outliers. However, it is unstable since it is not derivative at the origin.

+   - C. Mean square logarithmic loss
The mean square logarithmic loss is defined as

```
$L(y, f(x)) = \frac{1}{n} \sum_{i=1}^{n} |log y_i - f(x_i)|^2 \quad (2.43)$
```

The mean square logarithmic loss is applicable to the situation where there are large differences among samples.

+   - D. Huber loss
The Huber loss combines the mean square loss and the mean absolute loss, which is defined as

```
$L(y, f(x)) = \begin{cases} \frac{1}{2} |y - f(x)|^2, & |y - f(x)| \le \delta \ |y - f(x)| - \frac{1}{2}\delta^2, & |y - f(x)| > \delta \end{cases} \quad (2.44)$
```