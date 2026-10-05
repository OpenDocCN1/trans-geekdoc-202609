
## D.2 GAUSSIAN RANDOM FIELD MODEL

Given the forward process, $q(X(k)_t)$ is Gaussian and the score function can be computed explicitly:

$$\nabla_{X(k)} \log q(X(k)_t) = -\frac{X(k)_t}{\tilde{a}_t^2 + 1 - \tilde{a}_t} \quad (372)$$

### D.2.2 Mode retrieval

Our goal is to determine which Fourier coefficients are retrieved after the reverse process. Specifically, we want to compute the $k$ for the distance between the coefficient obtained at the end of the backward process $X(k,t)_0 \sim p(\mathbf{X}(k)_t)$ with the starting coefficient $X(k)_0$ is small:

$$|\mathbf{X}(k,t)_0 - X(k)_0| \le 1. \quad (373)$$

Thus, we consider the signal-to-noise ratio (SNR) for each mode $k$

$$SNR(\kappa, t) = \frac{\kappa^*}{\tilde{a}_t - 1}. \quad (374)$$

where $k = ||\kappa||$. Define the critical wavevector magnitude $\kappa^*$ where $SNR(\kappa^*, t) = 1$:

$$\kappa^* = (\tilde{a}_t^{-1} - 1)^{-1/a} \quad (375)$$

Modes with $\kappa < \kappa^*$ (low-frequency modes) have SNR $> 1$ and can be retrieved, while modes with $\kappa > \kappa^*$ (high-frequency modes) have SNR $> 1$ are dominated by the noise in the forward dynamics and cannot be reconstructed.

### D.2.3 Correlation analysis

We seek to compute the correlation of the changes after reverting the process at time $t$. $x(u,t)$ denote the field obtained after reverting the diffusion process at time $t$, at position $u$. In particular, $x(\cdot,0)$ denote the starting random field. Define the difference field $z(u,t) = x(u,t)-x(u,0)$. Both the fields are Gaussian, also $z(\cdot,t)$ is Gaussian.

We are interested in the following spatial correlation function:

$$C(r, t) = \mathbb{E}[z(u,t)^2z(0,t)^2], \quad (376)$$

where $r = ||u||$. Using Wick's theorem, we have

$$C(r, t) = \mathbb{E}[z(u,t)z(u,t)] \mathbb{E}[z(0,t)z(0,t)] + 2\mathbb{E}[z(u,t)z(0,t)]^2. \quad (377)$$

The first term is a constant independent of $r$, while the second term captures the spatial dependence.

## APPENDIX: PROBING HIDDEN HIERARCHIES IN DATA

![](img/86150bd6d44cb578b97e3eba954b7be2_245_0.png)

Figure 54: Gaussian random field model. (a) Relative modal errors as a function of wave-vector magnitude $|k|$. For $|k| > \kappa^*$, errors remain large, indicating unsuccessful retrieval of the Fourier coefficients, for $|k| < \kappa^*$, the error decreases, signifying significant recovery (b). Spatial correlation function $C(r,t)$, showing a power decay at short distances and a cutoff at long distances. The correlation length increases with inversion time $t$. (c) The susceptibility $\chi(t)$ increases monotonically and reaches its maximum at the inversion time $t = T$.

To compute $\mathbb{E}[z(u,t)z(0,t)]$, in terms of Fourier coefficients $Z(\mathbf{k},t)$, with $\kappa < \kappa^*$, we can assume $Z(\mathbf{k},t) \approx 0$. For with $\kappa > \kappa^*$, $\hat{X}(\mathbf{k},t)_0$ is approximately independent of $X(0)$. Thus, $Z(\mathbf{k},t)$ for $\kappa > \kappa^*$ is a Gaussian random variable with zero mean and variance $2\sigma_z^2$.

The variance of $z$ is

>$$\mathbb{E}[z(u,t)z(0,t)] \approx \int_{|k|>\kappa^*} k^{uk} 2\sigma_z^2 d^d k.\quad (378)$$

Substituting $\sigma_z^2 \approx \|k\|^{-a}$, we have:

>$$\mathbb{E}[z(u,t)z(0,t)] \approx \int_{|k|>\kappa^*} k^{uk} 2\|k\|^{-a} d^d k.\quad (379)$$

To evaluate the integral, we consider the asymptotic behavior for different regimes of $r$. At short distances $r \ll 1/\kappa^*$, the integral over $k$ is dominated by large $\kappa$ and behaves as $\mathbb{E}[z(u,t)z(0,t)] \approx C_1 r^{a-d}$, where $C_1$ is a constant. At long distances $r \gg 1/\kappa^*$, the lower limit $\kappa^*$ introduces an effective cutoff and the covariances decay faster than any power law.

Therefore, the correlation function $\dot{C}(r,t)$ exhibits algebraic decay with exponent $2(a-d)$ for $r \ll 1/\kappa^*$ and faster than any power law for $r \gg 1/\kappa^*$.

### D.2.4 Discussion

For the Gaussian random field model, the correlation length $\xi \sim 1/\kappa^*(t)$ is a monotonically increasing function of the inversion time $t_i$, or noise-to-signal ratio (NSR). As a result, the susceptibility $\chi(t)$ - calculated by integrating the correlation function over space - also increases monotonically reaches its maximum at the inversion time $t=T$, where the NSR = $\infty$. This behavior contrasts sharply with the hierarchical data studied here, where a phase transition occurs at a finite time/NSR. As discussed in the main text, this divergence arises due to the geometry of correlations induced by the hierarchical tree structure, which is absent in the Gaussian random field model.

### D.2.5 Numerical experiments

In Figure 5 (a), we plot the local model errors $\mathcal{E}_k = \varepsilon_k ||\hat{X}(k,t)_0||$.

(Note: The provided text for D.2.5 seems to end abruptly or be merged with subsequent sections in the OCR. I have processed the available content accordingly.)
