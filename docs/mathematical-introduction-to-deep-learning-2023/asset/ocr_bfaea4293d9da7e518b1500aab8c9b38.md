# 9.11. Convergence analysis for solutions of GF ODEs

assumption that for all \( t \in [0, \infty) \) it holds that \( \Theta_t = \Theta_0 - \int_0^t \mathscr{F}(\Theta_s) \, ds \) shows that for all \( r, s, t \in [0, \infty) \) with \( r \leq s \leq t \) it holds that

```
\|\Theta_t - \Theta_s\|_2 = \left\|\int_s^t \mathscr{F}(\Theta_u) \, du\right\|_2 \leq \int_s^t \|\mathscr{F}(\Theta_u)\|_2 \, du \leq \int_r^\infty \|\mathscr{F}(\Theta_u)\|_2 \, du = \mathscr{G}_r. \tag{9.146}
```

Next note that (9.144) and (9.145) imply that \( \infty > \mathscr{G}_0 \geq \lim\sup_{r \to \infty} \mathscr{G}_r = 0 \). Combining this with (9.146) demonstrates that there exist \( \psi \in \mathbb{R}^9 \) which satisfies

```
\lim\sup_{t \to \infty} \|\Theta_t - \psi\|_2 = 0. \tag{9.147}
```

In the next step of our proof of items (i), (ii), (iii), and (iv) we show that \( \mathcal{L}(\Theta_t), \ t \in [0, \infty), \) converges to \( \mathcal{L}(\psi) \) with convergence order 1. We accomplish this by bringing a suitable differential inequality for the reciprocal of the function \( \mathbf{L} \) in (9.128) into play (see (9.150) below for details). More specifically, observe that (9.135), (9.145), (9.130), and (9.126) ensure that for almost all \( t \in [0, \infty) \) it holds that

```
\mathbf{L}'(t) = -\|\mathscr{F}(\Theta_t)\|_2^2 \leq -\mathbf{c}^{-2}[\mathbf{L}(t)]^{2\alpha}. \tag{9.148}
```

Hence, we obtain that \( \mathbf{L} \) is non-increasing. This proves that for all \( t \in [0, \infty) \) it holds that \( \mathbf{L}(t) \leq \mathbf{L}(0) \). This and the fact that for all \( t \in [0, \tau) \) it holds that \( \mathbf{L}(t) > 0 \) establish that for almost all \( t \in [0, \tau) \) it holds that

```
\mathbf{L}'(t) \leq -\mathbf{c}^{-2}[\mathbf{L}(t)]^{(2\alpha - 2)}[\mathbf{L}(t)]^2 \leq -\mathbf{c}^{-2}[\mathbf{L}(0)]^{(2\alpha - 2)}[\mathbf{L}(t)]^2 = -\mathfrak{D}^{-1}[\mathbf{L}(t)]^2. \tag{9.149}
```

Therefore, we obtain that for almost all \( t \in [0, \tau) \) it holds that

```
\frac{\partial}{\partial t} \left( \frac{\mathfrak{D}}{\mathbf{L}(t)} \right) = - \left( \frac{\mathfrak{D}\, \mathbf{L}(t)}{[\mathbf{L}(t)]^2} \right)^{-1} \geq 1. \tag{9.150}
```

Furthermore, note that the fact that for all \( t \in [0, \tau) \) it holds that \( [0, t] \ni s \mapsto \mathbf{L}(s) \in (0, \infty) \) is absolutely continuous shows that for all \( t \in [0, \tau) \) it holds that \( [0, t] \ni s \mapsto \mathfrak{D}\mathbf{L}(s)^{-1} \in (0, \infty) \) is absolutely continuous. This and (9.150) imply that for all \( t \in [0, \tau) \) it holds that

```
\frac{\mathfrak{D}}{\mathbf{L}(t)} - \frac{\mathfrak{D}}{\mathbf{L}(0)} \geq t. \tag{9.151}
```

Hence, we obtain that for all \( t \in [0, \tau) \) it holds that

```
\frac{\mathfrak{D}}{\mathbf{L}(t)} \geq \frac{\mathfrak{D}}{\mathbf{L}(0)} + t. \tag{9.152}
```

Therefore, we obtain that for all \( t \in [0, \tau) \) it holds that

```
\mathfrak{D}\left( \frac{\mathfrak{D}}{\mathbf{L}(0)} + t \right)^{-1} \geq \mathbf{L}(t). \tag{9.153}
```