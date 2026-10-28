# 7.2 Slepian, Sudakov-Fernique and Gordon inequalities

In many applications, it helps to have a *uniform* bound on a random process:

$\mathbb{E}\sup_{t\in T} X_t = ?$

**Remark 7.2.1** (Making $T$ finite). To avoid measurability issues, let’s think of $\mathbb{E}\sup_{t\in T} X_t$ as shorthand for $\sup_{T_0\subset T}\mathbb{E}\max_{t\in T_0} X_t$ where $T_0$ runs over all finite subsets. The general case usually follows by approximation.

For some processes, this quantity can be computed exactly. For example, if $(X_t)$ is a standard Brownian motion, the so-called reflection principle gives

$\mathbb{E}\sup_{t\le t_0} X_t = \sqrt{\frac{2t_0}{\pi}}\quad\text{for every }t_0\ge 0.$

For general random processes—even Gaussian—the problem is nontrivial.

The first general bound we prove is the Slepian comparison inequality for Gaussian processes. It basically says: the faster the process grows (in terms of the increments), the farther it gets.

**Theorem 7.2.2** (Slepian inequality). Let $(X_t)_{t\in T}$ and $(Y_t)_{t\in T}$ be two mean-zero Gaussian processes. Assume that for all $t,s\in T$, we have

$\mathbb{E}X_t^2=\mathbb{E}Y_t^2\quad\text{and}\quad\mathbb{E}(X_t-X_s)^2\le\mathbb{E}(Y_t-Y_s)^2.$\tag{7.3}$

Then $\sup_{t\in T}X_t$ is stochastically dominated by $\sup_{t\in T}Y_t$: for every $\tau\in\mathbb{R}$, we have

$\mathbb{P}\left\{\sup_{t\in T}X_t\ge\tau\right\}\le\mathbb{P}\left\{\sup_{t\in T}Y_t\ge\tau\right\}.\tag{7.4}$

*Consequently,*

$\mathbb{E}\sup_{t\in T}X_t\le\mathbb{E}\sup_{t\in T}Y_t.\tag{7.5}$

We now prepare for the proof of Slepian inequality.

# 7.2.1 Gaussian interpolation

We will prove Slepian inequality using a trick called Gaussian interpolation. Assume that $T$ is finite; then we can look at $X=(X_t)_{t\in T}$ and $Y=(Y_t)_{t\in T}$ as Gaussian random vectors in $\mathbb{R}^n$ where $n=|T|$. We may also assume that $X$ and $Y$ are independent. (Why?)

Define the Gaussian random vector $Z(u)$ in $\mathbb{R}^n$ that continuously interpolates between $Z(0)=Y$ and $Z(1)=X$:

$Z(u):=\sqrt{u}\,X+\sqrt{1-u}\,Y,\quad u\in[0,1].$

Then the covariance matrix of $Z(u)$ continuously interpolates linearly between the covariance matrices of $Y$ and $X$:

$\Sigma(Z(u))=u\,\Sigma(X)+(1-u)\,\Sigma(Y).$