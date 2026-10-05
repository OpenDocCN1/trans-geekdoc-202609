
# Fitting A Model over Multiple Datasets: p = 0

![](img/99defe26aebed215976e83d281581f33_30_0.png)

Let's combine all of these hypotheses together into one picture to see the bias and variance of our model.

# Bias and Variance in Model Selection: p = 0

![](img/99defe26aebed215976e83d281581f33_30_1.png)

On the top left diagram we see all of our hypotheses and all training sets used. The bottom left diagram shows the average hypothesis in cyan. As we can see, this model has low bias for $x$'s in the center of the graph, but very high bias for $x$'s that are away from the center of the graph. the diagram in the bottom right shows that the variance of the hypotheses is quite high, for all values of $x$.

Now let's look at a 1st degree (linear) regression model.

# Fitting A Model over Multiple Datasets: $p = 1$

![](img/99defe26aebed215976e83d281581f33_31_0.png)

# Bias and Variance in Model Selection: $p = 1$

![](img/99defe26aebed215976e83d281581f33_31_1.png)

The bias is now very low bias for all $x$'s. The variance is low for $x$'s in the middle of the graph, but higher for $x$'s that are away from the center of the graph.

## 2.2 BIAS-VARIANCE TRADEOFF

Finally, let's look at a 2nd degree (quadratic) regression model.

# Fitting A Model over Multiple Datasets: p = 2

![](img/99defe26aebed215976e83d281581f33_32_0.png)

# Bias and Variance in Model Selection: p = 2

![](img/99defe26aebed215976e83d281581f33_32_1.png)

The bias is still very low for all $x$'s. However, the variance is much higher for all values of $x$.

Let's summarize our results. We find the bias and the variance empirically and graph them for all values of $x$, as shown in the first two graphs. Finally, we take an expectation over the bias and variance over all values of **$x$**, as shown in the third graph.

![](img/99defe26aebed215976e83d281581f33_33_0.png)

# Takeaways

Let us consider by stating some implications of the Bias-Variance Decomposition:

- 1. Underfitting is equivalent to high bias; most overfitting correlates to high variance.
- 2. Training error reflects bias but not variance. Test error reflects both. In practice, the training error is much smaller than the test error, then there is overfitting.
- 3. Variance $\rightarrow 0$ as $n\rightarrow\infty$.
- 4. If $f$ is in the set of hypothesis functions, bias will decrease with more data. If $f$ is not in the set of hypothesis functions, then there is an underfitting problem and more data won't help.
- 5. Adding good features will decrease the bias, but adding a bad feature rarely increase the bias (just set the coefficient of the feature to 0).
- 6. Adding a feature usually increase the variance, so a feature should only be added if it decreases bias more than it increases variance.
- 7. Irreducible error can not be reduced.
- 8. Noise in the test set only affects Var(N), but noise in the training set also affects bias and variance.
- 9. For real-world data, $f$ is rarely known, and the noise model might be wrong, so we cannot calculate bias and variance. But we can test algorithms over synthetic data.

## 2.3 Weighted Least Squares

So far we used MLE in the context of Gaussian noise to justify the optimization formulation of regression problems, such as OLS. Let's apply this dual optimization-probability philosophy to other regression problems, such as Weighted Least Squares.

### Optimization View

The basic idea of weighted least squares is the following: we place more emphasis on the loss contributed from certain data points over others - that is, we care more about fitting some data points over others. From an optimization perspective, the problem can be expressed as:

$$w_{WLS} = \arg\min_{w \in \mathbb{R}^d} \sum_{i=1}^n \omega_i(y_i - x_i^T w)^2$$

This objective is the same as OLS, except that each term in the sum is weighted by a coefficient $\omega_i$. As always, we can vectorize this problem:

$$w_{WLS} = \arg\min_{w \in \mathbb{R}^d} (y - Xw)^T \Omega (y - Xw)$$

Where the $i$'th row $X$ is $x_i^T$, and $\Omega \in \mathbb{R}^{n \times n}$ is a diagonal matrix with $\Omega_{i,i} = \omega_i$. We rewrite the WLS objective as

$$w_{WLS} = \arg\min_{w \in \mathbb{R}^d} (y - Xw)^T \Omega^{1/2} \Omega^{1/2} (y - Xw)$$
$= \arg\min_{w \in \mathbb{R}^d} (\Omega^{1/2}y - \Omega^{1/2}Xw)^T (\Omega^{1/2}y - \Omega^{1/2}Xw)$$

This formulation is identical to OLS except that we have the data matrix and the observation vector by $\Omega^{1/2}$, we conclude that

$$w_{WLS} = ((\Omega^{1/2}X)^T (\Omega^{1/2}X))^{-1} (\Omega^{1/2}X)^T \Omega^{1/2}y = (X^T\Omega X)^{-1} X^T\Omega y$$

### Probabilistic View

As in MLE, we assume that our observations $y$ are noisy; now suppose some of $y_i$ are more noisy than others. How can we take this into account in our learning algorithm so we get a better estimate of the weights? Our probabilistic model looks like $y_i = x_i^T w + Z_i$, where the $Z_i$ are still independent Gaussians, but not necessarily identical $Z_i \sim \mathcal{N}(0, \sigma_i^2)$. We can morph the problem into an MLE by scaling the data to make sure all $Z_i$'s are identically distributed by dividing by $\sigma_i$:

$$\frac{y_i}{\sigma_i} = \frac{x_i^T w}{\sigma_i} + \frac{Z_i}{\sigma_i}$$

Note that the scaled noise are now i.i.d: $\frac{Z_i}{\sigma_i} \overset{i.i.d}{\}\mathcal{N}(0,1)$. We rewrite our original as a scaled MLE problem:

$$w_{WLS}^* = \arg \min_{w \in \mathbb{R}^d} \sum_{i=1}^n \frac{(\frac{y_i}{\sigma_i} - \frac{x_i^T w}{\sigma_i})^2}{2} + n \log \sqrt{2\pi}$$

The MLE estimate of this scaled problem is equivalent to OLS of the original problem:

$$w_{WLS}^* = (\mathbf{X}^T \Sigma_z^{-1} \mathbf{X})^{-1} \mathbf{X}^T \Sigma_z^{-1} \mathbf{y}$$

where

$$\Sigma_z = \begin{bmatrix} \sigma_1^2 & 0 & \dots & 0 \\ 0 & \sigma_2^2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \sigma_n^2 \end{bmatrix}$$

Note that as no $\sigma_i=0$, $\Sigma_z$ is invertible. Note that $\omega_i$ from the optimization perspective is directly related to $\sigma_i^2$ from the probabilistic perspective: $\omega_i = \frac{1}{\sigma_i^2}$. As the variance $\sigma_i^2$ of the noise corresponding to data point $i$ decreases, the weight $\omega_i$ increases: we are more concerned about fitting data point $i$ because it is likely to match the true denoised point. Inversely, as the variance $\sigma_i^2$ increases, the weight $\omega_i$ decreases: we are less concerned about fitting data point $i$ because it is noisy and should not be trusted.

### Dependent Noise

If the $Z_i$'s aren't independent? This usually happens for time series data. Again, we assume a model for how the noise behaves. The noise entries are not independent, but there is a known process: e.g. $y_{i+1} = rZ_i + U_i$ where $U_i \sim \mathcal{N}(0,1)$, i.i.d, $-1 \le r \le 1$ (so that it doesn't blow up) or a "sliding window" example (like echo of audio) where $Z_i = \sum r_j U_{i-j}, U_i \sim \mathcal{N}(0,1)$.

## 2.4 Gaussians

In general, we can always represent the noise as $\mathbf{Z} = \mathbf{RU}$ where $\mathbf{Z} \in \mathbb{R}^n, \mathbf{R} \in \mathbb{R}^{n \times n}, \mathbf{U} \in \mathbb{R}^n$, and $\mathbf{U}_i \overset{i.i.d}{\}\mathcal{N}(0,1)$. $\mathbf{Z}$ is a Jointly Gaussian Random Vector. Our goal now is to derive its probability density formula.

There are three equivalent definitions of a jointly Gaussian (JG) random vector:

- 1. A random vector $\mathbf{Z} = (Z_1, Z_2, \dots, Z_k)^T$ is JG if there exists a base random vector $\mathbf{U} = (U_1, U_2, \dots, U_l)$ whose components are independent standard normal random variables, a transition matrix $\mathbf{R} \in \mathbb{R}^{k \times l}$, and a mean $\mu \in \mathbb{R}^k$, such that $\mathbf{Z} = \mathbf{RU} + \mu$.
- 2. A random vector $\mathbf{Z} = (Z_1, Z_2, \dots, Z_k)^T$ is JG if $\sum_{i=1}^k a_i Z_i$ is normally distributed for every $a = (a_1, a_2, \dots, a_k)^T$. A random vector $\mathbf{Z} = \mathbf{RU} + \mu$ is
- 3. (Non-degenerate case) $\mathbf{Z} = (Z_1, Z_2, \dots, Z_k)^T$ is JG if $f_{\mathbf{Z}}(\mathbf{z}) = \frac{1}{\sqrt{(2\pi)^k\det(\Sigma)}} e^{-\frac{1}{2}(\mathbf{z}-\mu)^T\Sigma^{-1}(\mathbf{z}-\mu)}$ where $\Sigma = \begin{bmatrix} \sigma_1^2 & 0 & \dots & 0 \\ 0 & \sigma_2^2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & \dots & \sigma_n^2 \end{bmatrix}$.

Note that as no $\sigma_i=0$, $\Sigma_z$ is invertible. Note that $\omega_i$ from the optimization perspective is directly related to $\sigma_i^2$ from the probabilistic perspective: $\omega_i = \frac{1}{\sigma_i^2}$. As the variance $\sigma_i^2$ of the noise corresponding to data point $i$ decreases, the weight $\omega_i$ increases: we are more concerned about fitting data point $i$ because it is likely to match the true denoised point. Inversely, as the variance $\sigma_i^2$ increases, the weight $\omega_i$ decreases: we are less concerned about fitting data point $i$ because it is noisy and should not be trusted.

# Proving (1) $\implies (3)$

In the context of the problem we defined earlier, we are starting with condition (1), i.e. $\mathbf{Z} = \mathbf{RU}$ (in this case $l=n$), and we would like to derive the probability of $\mathbf{Z}$. Note that we removed the $\mu$ from consideration in machine learning we always assume that the noise has a mean of 0. We leave it as an exercise for the reader to prove the case for arbitrary $\mu$.
