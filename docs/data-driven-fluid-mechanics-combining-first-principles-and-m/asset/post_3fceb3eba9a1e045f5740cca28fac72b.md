
recover its unitary norm (energy). We return to this property in Chapter 8. Before moving to continuous signals, it is worth introducing another important signal that is linked to delta functions, namely the Heaviside step function. This is defined as

$$u_S[k - l] = \begin{cases} 1 & \text{if } k \ge l \\ 0 & \text{if } k < l \end{cases} \quad \text{that is } \longrightarrow u_S[k - l] = \sum_{r=-\infty}^{k} \delta[r - l]. \tag{4.7}$$

The difference between two shifted step functions generates a box function $u_{Ba,p}$, which is unitary in the range $k = [a, b-1]$ and is zero outside. The difference between two step functions shifted by a single step is a delta function, that is, $\delta[k - l] = u_S[k - l] - u_S[k - l - 1]$. In the discrete setting, this is equivalent to a differentiation. Hence, *the delta function is the derivative of the step function* and the summation in (4.7) shows that *the step function is an integral of the delta functions*. The reader should close this subsection with an exercise on some distinctive features of discrete signals.

### Exercise 1: Continuous versus Discrete

Consider the continuous signal $y(t) = e^{-0.2t} \cos(2\pi t)$ where $t$ is in seconds. Assuming that the signal is sampled at $f = 100\text{Hz}$, and that $n_t = 320$ points are collected from $t = 0$, what is the resulting discrete signal? Plot this signal and comment on its link with the continuous one.

## 4.3.2 Continuous Signals

The extension of the previously introduced notion to continuous signals brings several complications, a detailed resolution of which is out of the scope of this chapter. Interested readers are referred to Kaiser (2010) for a gentle introduction. The main difficulty arises from the need to define an inner product space which can generalize (4.3) for functions while allowing for a basis of impulses, that is, functions that are zero at all but one point. This generalization is provided by the Hilbert space within which the inner product of two complex-valued functions $a(t), b(t) \in \mathbb{C}$ is

$$\langle a, b \rangle = \int_{-\infty}^{\infty} a(t) \overline{b(t)}\; dt. \tag{4.8}$$

The notion of energy (norm), correlation, and projection in (4.5)–(4.6) extends to continuous signals using the inner product⁸ in (4.8). The generalization of (4.4) requires the definition of a continuous delta function $\delta(t)$ with the same properties as $\delta[k]$: it is nonzero only at a given time and it is absolutely integrable. This can be constructed as the limit of a suitably chosen function having unit area over an infinitesimal time interval. An example is a normalized Gaussian $G(t, \mu, \sigma)$, which has unit integral regardless of its standard deviation $\sigma$:

$$\int_{-\infty}^{\infty} G(t, \mu = 0, \sigma)\, dt = \frac{1}{\sqrt{2\pi\sigma^2}} \int_{-\infty}^{\infty} e^{\frac{-t^2}{2\sigma^2}} dt = 1. \tag{4.9}$$

⁸ Note that the upper case is used for the norms of a continuous function, that is, $||a(t)||_2 = \sqrt{\langle a, a \rangle}$, with the inner product in (4.8), is the $L^2$ norm of the function $a(t)$.

This function gets narrower and taller, as σ → 0, to the point at which it becomes infinite at t = 0 and null everywhere else while still having unit area. This is the definition of a continuous Dirac delta function, which in its shifted form is

$$\delta(t - \tau) = \begin{cases} 0 & \text{if } t \neq \tau, \\ \infty & \text{if } t = \tau \end{cases} \quad \text{and} \quad \int_{-\infty}^{+\infty} \delta(t - \tau) dt = 1. \tag{4.10}$$

This function is not an ordinary one, as its integration poses several technical difficulties. Without entering into details of measure and distribution theory (Richards & Youn 1990), we shall accept this as a generalized function that serves well our purpose of sampling a continuous signal. From the definition in (4.10), it is easy to derive the sifting (sampling property):

$$y(t) = \langle y(\tau),\delta(t - \tau)\rangle = \int_{-\infty}^{\infty} y(\tau)\delta(t - \tau)d\tau = \int_{-\infty}^{\infty} y(t)\delta(t - \tau)d\tau$$
$$= y(t) \int_{-\infty}^{\infty} \delta(t - \tau)d\tau = y(t). \tag{4.11}$$

The equivalence y(τ) = y(t) in the integral results from the product y(τ)δ(t − τ) being null everywhere but at t; then, in the last step it is possible to move y(t) outside the integral as this is independent from the integration domain τ.

As for the discrete case, it is interesting to introduce the unitary step function and its link with the delta function as

$$u_S(t - t_0) = \begin{cases} 1 & \text{if } t > t_0, \\ 0 & \text{if } t < t_0 \end{cases} \quad \text{that is,} \longrightarrow u_S(t - t_0) = \int_{-\infty}^{t} \delta(\tau - t_0)d\tau. \tag{4.12}$$

Notice that the step function is not defined at t = t0. This definition is the continuous analogue of (4.7). To show that the delta function is the derivative of the step function, we must introduce the notion of generalized derivative. For a continuous signal u(t), denoting as u′ and u(n) its first and nth derivative, integration by part using an appropriate test function ξ(t) gives

$$\int_{-\infty}^{\infty} \xi(t) u^{(n)}(t) dt = (-1)^n \int_{-\infty}^{\infty} \xi^{(n)} u(t) dt, \tag{4.13}$$

$$\int_{-\infty}^{\infty} \xi(t) u'_S(t - t_0) dt = - \int_{-\infty}^{\infty} \xi'(t) u_S(t - t_0) dt = - \int_{t_0}^{\infty} \xi'(t) dt$$
$$= \xi(t_0) - \xi(\infty) = \xi(t_0) = \int_{-\infty}^{\infty} \xi(t) \delta(t - t_0) dt. \tag{4.14}$$

The first equality results from direct application of (4.13); the second from uS(t−t0) being zero in t < t0. After integration, the sifting property of the delta function (4.11) is used, and the result is obtained by equivalence of last step with the first, holding on the fact that ξ(t) is arbitrary.

## 4.4 Convolutions and Eigenfunctions

In a *linear system*, the input–output relation satisfies *homogeneity* and *superposition* conditions. For continuous ($\mathcal{S}_c\{u(t)\}=y(t)$) and discrete ($\mathcal{S}_d\{u[k]\}=y[k]$) systems, these are:

*Homogeneity:*

$$\mathcal{S}_c\{a u(t)\}=a\mathcal{S}_c\{u(t)\}=a y(t)\quad\text{for all }a\in\mathbb{C},$$
$$\mathcal{S}_d\{a u[k]\}=a\mathcal{S}_d\{u[k]\}=a y[k]\quad\text{for all }a\in\mathbb{C}.\tag{4.15}$$

*Superposition:*

$$\mathcal{S}_c\left\{\int_{-\infty}^{\infty}u(t)\right\}dt=\int_{-\infty}^{\infty}\mathcal{S}_c\{u(t)\}dt=\int_{-\infty}^{\infty}y(t)dt,$$
$$\mathcal{S}_d\left\{\sum_{n=1}^{N}u_n[k]\right\}=\sum_{n=1}^{N}\mathcal{S}_d\{u_n[k]\}=\sum_{n=1}^{N}y_n[k],\tag{4.16}$$

where we considered a finite summation of $N$ inputs for the discrete case and an infinite summation of infinitesimally close inputs for the continuous one. Combining these properties, we see that a linear combination of inputs results in the same linear combination of outputs:

$$\mathcal{S}_c\left\{\int_{-\infty}^{\infty}a(\tau)u(t,\tau)\right\}d\tau=\int_{-\infty}^{\infty}a(\tau)\mathcal{S}_c\{u(t,\tau)\}d\tau=\int_{-\infty}^{\infty}a(\tau)y(t,\tau)d\tau,$$
$$\mathcal{S}_d\left\{\sum_{n=1}^{N}a_n u_n[k]\right\}=\sum_{n=1}^{N}a_n \mathcal{S}_d\{u_n[k]\}=\sum_{n=1}^{N}a_n y_n[k].\tag{4.17}$$

A system is *time-invariant* (or *translation-invariant*, if time is replaced by space) if the response to the input does not change over time (or space), that is,

if $\mathcal{S}_c\{u(t)\}=y(t)$ then $\mathcal{S}_c\{u(t-t_0)\}=y(t-t_0)$ for all $t_0\in\mathbb{R}$,
if $\mathcal{S}_d\{u[k]\}=y[k]$ then $\mathcal{S}_d\{u[k-k_0]\}=y[k-k_0]$ for all $k_0\in\mathbb{Z}.\tag{4.18}$

A system is linear time/translation invariant (LTI) if it is both linear *and* time/translation invariant. These two properties, combined with the signal representations in (4.10)–(4.11), make the analysis of LTI systems particularly simple: the response to *any* input can be fully characterized from the response to a *single impulse*.

Defining as $h(t)=\mathcal{S}_c\{\delta(t)\}$ the impulse response of a continuous system, the response to any input is
