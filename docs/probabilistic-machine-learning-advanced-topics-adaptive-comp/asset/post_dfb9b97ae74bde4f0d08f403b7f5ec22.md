
Therefore, it can be seen from Equation (15.117) that given $\Sigma$, $\mathbf{W}$ follows a matrix normal distribution

$$
\mathbf{W}|\Sigma, \mathbf{X}, \mathbf{Y} \sim \mathcal{MN}(\mathbf{S}_{yx}\mathbf{S}_{xx}^{-1}, \Sigma, \mathbf{S}_{xx}).
$$ (15.120)

Marginalizing out $\mathbf{W}$ (which corresponds to removing the terms including $\mathbf{W}$ in the exponent in Equation (15.113)), it can be shown that the posterior distribution of $\Sigma$ is an inverse Wishart distribution. In fact, by replacing Equation (15.117) to the corresponding terms in Equation (15.113), it can be seen that the only terms left after integrating out $\mathbf{W}$ are $\Sigma^{-1}\Psi$ and $\Sigma^{-1}\mathbf{S}_{y|x}$, which indicates that the scale matrix of the posterior inverse Wishart distribution is $\Psi_0 + \mathbf{S}_{y|x}$.

In conclusion, the joint posterior distribution of $\{\mathbf{W}, \mathbf{\Sigma}\}$ given the observation is

$$
\mathbf{W}, \Sigma | \mathbf{X}, \mathbf{Y} \sim \text{MNIW}(\mathbf{M}_1, \mathbf{V}_1, \nu_1, \mathbf{\Psi}_1) \quad (15.121)
$$
$$
\mathbf{M}_1 = \mathbf{S}_{yx}\mathbf{S}_{xx}^{-1} \quad (15.122)
$$
$$
\mathbf{V}_1 = \mathbf{S}_{xx} \quad (15.123)
$$
$$
\nu_1 = N + \nu_0 \quad (15.124)
$$
$$
\mathbf{\Psi}_1 = \mathbf{\Psi}_0 + \mathbf{S}_{y|x} \quad (15.125)
$$

The MAP estimate of $\mathbf{W}$ and $\Sigma$ are the mode of the posterior matrix normal inverse Wishart distribution. To derive this, notice that $\mathbf{W}$ only appears in the matrix normal density function in the posterior, so the matrix $\mathbf{W}$ maximizing the posterior density of $\{\mathbf{W}, \mathbf{\Sigma}\}$ is the matrix $\mathbf{W}$ that maximizes the matrix normal posterior of $\mathbf{W}$. So the MAP estimate of $\mathbf{W}$ is $\hat{\mathbf{W}} = \mathbf{M}_1 = \mathbf{S}_{yx}\mathbf{S}_{xx}^{-1}$, and this holds for any value of $\Sigma$. By plugging $\mathbf{W} = \hat{\mathbf{W}}$ into the joint posterior of $\{\mathbf{W}, \mathbf{\Sigma}\}$, and taking derivatives over $\Sigma$, it can be seen that the matrix maximizing the density is $(\nu_1 + N_y + N_x + 1)^{-1}\mathbf{\Psi}_1$. Since $\mathbf{\Psi}_1$ is positive definite, it is the MAP estimate of $\Sigma$.

In conclusion, the MAP estimate of $\{\mathbf{W}, \mathbf{\Sigma}\}$ are

$$
\hat{\mathbf{W}} = \mathbf{S}_{yx}\mathbf{S}_{xx}^{-1} \quad (15.126)
$$
$$
\hat{\Sigma} = \frac{1}{\nu_1 + N_y + N_x + 1}(\mathbf{\Psi}_0 + \mathbf{S}_{y|x}) \quad (15.127)
$$

## 15.3 Logistic regression

**Logistic regression** is a very widely used discriminative classification model that maps input vectors $\mathbf{x} \in \mathbb{R}^D$ to a distribution over class labels, $y \in \{1, \dots, C\}$. If $C = 2$, this is known as **binary logistic regression**, and if $C > 2$, it is known as **multinomial logistic regression**, or alternatively, **multiclass logistic regression**.

### 15.3.1 Binary logistic regression

In the binary case, where $y \in \{0, 1\}$, the model has the following form

$$
p(y|\mathbf{x}; \boldsymbol{\theta}) = \text{Ber}(y|\sigma(\mathbf{w}^T\mathbf{x} + b)) \quad (15.128)
$$

where $\mathbf{w}$ are the weights, $b$ is the bias (offset), and $\sigma$ is the **sigmoid** or **logistic** function, defined by

$$
\sigma(a) \triangleq \frac{1}{1 + e^{-a}} \quad (15.129)
$$

Let \(\eta_n = \boldsymbol{w}^\mathsf{T}\boldsymbol{x}_n + b\) be the **logits** for example \(n\), and \(\mu_n = \sigma(\eta_n) = p(y=1|\boldsymbol{x}_n)\) be the mean of the output. Then we can write the log likelihood as the negative cross entropy:

\(\log p(\mathcal{D}|\boldsymbol{\theta}) = \log \prod_{n=1}^N \mu_n^{y_n} (1-\mu_n)^{1-y_n} = \sum_{n=1}^N y_n \log \mu_n + (1-y_n) \log(1-\mu_n)\) (15.130)

We can expand this equation into a more explicit form (that is commonly seen in implementations) by performing some simple algebra. First note that

\(\mu_n = \frac{1}{1+e^{-\eta_n}} = \frac{e^{\eta_n}}{1+e^{\eta_n}}, \quad 1-\mu_n = 1-\frac{e^{\eta_n}}{1+e^{\eta_n}} = \frac{1}{1+e^{\eta_n}}\) (15.131)

Hence

\(\log p(\mathcal{D}|\boldsymbol{\theta}) = \sum_{n=1}^N y_n[\log e^{\eta_n} - \log(1+e^{\eta_n})] + (1-y_n)[\log 1 - \log(1+e^{\eta_n})]\) (15.132)

\(= \sum_{n=1}^N y_n[\eta_n - \log(1+e^{\eta_n})] + (1-y_n)[-\log(1+e^{\eta_n})]\) (15.133)

\(= \sum_{n=1}^N y_n \eta_n - \sum_{n=1}^N \log(1+e^{\eta_n})\) (15.134)

Note that the \(\log(1+e^a)\) function is often implemented using `np.log1p(np.exp(a))`.

### 15.3.2 Multinomial logistic regression

**Multinomial logistic regression** is a discriminative classification model of the following form:

\(p(y|\boldsymbol{x};\boldsymbol{\theta}) = \text{Cat}(y|\text{softmax}(\boldsymbol{W}\boldsymbol{x} + \boldsymbol{b}))\) (15.135)

where \(\boldsymbol{x} \in \mathbb{R}^D\) is the input vector, \(y \in \{1, \dots, C\}\) is the class label, \(\boldsymbol{W}\) is a \(C \times D\) weight matrix, \(\boldsymbol{b}\) is \(C\)-dimensional bias vector, and \(\text{softmax}()\) is the **softmax function**, defined as

\(\text{softmax}(\boldsymbol{a}) \triangleq \left[ \frac{e^{a_1}}{\sum_{c'=1}^C e^{a_{c'}}}, \dots, \frac{e^{a_C}}{\sum_{c'=1}^C e^{a_{c'}}} \right]\) (15.136)

If we define the logits as \(\boldsymbol{\eta}_n = \boldsymbol{W}\boldsymbol{x}_n + \boldsymbol{b}\), the probabilities as \(\boldsymbol{\mu}_n = \text{softmax}(\boldsymbol{\eta}_n)\), and let \(\boldsymbol{y}_n\) be the one-hot encoding of the label \(y_n\), then the log likelihood can be written as the negative cross entropy:

\(\log p(\mathcal{D}|\boldsymbol{\theta}) = \log \prod_{n=1}^N \prod_{c=1}^C \mu_{nc}^{y_{nc}} = \sum_{n=1}^N \sum_{c=1}^C y_{nc} \log \mu_{nc}\) (15.137)

### 15.3.3 Dealing with class imbalance and the long tail

In many problems, some classes are much rarer than others; this problem is called **class imbalance**. In such a setting, standard maximum likelihood training may not work well, since it is designed to minimize (a bound on) the 0-1 loss, which can be dominated by the most frequent classes. A natural alternative is to consider the **balanced error rate**, which computes the average of the per-class error rates of classifier $f$:

$$\text{BER}(f) = \frac{1}{C} \sum_{y=1}^C p^*_{x|y} \left( y \notin \underset{y' \in \mathcal{Y}}{\text{argmax}} f_{y'}(x) \right)$$

where $p^*$ is the true distribution. The classifier that optimizes this loss, $f^*$, must satisfy

$$\underset{y \in \mathcal{Y}}{\text{argmax}} f^*_y(x) = \underset{y \in \mathcal{Y}}{\text{argmax}} p^*_\text{bal}(y|x) = \underset{y \in \mathcal{Y}}{\text{argmax}} p^*(x|y)$$

where $p^*_\text{bal}(y|x) \propto \frac{1}{C} p^*(x|y)$ is the predictor when using balanced classes. Thus to minimize the BER, we should use the class-conditional likelihood, $p(x|y)$, rather than the class posterior, $p(y|x)$.

In [Men+21], they propose a simple scheme called **logit adjustment** that can achieve this optimal classifier. We assume the model computes logits using $f_y(x) = w^\text{T}_y \phi(x)$, where $\phi(x) = x$ for a GLM. In the post-hoc version, the model is trained in the usual way, and then at prediction time, we use

$$\underset{y \in \mathcal{Y}}{\text{argmax}} p(x|y) = \underset{y \in \mathcal{Y}}{\text{argmax}} \frac{p(y|x)p(x)}{p(y)} = \underset{y \in \mathcal{Y}}{\text{argmax}} \frac{\exp(w^\text{T}_y \phi(x))}{\pi_y}$$

where $\pi_y = p(y)$ is the empirical label prior. In practice, it is helpful to introduce a tuning parameter $\tau > 0$ and to use the predictor

$$\hat{f}(x) = \underset{y \in \mathcal{Y}}{\text{argmax}} f_y(x) - \tau \log \pi_y$$

Alternatively, we can change the loss function used during training, by using the following **logit adjusted softmax cross-entropy loss**:

$$\ell(y, f(x)) = - \log \frac{e^{f_y(x) + \tau \log \pi_y}}{\sum_{y'=1}^C e^{f_{y'}(x) + \tau \log \pi_{y'}}}$$

This is like training with a predictor of the form $g_y(x) = f_y(x) + \tau \log \pi_y$, and then at test time using $\underset{y}{\text{argmax}} f_y(x) = \underset{y}{\text{argmax}} g_y(x) - \tau \log \pi_y$, as above.

We can also combine the above loss with a prior on the parameters and perform Bayesian inference, as we discuss below. (The use of a non-standard likelihood can be justified using the generalized Bayesian inference framework, as discussed in Section 14.1.3.)

### 15.3.4 Parameter priors

As with linear regression, it is standard to use Gaussian priors for the weights in a logistic regression model. It is natural to set the prior mean to 0, to reflect the fact that the output could either
