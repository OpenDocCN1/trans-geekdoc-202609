
![](img/f26d7f591c2a080d86425985301266a4_96_0.png)

Figure 3.3 Comparing LS and LC using the Belgium telephone dataset of Chapter 2, Section 2.9.1. LS is affected by outliers while LC is tolerant of outliers.

portion are outliers due to differences in measurement techniques. In the case of LS, it is highly sensitive to these outliers and fails to produce an acceptable model. We notice that the line is greatly affected by the outliers, whereas the LC regression line fits the true data and effectively ignores the outliers. This is due to the fact that the LS method, which uses the L2 loss function, seeks the mean of the data (meaning the line that averages out the errors to 0), while the LC method seeks the median (meaning the line that has the same number of points above and below it). We can observe that LC is ignoring the outliers and capturing the essence of the inlier data. This provides the needed evidence that log-cosh is a robust estimator. With that knowledge, we can now go ahead and understand the detailed mathematics and characteristics of this loss function.

## 3.5 Deriving the Distribution for Log-Cosh

It is important to understand the log-cosh loss function from both theoretical and foundational perspectives in order to appreciate its true value. Therefore, we need to study probability-based statistical models associated with this loss function and relate the results to the underlying distributions. In this section, we show how to derive this loss function and then provide a more mathematically rigorous view of its origin.

The log-cosh loss function can be derived from a probability density function (PDF) using the maximum-likelihood procedure. The challenge is to figure out which probability distribution to use as a starting point when only the loss function is known. The goal in this section is to find the associated PDF, $f_X(x)$. To do this, consider the relationship between $f_X(x)$ and one term of the loss function, $\rho(x)$. Since we know that the maximum-likelihood procedure (after constants are removed) produces $\rho(x) = -\log f_X(x)$, then it follows that the **reverse MLE procedure** would require that

$$f_X(x) = \frac{1}{\kappa}e^{-\rho(x)},$$ (3.5.1)

where $\kappa$ is a normalization coefficient. Here, $f_X(x)$ is the PDF we seek. We should keep in mind that the distribution associated with a loss function must be centered at 0; in other words, we expect it to be symmetric about 0. Hence, the mean of the distribution is 0, or mathematically $\mathbb{E}[X] = 0$. The reverse MLE procedure can be applied to well-known loss functions, such as $L_1$, $L_2$, and Huber. We illustrate the steps for $L_1$ and $L_2$ in the following examples and leave the derivation of the Huber distribution as an exercise for the reader.

**Example**: To find the distribution associated with the $L_1$ loss function, we begin with the term

$$\rho_{L_1}(x) = |x|.$$

Then we apply the reverse MLE rule above to obtain

$$f_X(x) = \frac{1}{\kappa}e^{-|x|}.$$

We can find $\kappa$ as follows:

$$\kappa = \int_{-\infty}^{\infty} e^{-|x|} dx = 2.$$

Hence, the basic form of the distribution for the $L_1$ loss is

$$f_X(x) = \frac{1}{2}e^{-|x|},$$ (3.5.2)

which is called the *Laplace distribution*.

**Example**: To find the distribution associated with the $L_2$ loss function, we begin with the term

$$\rho_{L_2}(x) = x^2/2.$$

Then we apply the reverse MLE rule above to obtain

$$f(x) = \frac{1}{\kappa}e^{-x^2/2}.$$

We can find $\kappa$ as follows:

$$\kappa = \int_{-\infty}^{\infty} e^{-x^2/2} dx = \sqrt{2\pi}.$$

Hence, the basic form of the distribution for the $L_2$ loss function is

$$f_X(x) = \frac{1}{\sqrt{2\pi}}e^{-x^2/2},$$ (3.5.3)

which is, of course, the Gaussian distribution.

If we now apply the reverse MLE rule to the log-cosh loss, we start with

$$\rho_{LC}(x) = \log(\cosh(x)).$$

Then we apply the reverse MLE rule above to obtain

\(f(x) = \frac{1}{\kappa}e^{-\rho_{\text{LC}}(x)} = \frac{1}{\kappa}e^{-\text{log}(\text{cosh}(x))} = \frac{1}{\kappa} \frac{1}{\text{cosh}(x)}\) .

We can find \(\kappa\) as follows:

\(\kappa = \int_{-\infty}^{\infty} \frac{1}{\text{cosh}(x)} dx = \pi\) .

Hence, the basic form of the distribution associated with log-cosh is

\(f_X(x) = \frac{1}{\pi} \frac{1}{\text{cosh}(x)}\) . (3.5.4)

The resulting PDF is sometimes referred to as the *hyperbolic secant distribution* but we will use the term **Cosh distribution** to keep in mind its connection to the log-cosh loss function.

The cumulative distribution function (CDF) is obtained by integrating the PDF function up to some desired point, \(x\), as follows:

\(F_X(x) = \int_{-\infty}^{x} f_X(x)dx\) . (3.5.5)

For the Cosh distribution, the CDF is found using

\(F_X(x) = \int_{-\infty}^{x} \frac{1}{\pi} \frac{1}{\text{cosh}(x)} dx\) . (3.5.6)

Then, integrating and setting the constant of integration to 1/2, the CDF is given by:

\(F_X(x) = \frac{1}{2} + \frac{1}{\pi} \text{arctan}(\text{sinh}(x))\) . (3.5.7)

The CDF is plotted in Figure 3.4(a) along with the PDF in Figure 3.4(b).

More generally, we have a location-scale family of distributions of the form

\(f_X(x; \theta, \sigma) = \frac{1}{\pi\sigma \text{cosh}(\frac{x-\theta}{\sigma})},\) (3.5.8)

where \(\theta\) is the location parameter and \(\sigma\) is the scale parameter (not to be confused with the standard deviation). We note here that

\(\mathbb{E}[X] = \theta \quad \text{and} \quad \mathbb{E}[X^2] = \frac{\pi^2\sigma^2}{4} + \theta^2\)

so the asymptotic variance of the distribution is

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = \frac{\pi^2\sigma^2}{4}.\) (3.5.9)

The location and scale parameters can be estimated from the data (i.e. residuals) as

\(\hat{\theta} = \frac{1}{n} \sum_{i=1}^n x_i \quad \text{and} \quad \hat{\sigma} = 2\sqrt{\widehat{\text{Var}(X)} / \pi},\) (3.5.10)

respectively, where

\(\widehat{\text{Var}(X)} = \frac{1}{n-1} \sum_{i=1}^n (x_i - \hat{\theta})^2.\) (3.5.11)

![](img/f26d7f591c2a080d86425985301266a4_99_0.png)

For the CDF, we have that

$$F_X(x; \theta, \sigma) = \frac{1}{2} + \frac{1}{\pi} \arctan \left( \sinh \left( \frac{x - \theta}{\sigma} \right) \right).$$

Typically, the location is 0 for distributions used to derive loss functions. Hence, for $\theta = 0$, the CDF is given by

$$F_X(x; \sigma) = \frac{1}{2} + \frac{1}{\pi} \arctan \left( \sinh \left( \frac{x}{\sigma} \right) \right).$$

It is interesting to compare the four main distributions we have mentioned thus far: Gaussian, Laplace, Huber, and Cosh. This is provided in Figure 3.5. Both Cosh and Huber ($\delta = 1.345$) look similar to one another, whereas Laplace and Gaussian are quite different. In robust statistics, the Laplace distribution is considered to have heavy tails. It is outlier-friendly because heavy tails imply a higher probability for the occurrence of outliers. That is, outliers are easily accommodated by the PDF of the Laplace distribution without affecting the model greatly, specifically, the mean and the variance. This makes it more robust to outliers. In contrast, the Gaussian distribution has light tails so outliers can have a significant effect on the mean and variance. Therefore, the Gaussian distribution is less suitable for outliers. Notice that the Cosh distribution has heavier tails which is similar to the Laplace distribution. In the case of Huber, the moderate tails are not as heavy as Cosh due to the fact that $\delta = 1.345$. However, it can be made heavier by reducing the value of $\delta$, or lighter by increasing its value.

The importance of the different distributions should now be clear. Each one has a different sensitivity to outliers. When we select a certain loss function, we are forcing the residuals of the regression to follow the associated probability distribution. Specifically, if we choose the $L_2$ loss function, the residuals will try to follow a Gaussian distribution (Eq. (3.5.3)). If we choose $L_1$, it will try to follow the Laplace distribution (Eq. (3.5.2)). A selection of log-cosh will follow the Cosh distribution (Eq. (3.5.4)), and a selection of Huber will follow some form of the Huber distribution, depending on $\delta$. The implications of this are profound in the sense that if we have outliers, we should not choose the $L_2$ loss function (which follows a Gaussian distribution) as it is highly sensitive to outliers. This was shown earlier in Figure 3.3. Fundamentally, this is why we seek robust loss functions that are more suitable for datasets with outliers.

![](img/f26d7f591c2a080d86425985301266a4_100_0.png)

Figure 3.5 Distributions for Laplace, Gaussian, Cosh, and Huber ($\delta = 1.345$).

## 3.6 Standard Errors for Robust Estimators

Standard error (s.e.) is a measure of the uncertainty around an estimate (see Montgomery et al. 2012). Since we know that different samples of a population will produce different estimates, it is desirable to get a handle on the degree of this uncertainty. In fact, it is possible to show that the estimates from a log-cosh estimator are asymptotically normal, meaning they follow a Gaussian distribution.$^2$ This makes life a lot easier since we can follow the usual procedures to obtain the standard errors, which is an estimate of the standard deviation of each parameter.

Consider the multiple linear regression model in matrix form as follows:

$y = X\beta + \epsilon, \qquad (3.6.1)$

where $y = (y_1, ..., y_n)^\top$ is a response vector, $X$ is an $n \times (d + 1)$ design matrix of constants with $X_1 = (1, ..., 1)^\top$, and $\epsilon = (\epsilon_1, ..., \epsilon_n)^\top$ is the error term. Regression parameters $\beta = (\beta_0, ..., \beta_d)^\top$ are the $d + 1$ coefficients of interest. Here we assume $\epsilon$ has some known distribution with mean $0 = (0, ..., 0)^\top$.

2 To be clear, the residuals follow the Cosh distribution while the estimates follow a Gaussian distribution.
