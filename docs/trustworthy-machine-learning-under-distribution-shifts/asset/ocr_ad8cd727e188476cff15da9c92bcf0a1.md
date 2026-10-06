# 7.2 PROOF FOR EVIL

Further, we can evaluate the first term that:

```
$$\mathbb{E}[V_0] - \mathbb{E}[V_T] \le \mathbb{E}[V_0] - \min_{	heta,\omega} \mathbb{E}[V(\theta, \omega)]$\n$$
\le \mathbb{E}[L^*(	heta_0)] - \min \mathbb{E}[L^*(	heta_0)] + \frac{1}{16}\left(\mathbb{E}[L^*(	heta_0)] - \mathbb{E}[L(\theta_0, \omega_0)]\right)\n$$
= \mathbb{E}[L^*(	heta_0)] - \min \mathbb{E}[L^*(	heta_0)] + \frac{1}{16}\Delta_0.$
```

where we denote the initial state as $\Delta_0 = \mathbb{E}[L^*(	heta_0)] - \mathbb{E}[L(\theta_0, \omega_0)].$

Therefore, the inequality 729 can be evaluated as:

```
$$\sum_{t=0}^{T-1} ||\mathbb{E}[
abla L^*(	heta_t)]||^2 \le \frac{80}{11\eta_0}(\mathbb{E}[L^*(	heta_0)] - \min_{\theta} \mathbb{E}[L^*(	heta)]) + \frac{5}{11\eta_0}\Delta_0 + 960\kappa^4l\eta_0\frac{\sigma^2}{M},.$
```

when we select $\eta_0 = \sqrt{\frac{M(\mathbb{E}[L^*(	heta_0)]-\min \mathbb{E}[L^*(	heta_0)]}{132T\kappa^4\sigma^2}}$, and samples per minibatch, the convergence is bounded by:

```
$$\sum_{t=0}^{T-1} ||\mathbb{E}[
abla L^*(	heta_t)]||^2 \le 3\sqrt{\frac{3\kappa^4(\mathbb{E}[L^*(	heta_0)]-\\min \mathbb{E}[L^*(	heta_0)])\sigma^2}{11MT}} = \mathcal{O}(\frac{\kappa^2}{\sqrt{M}}).$ (7.31)$
```

# 7.2 Proof for EVIL

This section provides the proof of Proposition 2. By aligning the selected invariant parameters, we have the label prediction $\hat{Y}^e = \text{sgn}(\theta_{inv}^e Z^e) = \text{sgn}((m \circ \theta)^T Z^e)$ where $\text{sgn}(m \circ \theta)$ returns the sign of input value. For this we:

```
$(m \circ \theta)^T Z^e = \frac{1}{\sqrt{M}}m^T Z^e$ (7.32)\n= \frac{1}{\sqrt{M}}\left[\frac{1}{M_{inv}}m_{i\in[0,M_{inv}]}, \m_{i\in[M_{inv},M_{var}]}]^T[Z_{inv}^e, Z_{var}^e]\right]\n= \frac{1}{\sqrt{M}}\left[\frac{1}{M_{inv}}m_{i\in[0,M_{inv}]}Z_{inv}^e + \frac{1}{M_{var}}m_{i\in[M_{inv},M_{var}]}Z_{var}^e\right]. (7.33)$
```

Then the error produced by the sample process for a given environment is:

```
$$\Err^e = \frac{1}{2}|\mathbb{E}_{(X^e,Y^e)\sim e}[1 - \mathbb{E}^e[Y^e\hat{Y}^e]]| = \frac{1}{2}[1 - \mathbb{E}^e[Y^e\hat{Y}^e]].$ (7.34)$
```