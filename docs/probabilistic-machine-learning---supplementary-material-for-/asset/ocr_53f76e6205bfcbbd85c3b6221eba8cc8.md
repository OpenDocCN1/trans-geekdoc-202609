# 6.1.4 Mirror descent

We can extend the proximal point update in Equation (6.34) by replacing the Euclidean distance term $||	heta - 	heta_t||_2^2$ by a more general Bregman divergence (**??**),

$$D_h(x, y) = h(x) - [h(y) + \nabla h(y)^T(x - y)] \quad (6.42)$$

where $h(x)$ is a strongly convex function. This gives the following update:

$$\theta_{t+1} = \text{argmin}_\theta \mathcal{L}(\theta) + \frac{1}{\eta_t} D_h(\theta, \theta_t) \quad (6.43)$$

Suppose we make a linear approximation to $\mathcal{L}(\theta)$.

$$\hat{\mathcal{L}}_t(\theta) = \mathcal{L}(\theta_t) + g_t^T(\theta - \theta_t) \quad (6.44)$$

where $g_t = \nabla_\theta \mathcal{L}(\theta_t)$. If we perform a proximal update with this linear approximation using Euclidean distance, we get a standard gradient update, as we showed in Section 6.1.3.2. However, combining this with the Bregman divergence gives the following update:

$$\theta_{t+1} = \text{argmin}_\theta \eta_t g_t^T \theta + D_h(\theta, \theta_t) \quad (6.45)$$

This is known as **mirror descent** [NY83; BT03]. This can easily be extended to the stochastic setting in the obvious way.

One can show that natural gradient descent (**??**) is a form of mirror descent [RM15]. More precisely, mirror descent in the mean parameter space is equivalent to natural gradient descent in the canonical parameter space.

# 6.1.5 Proximal gradient method

We are often interested in optimizing a composite objective of the form

$$\mathcal{L}(\theta) = \mathcal{L}_s(\theta) + \mathcal{L}_r(\theta) \quad (6.46)$$

where $\mathcal{L}_s$ is convex and differentiable (smooth), and $\mathcal{L}_r$ is convex but not necessarily differentiable (i.e., it may be non-smooth or “rough”). For example, $\mathcal{L}_r$ might be an $\ell_1$ norm regularization term, and $\mathcal{L}_s$ might be the NLL for linear regression (see Section 6.1.5.1).

The **proximal gradient method** is the following update:

$$\theta_{t+1} = \text{prox}_{\eta_t \mathcal{L}_r}(\theta_t - \eta_t \nabla \mathcal{L}_s(\theta_t)) \quad (6.47)$$

If $\mathcal{L}_r = I_C$, this is equivalent to **projected gradient descent**. If $\mathcal{L}_r = 0$, this is equivalent to gradient descent. If $\mathcal{L}_s = 0$, this is equivalent to a proximal point method.

We can create a version of the proximal gradient method with **Nesterov acceleration** as follows:

$$\tilde{\theta}_{t+1} = \theta_t + \beta_t(\theta_t - \theta_{t-1}) \quad (6.48)$$

$$\theta_{t+1} = \text{prox}_{\eta_t \mathcal{L}_r}(\tilde{\theta}_{t+1} - \eta_t \nabla \mathcal{L}_s(\tilde{\theta}_{t+1})) \quad (6.49)$$

See e.g., [Tse08].

Now we consider the stochastic case, where $\mathcal{L}_s(\theta) = \mathbb{E}[\mathcal{L}_s(\theta, z)]$. (We assume $\mathcal{L}_r$ is deterministic.) In this setting, we can use the following stochastic update:

$$\theta_{t+1} = \text{prox}_{\eta_t \mathcal{L}_r}(\theta_t - \eta_t \nabla \mathcal{L}_s(\theta_t, z_t)) \quad (6.50)$$

where $z_t \sim q$. This is called the **stochastic proximal gradient method**. If $q$ is the empirical distribution, this is called the **incremental proximal gradient method** [Ber15]. Both methods can also be accelerated (see e.g., [Nit14]).

If $\mathcal{L}_s$ is not convex, we can compute a locally convex approximation, as in Section 6.1.3.3. (We assume $\mathcal{L}_r$ remains convex.) The accelerated version of this is studied in [LL15]. In the stochastic case, we can similarly make a locally convex approximation to $\mathcal{L}_s(\theta, z)$. This is studied in [Red+16; LL18]. An EKF interpretation in the incremental case (where $q = p_D$) is given in [Aky+19].