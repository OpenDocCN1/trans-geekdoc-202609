
for $i = 1, \dots, n$. We will frequently use the more general form $r_i = y_i - \mathbf{x}_i^\top \boldsymbol{\beta}$ for convenience. Then, the $L_1$ loss function is the sum of the absolute values of the residuals, given by

$L_1 \text{ loss} = \sum_{i=1}^n |r_i|,$ (2.4.5)

while the $L_2$ loss function is half the sum of the squares of the residuals, given by

$L_2 \text{ loss} = \frac{1}{2} \sum_{i=1}^n r_i^2.$ (2.4.6)

Minimizing the $L_1$ loss is commonly referred to as least absolute deviation (LAD) while minimizing the $L_2$ loss is called least squares estimation (LSE). These loss functions are minimized to obtain their respective estimates of $\beta_0$ and $\beta_1$ which may be quite different. We will derive both functions and explore their differences shortly.

**Exercise:** Assume that we know the true values of the regression parameters to be $\beta_0 = 3$ and $\beta_1 = 1$. Using LSE, we find that $\hat{\beta}_0 = 3.2$ and $\hat{\beta}_1 = 1.1$. Compute the residuals and errors (the two are different) assuming that $\mathbf{y} = (3.3, 4.1, 5.5)^\top$ and $\mathbf{x} = (0, 1, 2)^\top$.

**Ans.:** The residuals are given by $r_i = y_i - (\hat{\beta}_0 + \hat{\beta}_1 x_i): r_1 = 3.3 - (3.2 + 1.1 \times 0) = 0.1, r_2 = 4.1 - (3.2 + 1.1 \times 1) = -0.2, \text{ and } r_3 = 5.5 - (3.2 + 1.1 \times 2) = 0.1$. On the other hand, the errors are given by $\epsilon_i = y_i - (\beta_0 + \beta_1 x_i): \epsilon_1 = 3.3 - (3 + 1 \times 0) = 0.3, \epsilon_2 = 4.1 - (3 + 1 \times 1) = 0.1, \text{ and } \epsilon_3 = 5.5 - (3 + 1 \times 2) = 0.5$. Note that ideally $\sum r_i = 0$ (a property of least squares), whereas $\sum \epsilon_i = 0.9 \neq 0$.

**Note:** It is important to recognize that the roots of machine learning lie in the field of probability and statistics. The fundamentals of probability distributions, estimators and estimation, convexity and convergence, and error measures are all based on theoretical underpinnings provided in this field. Essentially, they ensure that the ML techniques will work; that is, they will converge to the desired values with a certain amount of assurance and a certain level of accuracy. As such, it is necessary to cover the basics of probability and statistics as it relates to the subject matter at hand.

### 2.4.3 Distribution of Residuals

We are now ready to carry out a statistical analysis of the probability distribution of regression errors. Since we do not have access to the true errors, our focus will be on the residuals which we can compute after estimation. The starting point of the statistical analysis is to examine the properties of random variables because the residuals are themselves random variables. In this section, we use $X$ as a generic random variable but you should view it as the random variable representing residuals. More formally, we define $X$ as an independent and identically distributed (i.i.d.) random variable (r.v.). This type of assumption will be carried throughout the book.

A random variable may be distributed in a variety of different ways. The probability density function (PDF) specifies a continuous distribution denoted by $f_X(x)$. The cumulative distribution function (CDF) gives the probability that the random variable is less than a particular value and is denoted as $F_X(x)$. These two functions are directly related to one another. If we know the CDF, we can obtain the PDF by differentiation:

$f_X(x) = \frac{dF_X(x)}{dx}$.
(2.4.7)

Likewise, if we know the PDF, we can integrate to obtain the CDF. That is,

$F_X(x) = \mathbb{P}(X \le x) = \int_{-\infty}^x f_X(t)dt$.
(2.4.8)

Recall that the Gaussian distribution has a PDF given by:

$f_X(x) = \frac{1}{\sqrt{2\pi\sigma^2}} e^{-\frac{x^2}{2\sigma^2}}$
(2.4.9)

where \(\sigma^2\) is the variance. A random variable, \(X\), is said to follow a Gaussian distribution if any sample of \(X\) is distributed according to the equation above. The compact notation used for random variable \(X\) following a Gaussian distribution is

\(X \sim \mathcal{N}(0, \sigma^2)\).
(2.4.10)

Here, the \(\mathcal{N}\) symbol refers to the normal distribution and, inside the parentheses, 0 is the mean and \(\sigma^2\) is the variance. In some sense, both Eq. (2.4.9) and Eq. (2.4.10) are saying the same thing; one is just a compact version of the other. The normal distribution is important for a variety of reasons but for our purposes, it leads to the \(L_2\) loss function which is not tolerant to outliers.

Another important but less well-known distribution is the Laplace distribution, which is commonly referred to as the double-exponential distribution. The basic form is given by

$f_X(x) = \frac{1}{2} e^{-|x|}$.
(2.4.11)

The interesting part for our purposes is that this distribution leads us to the \(L_1\) loss function which is tolerant to outliers in the dataset. For this reason, we will be encountering this distribution several times in this and other chapters.

The distribution of well-behaved errors is usually taken to be \(\epsilon \sim \mathcal{N}(0, \sigma^2)\). That is, the mean is always zero but the variance may differ from dataset to dataset. The tacit assumption is that the residuals of linear regression follow a Gaussian distribution. Outliers cause the distribution to depart from this standard assumption which is why robust methods, involving the use of the \(L_1\) loss, are considered. This is a subtle but important point. If the residuals are not normally distributed, then robust methods are likely to produce better results.

Two quantities of great interest when working with probability distributions are the expected value and the variance. The expected value of \(X\) is the first moment of the PDF, given by

\(\mathbb{E}[X] = \int_{-\infty}^{\infty} x f_X(x) dx\).
(2.4.12)

We use the notation \(\mathbb{E}[X]\) for convenience to represent this integral. It can be viewed as the expected value operator \(\mathbb{E}[\cdot]\) acting on \(X\). In simpler terms, this is the value you would expect if you ran an experiment of independently selecting \(X\) a large number of times (approaching infinity) and then taking the average. It is commonly known as the mean of the distribution. We are also interested in the second moment as follows:

\(\mathbb{E}[X^2] = \int_{-\infty}^{\infty} x^2 f_X(x) dx.\)

The reason for our interest in the second moment is that the variance can be expressed in terms of this quantity. In particular, the variance of X can be expressed using the two expectations above as

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2;\)

that is, the second moment minus the first moment squared is the variance. Intuitively, this gives us a measure of spread or variability of the random variable about the mean.

For those unfamiliar with the expectation represented as \(\mathbb{E}[X]\), there is a simple way to think about it. Every time it is encountered, view E as an averaging operator on X. If you draw \(x_i\) (an observation of X) from a distribution n times, then the average, \(\frac{1}{n} \sum_{i=1}^n x_i\), is an estimate of the expectation. Now if you draw \(x_i\) an infinite number of times and take the average, you obtain the true mean of the distribution which is expressed as \(\mathbb{E}[X]\). More rigorously,

\(\lim_{n \to \infty} \frac{1}{n} \sum_{i=1}^n x_i = \mathbb{E}[X].\)

In the case of \(\mathbb{E}[X^2]\), it can be viewed simply as \(\frac{1}{n} \sum_{i=1}^n x_i^2\), where n goes to infinity. More rigorously,

\(\lim_{n \to \infty} \frac{1}{n} \sum_{i=1}^n x_i^2 = \mathbb{E}[X^2].\)

These results follow directly from the Law of Large Numbers and limit theory.

## 2.5 Estimation Background

Having described the goals of linear regression, the models, the errors, the residuals, and two competing loss functions, we will now step back and build up the knowledge of how to derive the functions that will lead to the estimates of the slope and intercept. We will briefly explore desirable characteristics of estimators and how to use them for comparison purposes. This section concludes with a rudimentary description of numerical optimization using gradient descent which is how the estimates are actually computed.

### 2.5.1 Linear Models

For problems with one explanatory variable, the equation was shown earlier to be

\(\mathbf{y} = \beta_0 + \beta_1 \mathbf{x}_1 + \varepsilon = \mathbf{X}\beta + \varepsilon.\)

This is referred to as the **simple linear model**. For problems with more than one variable, the equation becomes

\(\mathbf{y} = \beta_0 + \beta_1 \mathbf{x}_1 + \beta_2 \mathbf{x}_2 + \cdots + \beta_d \mathbf{x}_d + \varepsilon = \mathbf{X}\beta + \varepsilon.\)

This is referred to as the **multiple linear model**. If there are n observations and d variables, then \(\mathbf{y} \in \mathbb{R}^n\), \(\beta \in \mathbb{R}^{d+1}\), \(\mathbf{X} \in \mathbb{R}^{n \times (d+1)}\), and \(\varepsilon \in \mathbb{R}^n\). The only difference relative to the simple linear model is that we
