# 8 Nonlinear input transformations and kernels

By comparing (8.14b) and (8.5), we have that

```
$$\widetilde{Y}(x_*) = \bar{	heta}^T \phi(x_*) = \bar{\alpha}^T \frac{\Phi(X)\phi(x_*)}{K(X,x_*)} \quad (8.15)$
```

for all $x_*$, which suggests that

```
$$\bar{	heta} = \Phi(X)^T \bar{\alpha}. \quad (8.16)$
```

This relationship between the primal parameters $\theta$ and the dual parameters $\alpha$ is not specific for kernel regression, (8.16) is the consequence of a general result called the representer theorem.
In essence the representer theorem tells us that if $\widetilde{Y}(x) = \theta^T \phi(x)$, the equation (8.16) holds when $\theta$ is learned using (any) loss function and $L^2$-regularization. A full treatment is beyond the scope of this chapter, but we give a complete statement of the theorem in Section 8A. An implication of the representer theorem is that $L^2$-regularization is crucial in order to obtain kernel ridge regression (8.14). The representer theorem is a cornerstone for most kernel methods, since it tells us that we can express some models in terms of dual parameters $\alpha$ (of finite length $n$) and a kernel $\kappa(x,x')$ instead of the primal parameters $\theta$ (possibly of infinite length $d$) and a nonlinear feature transformation $\phi(x)$, just like we do in linear regression (8.14).

# Support vector regression

From a model perspective the support vector regression is another of the off-the-shelf kernel method for regression. This new loss function has an interesting effect in that the dual vector $\bar{\alpha}$ in support vector regression becomes \sparse\, meaning that several elements of $\bar{\alpha}$ are exactly zero. Recall that with one data point, the data points connecting the non-zero elements of $\bar{\alpha}$ are referred to as support vectors, and the prediction $\widetilde{Y}(x_*)$ will depend only on these (in contrast to kernel ridge regression (8.14b), where all training data are needed to compute $\widetilde{Y}(x_*)$). This support vector regression example of a so-called support vector machine (SVM), a family of methods with sparse dual vector parameters.

The loss we use for support vector regression is the $\epsilon$-insensitive loss

```
$L(Y, \widetilde{Y}) = \begin{cases} 0 & \text{if } |y - \widetilde{y}| < \epsilon, \ |y - \widetilde{y}| - \epsilon & \text{otherwise},\ \end{cases} \quad (8.17)$
```

or equivalently $L(Y, \widetilde{Y}) = \max\{0, |y - \widetilde{y}| - \epsilon\}$, which was introduced in (5.9) in Chapter 5. The parameter $\epsilon$ is a user design choice. In its primal formulation, support vector regression also makes use of linear regression model

```
$$\widetilde{Y}(x_*) = \bar{	heta}^T \phi(x_*). \quad (8.18a)$
```

but instead of the least square function in (8.4), we now have

```
$$\bar{	heta} = \arg\min_{\theta} \sum_{i=1}^n \max\{0, |y_i - \theta^T \phi(x_i)| - \epsilon\} + \lambda|\theta||_2^2. \quad (8.18b)$
```

With kernel ridge regression, we reformulate the primal formulation (8.18) into a dual formulation with $\alpha$ as instead of $\theta$ and the kernel-trick. For the dual formulation, we cannot repeat the closed-form derivation along of (8.4–8.14) since there is no closed-form solution for $\theta$. Instead we use optimization theory, introduce slack variables and construct the Lagrangian of (8.18b).