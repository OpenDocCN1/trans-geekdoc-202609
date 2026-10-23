
Suppose, for simplicity, that \( \sigma^{2}=1 \) and we set \( \boldsymbol{\mu}=\mathbf{0} \). Hence

\( \hat{\boldsymbol{\theta}}=\left(1-\lambda\right) \mathbf{x} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (\mathrm{E}.96) \)

From Eq. (E.185), we have that

\( \hat{r}^{2}+1=\frac{1}{K} \sum_{k=1}^{K} x_{k}^{2}=\frac{1}{K}\|\mathbf{x}\|^{2} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (\mathrm{E}.97) \)

and hence

\( \lambda=\frac{1}{1+\hat{r}^{2}} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (\mathrm{E}.98) \)

Hence

\( \hat{\boldsymbol{\theta}}_{E B}=\left(1-\lambda\right) \mathbf{x}=\frac{\hat{r}^{2}}{1+\hat{r}^{2}} \mathbf{x}=\left(1-\frac{K}{\|\mathbf{x}\|^{2}}\right) \mathbf{x} \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad \quad (\mathrm{E}.99) \)

which matches Eq. (E.94) when \( \sigma^{2}=1 \).

## E.5.4.3 Why is it called a “paradox”?

Suppose we set \( \boldsymbol{\mu}=\bar{x} \mathbf{1} \), where \( \bar{x}=\frac{1}{K} \sum_{k=1}^{K} x_{k} \) is the average of all the observations. This is a reasonable thing to do if the observations are related, since we can pool information from across multiple sources. However, this estimate will have lower risk than the sample mean even if the observations are unrelated. This can lead to paradoxical behavior. For example, suppose we want to estimate the speed of light, tea consumption in Taiwan, hog weight in Montana, and the rainfall in Vancouver. $ ^{2} $ The average of these quantities, \( \bar{x} \), is not very meaningful. Nevertheless, if we want to estimate the joint vector of parameters \( \boldsymbol{\theta} \), the shrinkage estimator with \( \boldsymbol{\mu}=\bar{x} \mathbf{1} \) will reduce the MSE compared to the sample mean. However, any particular component (such as the speed of light) would improve for some parameter values, and deteriorate for others.

## E.6 Empirical risk minimization

In this section, we consider how to apply frequentist decision theory in the context of supervised learning.

### E.6.1 Empirical risk

In standard accounts of frequentist decision theory used in statistics textbooks, there is a single unknown ‘state of nature’, corresponding to the unknown parameters \( \boldsymbol{\theta}^{*} \) of some model, and we define the risk as in Eq. (E.78), namely \( R(\pi, \boldsymbol{\theta}^{*})=\mathbb{E}_{p(\mathcal{D}|\boldsymbol{\theta}^{*})}\left[\ell\left(\boldsymbol{\theta}^{*}, \pi(\mathcal{D})\right)\right]. \)

2. This example is based on https://en.wikipedia.org/wiki/James-Stein_estimator. See also [EM75].

In supervised learning, we have a different unknown state of nature (namely the output $y$) for each input $\mathbf{x}$, and our estimator $\pi$ is a prediction function $\hat{y}=f(\mathbf{x})$, and the state of nature is the true distribution $p^*(\mathbf{x},\mathbf{y})$. Thus the risk of an estimator as follows:

$$R(f,p^*)=R(f)\triangleq\mathbb{E}_{p^*(\mathbf{x})p^*(y|\mathbf{x})}[\ell(\mathbf{y},f(\mathbf{x}))]\tag{E.100}$$

This is called the **population risk**, since the expectations are taken wrt the true joint distribution $p^*(\mathbf{x},\mathbf{y})$. Of course, $p^*$ is unknown, but we can approximate it using the empirical distribution with $N$ samples:

$$p_D(\mathbf{x},\mathbf{y}|\mathcal{D})\triangleq\frac{1}{|\mathcal{D}|}\sum_{(\mathbf{x}_n,\mathbf{y}_n)\in\mathcal{D}}\delta(\mathbf{x}-\mathbf{x}_n)\delta(\mathbf{y}-\mathbf{y}_n)\tag{E.101}$$

where $p_D(\mathbf{x},\mathbf{y})=p_{\text{train}}(\mathbf{x},\mathbf{y})$. Plugging this in gives us the **empirical risk**:

$$R(f,\mathcal{D})\triangleq\mathbb{E}_{p_D(\mathbf{x},\mathbf{y})}[\ell(\mathbf{y},f(\mathbf{x}))]=\frac{1}{N}\sum_{n=1}^{N}\ell(\mathbf{y}_n,f(\mathbf{x}_n))\tag{E.102}$$

Note that $R(f,\mathcal{D})$ is a random variable, since it depends on the training set.

A natural way to choose the predictor is to use

$$\hat{f}_{\text{ERM}}=\argmin_{f\in\mathcal{H}}R(f,\mathcal{D})=\argmin_{f\in\mathcal{H}}\frac{1}{N}\sum_{n=1}^{N}\ell(\mathbf{y}_n,f(\mathbf{x}_n))\tag{E.103}$$

where we optimize over a specific **hypothesis space** $\mathcal{H}$ of functions. This is called **empirical risk minimization (ERM)**.

### E.6.1.1 Approximation error vs estimation error

In this section, we analyze the theoretical performance of functions that are fit using the ERM principle. Let $f^{**}=\argmin_f R(f)$ be the function that achieves the minimal possible population risk, where we optimize over all possible functions. Of course, we cannot consider all possible functions, so let us also define $f^*=\argmin_{f\in\mathcal{H}}R(f)$ to be the best function in our hypothesis space, $\mathcal{H}$. Unfortunately we cannot compute $f^*$, since we cannot compute the population risk, so let us finally define the prediction function that minimizes the empirical risk in our hypothesis space:

$$f_N^*=\argmin_{f\in\mathcal{H}}R(f,\mathcal{D})=\argmin_{f\in\mathcal{H}}\mathbb{E}_{p_{\text{train}}}[\ell(\mathbf{y},f(\mathbf{x}))]\tag{E.104}$$

**estimation error**, which measures the difference in estimated risks due to having a finite training set. We can approximate this by the difference between the training set error and the test set error, using two empirical distributions drawn from $p^*$:

$$\mathbb{E}_{p^*}[R(f_N^*) - R(f^*)] \approx \mathbb{E}_{p_{\mathrm{train}}}[\ell(y, f_N^*(x))] - \mathbb{E}_{p_{\mathrm{test}}}[\ell(y, f_N^*(x))] \tag{E.106}$$

This difference is often called the **generalization gap**.

We can decrease the approximation error by using a more expressive family of functions $\mathcal{H}$, but this usually increases the generalization error, due to overfitting. We discuss solutions to this tradeoff below.

### E.6.1.2 Regularized risk

To avoid the chance of overfitting, it is common to add a complexity penalty to the objective function, giving us the **regularized empirical risk**:

$$R_\lambda(f, \mathcal{D}) = R(f, \mathcal{D}) + \lambda C(f) \tag{E.107}$$

where $C(f)$ measures the complexity of the prediction function $f(x;\theta)$ and $\lambda \geq 0$, which is known as a **hyperparameter**, controls the strength of the complexity penalty. (We discuss how to pick $\lambda$ in Sec. [E.6.2](#e62).)

In practice, we usually work with parametric functions, and apply the regularizer to the parameters themselves. This yields the following form of the objective:

$$R_\lambda(\theta, \mathcal{D}) = R(\theta, \mathcal{D}) + \lambda C(\theta) \tag{E.108}$$

Note that, if the loss function is log loss, and the regularizer is a negative log prior, the regularized risk is given by

$$R_\lambda(\theta, \mathcal{D}) = -\frac{1}{N}\sum_{n=1}^{N}\log p(y_n\mid x_n, \theta) - \lambda\log p(\theta) \tag{E.109}$$

Minimizing this is equivalent to MAP estimation.

### E.6.2 Structural risk

A natural way to estimate the hyperparameters is to minimize for the lowest achievable empirical risk:

$$\hat{\lambda} = \underset{\lambda}{\arg\min}\;\underset{\theta}{\min}\;R_\lambda(\theta, \mathcal{D}) \tag{E.110}$$

(This is an example of **bilevel optimization**, also called **nested optimization**.) Unfortunately, this technique will not work, since it will always pick the least amount of regularization, i.e., $\hat{\lambda}=0$. To see this, note that

$$\underset{\lambda}{\arg\min}\;\underset{\theta}{\min}\;R_\lambda(\theta, \mathcal{D}) = \underset{\lambda}{\arg\min}\;\underset{\theta}{\min}\;R(\theta, \mathcal{D}) + \lambda C(\theta) \tag{E.111}$$
