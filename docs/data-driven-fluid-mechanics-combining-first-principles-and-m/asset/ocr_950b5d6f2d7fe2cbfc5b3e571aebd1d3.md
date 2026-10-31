# 4.4 Convolutions and Eigenfunctions

In a *linear system*, the input–output relation satisfies *homogeneity* and *superposition* conditions. For continuous ($\mathcal{S}_c\{u(t)\}=y(t)$) and discrete ($\mathcal{S}_d\{u[k]\}=y[k]$) systems, these are:

*Homogeneity:*

$$\mathcal{S}_c\{a u(t)\}=a\mathcal{S}_c\{u(t)\}=a y(t)\quad\text{for all }a\in\mathbb{C},$$
$$\mathcal{S}_d\{a u[k]\}=a\mathcal{S}_d\{u[k]\}=a y[k]\quad\text{for all }a\in\mathbb{C}.\tag{4.15}$$

*Superposition:*

$$\mathcal{S}_c\left\{\int_{-\infty}^{\infty}u(t)\right\}dt=\int_{-\infty}^{\infty}\mathcal{S}_d\{u(t)\}dt=\int_{-\infty}^{\infty}y(t)dt,$$
$$\mathcal{S}_d\left\{\sum_{n=1}^{N}u_n[k]\right\}=\sum_{n=1}^{N}\mathcal{S}_d\{u_n[k]\}=\sum_{n=1}^{N}y_n[k],\tag{4.16}$$

where we considered a finite summation of $N$ inputs for the discrete case and an infinite summation of infinitesimally close inputs for the continuous one. Combining these properties, we see that a linear combination of inputs results in the same linear combination of outputs:

$$\mathcal{S}_c\left\{\int_{-\infty}^{\infty}a(\tau)u(t,\tau)\right\}d\tau=\int_{-\infty}^{\infty}a(\tau)\mathcal{S}_d\{u(t,\tau)\}d\tau=\int_{-\infty}^{\infty}a(\tau)y(t,\tau)d\tau,$$
$$\mathcal{S}_d\left\{\sum_{n=1}^{N}a_n u_n[k]\right\}=\sum_{n=1}^{N}a_n\mathcal{S}_d\{u_n[k]\}=\sum_{n=1}^{N}a_n y_n[k].\tag{4.17}$$

A system is *time-invariant* (or *translation-invariant*, if time is replaced by space) if the response to the input does not change over time (or space), that is,

if $\mathcal{S}_c\{u(t)\}=y(t)$ then $\mathcal{S}_c\{u(t-t_0)\}=y(t-t_0)$ for all $t_0\in\mathbb{R}$.,
if $\mathcal{S}_d\{u[k]\}=y[k]$ then $\mathcal{S}_d\{u[k-k_0]\}=y[k-k_0]$ for all $k_0\in\mathbb{Z}.\tag{4.18}$

A system is linear time/translation invariant (LTI) if it is both linear *and* time/translation invariant. These two properties, combined with the signal representations in (4.10)–(4.11), make the analysis of LTI systems particularly simple: the response to *any* input can be fully characterized from the response to a *single impulse*.

Defining as $h(t)=\mathcal{S}_c\{\delta(t)\}$ the impulse response of a continuous system, the response to any input is