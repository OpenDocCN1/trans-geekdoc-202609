
![](img/c73db5a1f734ebb7c0655f19e5bc9daa_52_0.png)

![](img/c73db5a1f734ebb7c0655f19e5bc9daa_52_1.png)

Figure 6.2: Illustration of the benefits of using a lower-bounded loss function when training a resnet-128 CNN on the CIFAR10 image classification dataset. The curves are as follows: SGM (stochastic gradient method, i.e., SGD), Adam, truncated SGD and truncated AdaGrad. (a) Time to reach an error that satisfies \(\mathcal{L}(\boldsymbol{\theta}_t) - \mathcal{L}(\boldsymbol{\theta}^*) \le \epsilon\) vs initial learning rate \(\eta_0\). (b) Top-1 accuracy after 50 epochs vs \(\eta_0\). The lines represent median performance across 50 random restarts, and the shading represents 90% confidence intervals. From Figure 4 of [AD19c]. Used with kind permission of Hilal Asi.

### 6.1.3.3 Beyond linear approximations (truncated AdaGrad)

Sometimes we can do better than just using PPM with a linear approximation to the objective, at essentially no extra cost, as pointed out in [AD19b; AD19a; AD19c]. For example, suppose we know a lower bound on the loss, \(\ell_t^{\min} = \min_{\boldsymbol{\theta}} \ell_t(\boldsymbol{\theta})\). For example, when using squared error, or cross-entropy loss for discrete labels, we have \(\ell_t(\boldsymbol{\theta}) \ge 0\). Let us therefore define the **truncated model**

\[
\hat{\ell}_t(\boldsymbol{\theta}) = \max \left(\ell_t(\boldsymbol{\theta}) + \boldsymbol{g}_t^\top (\boldsymbol{\theta} - \boldsymbol{\theta}_t), \ell_t^{\min}\right) \tag{6.39}
\]

We can further improve things by replacing the Euclidean norm with a scaled Euclidean norm, where the diagonal scaling matrix is given by \(\mathbf{A}_t = \text{diag}(\sum_{i=1}^t \boldsymbol{g}_i \boldsymbol{g}_i^\top)^{\frac{1}{2}}\), as in AdaGrad [DHS11]. If \(\ell_t^{\min} = 0\), the resulting proximal update becomes

\[
\boldsymbol{\theta}_{t+1} = \underset{\boldsymbol{\theta}}{\text{argmin}} \left[ \ell_t(\boldsymbol{\theta}_t) + \boldsymbol{g}_t^\top (\boldsymbol{\theta} - \boldsymbol{\theta}_t) \right]_+ + \frac{1}{2\eta_t} (\boldsymbol{\theta} - \boldsymbol{\theta}_t)^\top \mathbf{A}_t (\boldsymbol{\theta} - \boldsymbol{\theta}_t) \tag{6.40}
\]

\[
= \boldsymbol{\theta}_t - \min\left(\eta_t, \frac{\ell_t(\boldsymbol{\theta}_t)}{\boldsymbol{g}_t^\top \mathbf{A}_t^{-1} \boldsymbol{g}_t}\right) \boldsymbol{g}_t \tag{6.41}
\]

Thus the update is like a standard SGD update, but we truncate the learning rate if it is too big.$^1$

[AD19c] call this **truncated AdaGrad**. Furthermore, they prove optimizing this truncated linear approximation (with or without AdaGrad weighting), instead of the standard linear approximation used by gradient descent, can result in significant benefits. In particular, it is guaranteed to be stable (under certain technical conditions) for any learning rate, whereas standard GD can “blow up”, even for convex problems.

Figure 6.2 shows the benefits of this approach when training a resnet-128 CNN (**??**) on the CIFAR10 image classification dataset. For SGD and the truncated proximal method, the learning rate is decayed using \(\eta_t = \eta_0 t^{-\beta}\) with \(\beta = 0.6\). For Adam and truncated AdaGrad, the learning rate is set to \(\eta_t = \eta_0\), since we use diagonal scaling. We see that both truncated methods (regular and AdaGrad version) have good performance for a much broader range of initial learning rate \(\eta_0\) compared to SGD or Adam.

$^1$One way to derive this update (suggested by Hilal Asi) is to do case analysis the value of \(\hat{\ell}_t(\boldsymbol{\theta}_{t+1})\), where \(\hat{\ell}_t\) is the truncated linear model. If \(\hat{\ell}_t(\boldsymbol{\theta}_{t+1}) > 0\), then setting the gradient to zero yields the usual SGD update, \(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \eta_t \boldsymbol{g}_t\). (We assume \(\mathbf{A}_t = \mathbf{I}\) for simplicity.) Otherwise we must have \(\hat{\ell}_t(\boldsymbol{\theta}_{t+1}) = 0\). But we know that \(\boldsymbol{\theta}_{t+1} = \boldsymbol{\theta}_t - \lambda \boldsymbol{g}_t\) for some \(\lambda\), so we solve \(\hat{\ell}_t(\boldsymbol{\theta}_t - \lambda \boldsymbol{g}_t) = 0\) to get \(\lambda = \hat{\ell}_t(\boldsymbol{\theta}_t) / \|\boldsymbol{g}_t\|_2^2\).

### 6.1.4 Mirror descent

We can extend the proximal point update in Equation (6.34) by replacing the Euclidean distance term \(\|\boldsymbol{\theta} - \boldsymbol{\theta}_t\|_2^2\) by a more general Bregman divergence (**??**),

\[
D_h(x, y) = h(x) - [h(y) + \nabla h(y)^\top (x - y)] \tag{6.42}
\]

where \(h(x)\) is a strongly convex function. This gives the following update:

\[
\theta_{t+1} = \text{argmin}_\theta \mathcal{L}(\theta) + \frac{1}{\eta_t} D_h(\theta, \theta_t) \tag{6.43}
\]

Suppose we make a linear approximation to \(\mathcal{L}(\theta)\).

\[
\hat{\mathcal{L}}_t(\theta) = \mathcal{L}(\theta_t) + \boldsymbol{g}_t^\top (\theta - \theta_t) \tag{6.44}
\]

where \(\boldsymbol{g}_t = \nabla_\theta \mathcal{L}(\theta_t)\). If we perform a proximal update with this linear approximation using Euclidean distance, we get a standard gradient update, as we showed in Section 6.1.3.2. However, combining this with the Bregman divergence gives the following update:

\[
\theta_{t+1} = \text{argmin}_\theta \eta_t \boldsymbol{g}_t^\top \theta + D_h(\theta, \theta_t) \tag{6.45}
\]

This is known as **mirror descent** [NY83; BT03]. This can easily be extended to the stochastic setting in the obvious way.

One can show that natural gradient descent (**??**) is a form of mirror descent [RM15]. More precisely, mirror descent in the mean parameter space is equivalent to natural gradient descent in the canonical parameter space.

### 6.1.5 Proximal gradient method

We are often interested in optimizing a composite objective of the form

\[
\mathcal{L}(\theta) = \mathcal{L}_s(\theta) + \mathcal{L}_r(\theta) \tag{6.46}
\]

where \(\mathcal{L}_s\) is convex and differentiable (smooth), and \(\mathcal{L}_r\) is convex but not necessarily differentiable (i.e., it may be non-smooth or “rough”). For example, \(\mathcal{L}_r\) might be an \(\ell_1\) norm regularization term, and \(\mathcal{L}_s\) might be the NLL for linear regression (see Section 6.1.5.1).

The **proximal gradient method** is the following update:

\[
\theta_{t+1} = \text{prox}_{\eta_t \mathcal{L}_r}(\theta_t - \eta_t \nabla \mathcal{L}_s(\theta_t)) \tag{6.47}
\]

If \(\mathcal{L}_r = I_C\), this is equivalent to **projected gradient descent**. If \(\mathcal{L}_r = 0\), this is equivalent to gradient descent. If \(\mathcal{L}_s = 0\), this is equivalent to a proximal point method.

We can create a version of the proximal gradient method with **Nesterov acceleration** as follows:

\[
\tilde{\theta}_{t+1} = \theta_t + \beta_t(\theta_t - \theta_{t-1}) \tag{6.48}
\]

\[
\theta_{t+1} = \text{prox}_{\eta_t \mathcal{L}_r}(\tilde{\theta}_{t+1} - \eta_t \nabla \mathcal{L}_s(\tilde{\theta}_{t+1})) \tag{6.49}
\]

See e.g., [Tse08].

Now we consider the stochastic case, where \(\mathcal{L}_s(\theta) = \mathbb{E}[\mathcal{L}_s(\theta, z)]\). (We assume \(\mathcal{L}_r\) is deterministic.) In this setting, we can use the following stochastic update:

\[
\theta_{t+1} = \text{prox}_{\eta_t \mathcal{L}_r}(\theta_t - \eta_t \nabla \mathcal{L}_s(\theta_t, z_t)) \tag{6.50}
\]

where \(z_t \sim q\). This is called the **stochastic proximal gradient method**. If \(q\) is the empirical distribution, this is called the **incremental proximal gradient method** [Ber15]. Both methods can also be accelerated (see e.g., [Nit14]).

If \(\mathcal{L}_s\) is not convex, we can compute a locally convex approximation, as in Section 6.1.3.3. (We assume \(\mathcal{L}_r\) remains convex.) The accelerated version of this is studied in [LL15]. In the stochastic case, we can similarly make a locally convex approximation to \(\mathcal{L}_s(\theta, z)\). This is studied in [Red+16; LL18]. An EKF interpretation in the incremental case (where \(q = p_D\)) is given in [Aky+19].

### 6.1.5.1 Example: Iterative soft-thresholding algorithm (ISTA) for sparse linear regression

Suppose we are interested in fitting a linear regression model with a sparsity-promoting prior on the weights, as in the lasso model (**??**). One way to implement this is to add the \(\ell_1\)-norm of the parameters as a (non-smooth) penalty term, \(\mathcal{L}_r(\theta) = \|\theta\|_1 = \sum_{d=1}^D |\theta_d|\). Thus the objective is

\[
\mathcal{L}(\theta) = \mathcal{L}_s(\theta) + \mathcal{L}_r(\theta) = \frac{1}{2}\|\mathbf{X}\theta - \mathbf{y}\|_2^2 + \lambda\|\theta\|_1
\]

The proximal gradient descent update can be written as

\[
\theta_{t+1} = \text{SoftThreshold}_{\eta_t\lambda}(\theta_t - \eta_t \nabla\mathcal{L}_s(\theta_t))
\]

where the soft thresholding operator (Equation (6.26)) is applied elementwise, and \(\nabla\mathcal{L}_s(\theta) = \mathbf{X}^\top(\mathbf{X}\theta - \mathbf{y})\). This is called the **iterative soft thresholding algorithm** or **ISTA** [DDM04; Don95]. If we combine this with Nesterov acceleration, we get the method known as “fast ISTA” or **FISTA** [BT09], which is widely used to fit sparse linear models.

### 6.1.6 Alternating direction method of multipliers (ADMM)

Consider the problem of optimizing \(\mathcal{L}(x) = \mathcal{L}_s(x) + \mathcal{L}_r(x)\) where now both \(\mathcal{L}_s\) and \(\mathcal{L}_r\) may be non-smooth (but we assume both are convex). We may want to optimize these problems independently (e.g., so we can do it in parallel), but need to ensure the solutions are consistent.

One way to do this is by using the **variable splitting trick** combined with constrained optimization:

minimize \(\mathcal{L}_s(x) + \mathcal{L}_r(z)\) s.t. \(x - z = \mathbf{0}\)

This is called **consensus form**.

The corresponding augmented Lagrangian is given by

\[
L_\rho(x, z, y) = \mathcal{L}_s(x) + \mathcal{L}_r(z) + y^\top(x - z) + \frac{\rho}{2}\|x - z\|_2^2
\]

where \(\rho > 0\) is the penalty strength, and \(y \in \mathbb{R}^n\) are the dual variables associated with the consistency constraint. We can now perform the following block coordinate descent updates:

\[
x_{t+1} = \underset{x}{\text{argmin}} L_\rho(x, z_t, y_t)
\]

\[
z_{t+1} = \underset{z}{\text{argmin}} L_\rho(x_{t+1}, z, y_t)
\]

\[
y_{t+1} = y_t + \rho(x_{t+1} - z_{t+1})
\]

We see that the dual variable is the (scaled) running average of the consensus errors.

Inserting the definition of \(L_\rho(x, z, y)\) gives us the following more explicit update equations:

\[
x_{t+1} = \underset{x}{\text{argmin}} \left( \mathcal{L}_s(x) + y_t^\top x + \frac{\rho}{2}\|x - z_t\|_2^2 \right)
\]

\[
z_{t+1} = \underset{z}{\text{argmin}} \left( \mathcal{L}_r(z) - y_t^\top z + \frac{\rho}{2}\|x_{t+1} - z\|_2^2 \right)
\]

If we combine the linear and quadratic terms, we get

\[
x_{t+1} = \underset{x}{\text{argmin}} \left( \mathcal{L}_s(x) + \frac{\rho}{2}\|x - z_t + (1/\rho)y_t\|_2^2 \right)
\]

\[
z_{t+1} = \underset{z}{\text{argmin}} \left( \mathcal{L}_r(z) + \frac{\rho}{2}\|x_{t+1} - z - (1/\rho)y_t\|_2^2 \right)
