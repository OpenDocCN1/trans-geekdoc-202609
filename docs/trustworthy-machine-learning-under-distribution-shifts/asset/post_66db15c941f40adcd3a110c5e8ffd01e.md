
# 7 PROOFS AND THEORETICAL ANALYSES

We have the following property according to Lemma 2 and the PL condition 12:

```
$|\nabla L^*(\theta_t) - \nabla_0 f(\theta_t, \omega_t)|| \leq |l|\omega^*(\theta_t) - \omega_t|| \leq \kappa ||\nabla_{\omega} f(\theta_t, \omega_t)|.$
```

So we can derive the above inequality as follows:

```
$E[V_{t+1}] - E[V_t]$
\leq {^\frac{\eta_0^2}{2}(1+\alpha)(1-5\rho) - 2L\eta_0(4\rho^2 + 2\rho + 2))\ - 2\alpha({\frac{3\eta_0^2}{2} - \frac{\eta_t^2}{2}}\rho^2 + \eta_t^2(2\rho^2 + \rho + 1) + \eta_0^2\eta_{\omega}^2(2\rho^2 + \rho + 1))})E|\nabla L^*(\theta_t)||^2$\
-{\{\frac{\eta_0^2}{2} - \frac{\eta_t^2}{2}})^2 - \kappa^2[(1+\alpha)(\frac{1}{2} + \frac{1}{2}) + \eta_0^2(4\rho^2 + 2\rho + 2)]$\
+ 2\alpha({\frac{3\eta_0^2}{2} + \frac{\eta_t^2}{2}}\rho^2 + \eta_t^2(2\rho^2 + \rho + 1) + \eta_0^2\eta_{\omega}^2(2\rho^2 + \rho + 1))})E|\nabla_{\omega} f(\theta_t, \omega_t)||^2$\
+ [(1+\alpha)(5\rho^2 + 2)]\frac{L\eta_t^2}{2}\
+ \alpha({\frac{2\rho^2}{2} + \frac{\eta_t^2}{2}}(5\rho^2 + 2)) + \alpha({\frac{\eta_{\omega}^2}{2} + \frac{\eta_0^2\eta_{\omega}^2}{2}}(5\rho^2 + 2))}\sigma^2.$
```

Then we require the parameters to satisfy: $\alpha = \frac{1}{16}, \rho l \leq \frac{1}{10}, \eta_0(2\rho + 1)^2\kappa l \leq \frac{1}{64}, \kappa^2\eta_{\omega}l \leq \frac{1}{128}, \rho \leq \frac{\eta_0}{2}$ and $\eta_{\omega} \leq 64\kappa^2\eta_0.$

So the inequality can be further simplified as:

```
$E[V_{t+1}] - E[V_t]$
\leq -{\frac{1}{80}}{\eta_0}|\nabla L^*(\theta_t)||^2 - \frac{41}{32}\kappa^2E|\nabla_{\omega} f(\theta_t, \omega_t)||^2 + 129\kappa^4\eta_0^2\frac{\sigma^2}{M}. (7.28)
```

Telescoping the above inequality we can get:

```
$\sum_{t=0}^{T-1} E|\nabla L^*(\theta_t)||^2 \leq {\frac{80}{11\eta_0\gamma}}(E[V_0] - E[V_T]) + 960\kappa^4\eta_0^2\frac{\sigma^2}{M}. (7.29)
```

## 7.2 PROOF FOR EVIL

Further, we can evaluate the first term that:

```
$$\mathbb{E}[V_0] - \mathbb{E}[V_T] \le \mathbb{E}[V_0] - \min_{\theta,\omega} \mathbb{E}[V(\theta, \omega)]$$
\le \mathbb{E}[L^*(\theta_0)] - \min \mathbb{E}[L^*(\theta_0)] + \frac{1}{16}\left(\mathbb{E}[L^*(\theta_0)] - \mathbb{E}[L(\theta_0, \omega_0)]\right)$$
= \mathbb{E}[L^*(\theta_0)] - \min \mathbb{E}[L^*(\theta_0)] + \frac{1}{16}\Delta_0.
```

where we denote the initial state as $\Delta_0 = \mathbb{E}[L^*(\theta_0)] - \mathbb{E}[L(\theta_0, \omega_0)].$

Therefore, the inequality 729 can be evaluated as:

```
$$\sum_{t=0}^{T-1} ||\mathbb{E}[\nabla L^*(\theta_t)]||^2 \le \frac{80}{11\eta_0}(\mathbb{E}[L^*(\theta_0)] - \min_{\theta} \mathbb{E}[L^*(\theta)]) + \frac{5}{11\eta_0}\Delta_0 + 960\kappa^4l\eta_0\frac{\sigma^2}{M},$$
```

when we select $\eta_0 = \sqrt{\frac{M(\mathbb{E}[L^*(\theta_0)]-\min \mathbb{E}[L^*(\theta_0)]}{132T\kappa^4\sigma^2}}$, and samples per minibatch, the convergence is bounded by:

```
$$\sum_{t=0}^{T-1} ||\mathbb{E}[\nabla L^*(\theta_t)]||^2 \le 3\sqrt{\frac{3\kappa^4(\mathbb{E}[L^*(\theta_0)]-\min \mathbb{E}[L^*(\theta_0)])\sigma^2}{11MT}} = \mathcal{O}(\frac{\kappa^2}{\sqrt{M}}).$ (7.31)$
```

## 7.2 Proof for EVIL

This section provides the proof of Proposition 2. By aligning the selected invariant parameters, we have the label prediction $\hat{Y}^e = \text{sgn}(\theta_{inv}^e Z^e) = \text{sgn}((m \circ \theta)^T Z^e)$ where $\text{sgn}(m \circ \theta)$ returns the sign of input value. For this we:

```
$(m \circ \theta)^T Z^e = \frac{1}{\sqrt{M}}m^T Z^e$ (7.32)
= \frac{1}{\sqrt{M}}\left[\frac{1}{M_{inv}}m_{i\in[0,M_{inv}]}, m_{i\in[M_{inv},M_{var}]}]^T[Z_{inv}^e, Z_{var}^e]\right]$
= \frac{1}{\sqrt{M}}\left[\frac{1}{M_{inv}}m_{i\in[0,M_{inv}]}Z_{inv}^e + \frac{1}{M_{var}}m_{i\in[M_{inv},M_{var}]}Z_{var}^e\right]. (7.33)$
```

Then the error produced by the sample process for a given environment is:

```
$$\Err^e = \frac{1}{2}|\mathbb{E}_{(X^e,Y^e)\sim e}[1 - \mathbb{E}^e[Y^e\hat{Y}^e]]|. (7.34)$$
```

## 7 PROOFS AND THEORETICAL ANALYSES

Here we simplify the expectation on samples from distribution $e$:

```
$E^e[y^e Y^e] = E^e\left[\text{sgn}\left(\frac{1}{M}m^T Z^e\right) Y^e\right] = \sum_{y\in\{-1,1\}} \mathbb{P}[Y^e=y] \mathbb{P}\left[\text{sgn}\left(\frac{1}{M}m^T Z^e\right)\mid Y^e=y\right]. (7.35)$
```

```
$E^e\left[\text{sgn}\left(\frac{1}{M}m^T Z^e\right)\mid Y^e=1\right]=\mathbb{P}\left[\frac{1}{M}m^T Z^e > 0\mid Y^e=1\right]-\mathbb{P}\left[\frac{1}{M}m^T Z^e \le 0\mid Y^e=1\right]=2\mathbb{P}\left[\frac{1}{M}m^T Z^e > 0\mid Y^e=1\right]-1. (7.36)$
```

Similar to Zhang et al. [183], we observe that:

```
$\mathbb{P}\left[\frac{1}{M}m^T Z^e \le 0\mid Y^e=1\right]=\mathbb{P}\left[\frac{1}{M}m^T Z^e > 0\mid Y^e=1\right]. (7.37)$
```

and plug (7.37) into (7.35) to get:

```
$Err^e = \mathbb{P}\left[\frac{1}{M}m^T Z^e \le 0\mid Y^e=1\right]. (7.38)$
```

Similar to Equation (7.33), we further decompose (7.38):

```
$Err^e = \mathbb{P}\left[\frac{1}{M_{inv}}m_{i\in[0,M_{inv}]}Z_{inv}^e+\frac{1}{M_{var}}m_{i\in[M_{inv},M_{var}]}Z_{var}^e \le 0\mid Y^e=1\right]. (7.39)$
```

Since all elements in $Z_{inv}$ are equal, the first term equals 0, Then, we have:

```
$Err^e = \mathbb{P}\left[\frac{1}{M_{var}}m_{i\in[M_{inv},M_{var}]}Z_{var}^e \le 0\mid Y^e=1\right]. (7.40)$
```

Here we assume element of $Z^e$ and $m_i$ are independent with each other, we can have $Err^e = \mathbb{P}\left[m_i Z_{var,i}^e \le 0\mid Y^e=1\right]$. It is obvious that there is one situation when the error occurs, i.e., $m_i=1$ and $Z_{var} \le 0$. In this scenario, the sparse training strategy would update the value to 0. Therefore $\mathbb{P}[m_i=0]=p^e$. For other cases where $\mathbb{P}[Z_{var,i}^e > 0]=p^e$, the value of each $m_i$ is randomly initialized and stays intact since is no error, hence $\mathbb{P}[m_i = 0] = \mathbb{P}[m_i = 1] = \frac{\mathbb{E}^e}{2}$. So, for $i \in [M_{inv}, M]$, $\mathbb{P}[m_i = 0] = 1 - \frac{\mathbb{E}^e}{2}$ and $\mathbb{P}[m_i = 1] = \frac{\mathbb{E}^e}{2}$.

To further bound the error, we denote $mZ^e_{var} = \frac{1}{M_{var}}\sum_{i \in [M_{inv}, M]} Z^e_{var}$, and we have:

```
$$\begin{aligned} \text{Err}^e &= \mathbb{P}\left[mZ^e_{var} \le 0\right] &= \mathbb{P}\left[mZ^e_{var} - \mathbb{E}[mZ^e_{var}] \le -\mathbb{E}[mZ^e_{var}] \mid Y^e = 1\right] &\le \mathbb{P}\left[|mZ^e_{var} - \mathbb{E}[mZ^e_{var}]| \ge \mathbb{E}[|mZ^e_{var}| \mid Y^e = 1\right], \quad (7.41) \\ \mathbb{E}[mZ^e_{var}] &= \text{sgn}\left[\frac{1}{M_{var}}\sum_{i \in [M_{inv}, M]} Z^e_{var} \mid Y^e = 1\right] &= 2\mathbb{P}\left[\frac{1}{M_{var}}\sum_{i \in [M_{inv}, M]} Z^e_{var} > 0 \mid Y^e = 1\right] &= (p^e)^2 - 1. \end{aligned}$$
```

Therefore, $\text{Err}^e \le 2e^{-2(p^e)^2-1}M_{var} = O(e^{-(p^e)^2})$. In contrast to the idealized bound that achieves 0 error in Zhang et al. [183], when $\theta$ is initialized with the unit norm and given a small $p^e$, the error could be considerably large. This is because the error produced by the variant parameters is largely decided by the probability $p^e$, which could further affect the pruning process. Based on such an intuition, we propose to enhance the pruning strategy by adding an additional regularization that leverages domain knowledge.

Specifically, the regularization considers the errors from distinguishing different distributions using variant parameters:

```
$$\text{Err}^d = \frac{1}{2}\mathbb{E}_{(X,Y)\sim\varepsilon}[1 - D\hat{D}] = \frac{1}{2}[1 - \mathbb{E}[D\hat{D}]], \quad \hat{D} = \text{sgn}(\theta^d_{var}Z^d) = \text{sgn}((1-\mathbf{m}) \circ \theta)^T Z^d). \quad (7.43)$$
```
