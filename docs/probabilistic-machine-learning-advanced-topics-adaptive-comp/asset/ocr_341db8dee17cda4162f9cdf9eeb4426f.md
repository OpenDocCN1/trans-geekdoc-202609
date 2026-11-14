$f(\boldsymbol{x}; \boldsymbol{\theta}) = \boldsymbol{\theta}^\mathsf{T} \boldsymbol{\phi}(\boldsymbol{x})$ for some fixed feature transformation $\phi)$, then the model is called a generalized linear model or GLM, which we discuss in Chapter 15. If $f$ is a non-linear, but differentiable, function of $\boldsymbol{\theta}$ (e.g., $f(\boldsymbol{x}; \boldsymbol{\theta}) = \boldsymbol{\theta}_2^\mathsf{T} \boldsymbol{\phi}(\boldsymbol{x}; \boldsymbol{\theta}_1)$ for some learnable function $\boldsymbol{\phi}(\boldsymbol{x}; \boldsymbol{\theta}_1)$), then it is common to represent $f$ using a neural network (Chapter 16). Other types of predictive model, such as decision trees and random forests, are discussed in the prequel to this book, [Mur22].

# 14.1.2 Model fitting using ERM, MLE, and MAP

In this section, we briefly discuss some methods used for fitting (parametric) models. The most common approach is to use **maximum likelihood estimation** or **MLE**, which amounts to solving the following optimization problem:

$\hat{\boldsymbol{\theta}} = \operatorname{argmax}_{\boldsymbol{\theta} \in \Theta} p(\mathcal{D}|\boldsymbol{\theta}) = \operatorname{argmax}_{\boldsymbol{\theta} \in \Theta} \log p(\mathcal{D}|\boldsymbol{\theta})$ (14.1)

If the dataset is $N$ iid data samples, the likelihood decomposes into a product of terms, $p(\mathcal{D}|\boldsymbol{\theta}) = \prod_{n=1}^N p(\boldsymbol{y}_n|\boldsymbol{x}_n, \boldsymbol{\theta})$. Thus we can instead minimize the following (scaled) **negative log likelihood**:

$\hat{\boldsymbol{\theta}} = \operatorname{argmin}_{\boldsymbol{\theta} \in \Theta} \frac{1}{N} \sum_{n=1}^N [-\log p(\boldsymbol{y}_n|\boldsymbol{x}_n, \boldsymbol{\theta})]$ (14.2)

We can generalize this by replacing the log loss $\ell_n(\boldsymbol{\theta}) = -\log p(\boldsymbol{y}_n|\boldsymbol{x}_n, \boldsymbol{\theta})$ with a more general loss function to get

$\hat{\boldsymbol{\theta}} = \operatorname{argmin}_{\boldsymbol{\theta} \in \Theta} r(\boldsymbol{\theta})$ (14.3)

where $r(\boldsymbol{\theta})$ is the **empirical risk**

$r(\boldsymbol{\theta}) = \frac{1}{N} \sum_{n=1}^N \ell_n(\boldsymbol{\theta})$ (14.4)

This approach is called **empirical risk minimization** or **ERM**.

ERM can easily result in **overfitting**, so it is common to add a penalty or regularizer term to get

$\hat{\boldsymbol{\theta}} = \operatorname{argmin}_{\boldsymbol{\theta} \in \Theta} r(\boldsymbol{\theta}) + \lambda C(\boldsymbol{\theta})$ (14.5)

where $\lambda \ge 0$ controls the degree of regularization, and $C(\boldsymbol{\theta})$ is some complexity measure. If we use log loss, and we define $C(\boldsymbol{\theta}) = -\log \pi_0(\boldsymbol{\theta})$, where $\pi_0(\boldsymbol{\theta})$ is some prior distribution, and we use $\lambda = 1$, we recover the **MAP estimate**

$\hat{\boldsymbol{\theta}} = \operatorname{argmax}_{\boldsymbol{\theta} \in \Theta} \log p(\mathcal{D}|\boldsymbol{\theta}) + \log \pi_0(\boldsymbol{\theta})$ (14.6)

This can be solved using standard optimization methods (see Chapter 6).