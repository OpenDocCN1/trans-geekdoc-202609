recover its unitary norm (energy). We return to this property in Chapter 8. Before moving to continuous signals, it is worth introducing another important signal that is linked to delta functions, namely the Heaviside step function. This is defined as

$$u_S[k - l] = \begin{cases} 1 & \text{if } k \ge l \\ 0 & \text{if } l < k \end{cases} \quad \text{that is } \longrightarrow u_S[k - l] = \sum_{r=-\infty}^{k} \delta[r - l]. \tag{4.7}$$

The difference between two shifted step functions generates a box function $u_{Ba,p}$, which is unitary in the range $k = [a, b-1]$ and is zero outside. The difference between two step functions shifted by a single step is a delta function, that is, $\delta[k - l] = u_S[k - l] - u_S[k - l - 1]$. In the discrete setting, this is equivalent to a differentiation. Hence, *the delta function is the derivative of the step function* and the summation in (4.7) shows that *the step function is an integral of the delta functions*. The reader should close this subsection with an exercise on some distinctive features of discrete signals.

# Exercise 1: Continuous versus Discrete

Consider the continuous signal $y(t) = e^{-0.2t} \cos(2\pi t)$ where $t$ is in seconds. Assuming that the signal is sampled at $f = 100\text{Hz}$, and that $n_t = 320$ points are collected from $t = 0$, what is the resulting discrete signal? Plot this signal and comment on its link with the continuous one.

# 4.3.2 Continuous Signals

The extension of the previously introduced notion to continuous signals brings several complications, a detailed resolution of which is out of the scope of this chapter. Interested readers are referred to Kaiser (2010) for a gentle introduction. The main difficulty arises from the need to define an inner product space which can generalize (4.3) for functions while allowing for a basis of impulses, that is, functions that are zero at all but one point. This generalization is provided by the Hilbert space within which the inner product of two complex-valued functions $a(t), b(t) \in \mathbb{C}$ is

$$\langle a, b \rangle = \int_{-\infty}^{\infty} a(t) \overline{b(t)}\; dt. \tag{4.8}$$

The notion of energy (norm), correlation, and projection in (4.5)–(4.6) extends to continuous signals using the inner product⁸ in (4.8). The generalization of (4.4) requires the definition of a continuous delta function $\delta(t)$ with the same properties as $\delta[k]$: it is nonzero only at a given time and it is absolutely integrable. This can be constructed as the limit of a suitably chosen function having unit area over an infinitesimal time interval. An example is a normalized Gaussian $G(t, \mu, \sigma)$, which has unit integral regardless of its standard deviation $\sigma$:

$$\int_{-\infty}^{\infty} G(t, \mu = 0, \sigma)\, dt = \frac{1}{\sqrt{2\pi\sigma^2}} \int_{-\infty}^{\infty} e^{\frac{-t^2}{2\sigma^2}} dt = 1. \tag{4.9}$$

⁸ Note that the upper case is used for the norms of a continuous function, that is, $||a(t)||_2 = \sqrt{\langle a, a \rangle}$, with the inner product in (4.8), is the $L^2$ norm of the function $a(t)$.