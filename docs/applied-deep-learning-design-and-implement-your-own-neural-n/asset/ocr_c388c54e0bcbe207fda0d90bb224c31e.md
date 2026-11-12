For MLE, it is convenient to maximize the log of L rather than L itself. A log is a monotonically increasing function, the following holds:

log L = \sum_{n=1}^N log[\frac{1}{\sqrt{2\pi\sigma^2}} exp (\frac{-1}{2\sigma^2}(t_n - y_n)^2)]

As

log (m * n) = log m + log n

Applying equation (3.8) in equation (3.7), we get as follows:

log L = \sum_{n=1}^N [log \frac{1}{\sqrt{2\pi\sigma^2}} + log * exp (\frac{-1}{2\sigma^2}(t_n - y_n)^2)]

log L = \sum_{n=1}^N [log \frac{1}{\sqrt{2\pi\sigma^2}} + \frac{-1}{2\sigma^2}(t_n - y_n)^2]

(log L) = \sum_{n=1}^N C_1 - C_2 \sum_{n=1}^N (t_n - y_n)^2

Where, \( C_1 = log \frac{1}{\sqrt{2\pi\sigma^2}} \) (constant_1) and \( C_2 = \frac{-1}{2\sigma^2} \) (constant_2). As \( t_n \) (target) and \( y_n \) (predicted) are as much as closer to each other, the value of the squared error function \( \sum_{n=1}^N(t_n - y_n)^2 \) becomes minimum. Hence, as the amount of squared error function gets reduced, the value log-likelihood is maximum as per the equation \( (log L) = \sum_{n=1}^N C_1 - C_2 \sum_{n=1}^N(t_n - y_n)^2 \). Finally, to minimize the value of squared error function, the values of \( t_n \) and \( y_n \) must be close to each other. Moreover, if the predicted value is near to actual value, then it leads to maximum log-likelihood.

In binary classification, we use binary cross-entropy cost function instead of squared error.

L = -\frac{1}{N} \sum_{n=1}^N t_n log(y_n) + (1 - t_n) log(1 - y_n)

Log-likelihood equivalence of binary cross-entropy is as follows:

t_n ~ Bernoulli(y_n)

L = \prod_{n=1}^N y_n^{t_n} * (1 - y_n)^{(1-t_n)}

-Log(L) = - \sum_{n=1}^N t_n log(y_n) + (1 - t_n) log(1 - y_n)

Categorical cross-entropy loss function using Bernoulli's distribution