where \(\hat{e}_t^{i,x} = \sum_{j=1}^N w^{ij}(e_t^{j,x} - \hat{e}_t^{i,x})\) and \(\hat{e}_t^{i,y} = \sum_{j=1}^N w^{ij}(e_t^{j,y} - \hat{e}_t^{i,y})\).

For analytical purposes, we denote the subsequent notations: \(x_t = [(x_t^1)^\mathrm{T}, ..., (x_t^N)^\mathrm{T}]^\mathrm{T}\), \(y_t = [(y_t^1)^\mathrm{T}, ..., (y_t^N)^\mathrm{T}]^\mathrm{T}\), \(\hat{e}_t^x = [(\hat{e}_t^{1,x})^\mathrm{T}, ..., (\hat{e}_t^{N,x})^\mathrm{T}]^\mathrm{T}\), \(\hat{e}_t^y = [(\hat{e}_t^{1,y})^\mathrm{T}, ..., (\hat{e}_t^{N,y})^\mathrm{T}]^\mathrm{T}\), \(\nabla G_t = [(\nabla g_t^1)^\mathrm{T}, ..., (\nabla g_t^N)^\mathrm{T}]^\mathrm{T}\), and \(\hat{W} = W \otimes I_d\). Subsequently, Algorithm 1 can be expressed in a condensed manner as follows:

```
\(x_{t+1} = \hat{W} x_t + \hat{e}_t^x - \alpha_t y_t, \quad (4.7a)\)
\(y_{t+1} = \hat{W} y_t + \hat{e}_t^y + \nabla G_{t+1} - \nabla G_t. \quad (4.7b)\)
```

**Remark 4.3.** In comparison to the current decentralized event-triggering techniques referenced in [38–41] and decentralized stochastic gradient tracking approaches mentioned in [14,16,17,36], Algorithm 1 successfully fulfills both objectives. Specifically, Algorithm 1 enhances communication efficiency while also ensuring precise convergence. Therefore it can be inferred that this chapter presents a unique decentralized optimization algorithm.

# 4.3 Convergence guarantees

In this section, we examine the convergence characteristics of ET-DSGT in terms of mean square convergence.

# 4.3.1 Preliminary results

For analytical purposes, we introduce two supporting sequences, denoted as \(\{y'_t\}\) and \(\{\xi_t\}\) and defined as follows:

```
\(y'_{t+1} = \hat{W} y'_t + \nabla F_{t+1} - \nabla F_t, \quad y'_0 = \nabla F_0, \quad (4.8)\)
\(\xi_{t+1} = \hat{W} \xi_t + \hat{e}_t^y + \varepsilon_{t+1} - \varepsilon_t, \quad \xi_0 = \varepsilon_0, \quad (4.9)\)
```

where \(\varepsilon_t^i := \nabla g^i(x_t^i, \zeta_t^i) - \nabla f^i(x_t^i)\), \(\varepsilon_t = \nabla G_t - \nabla F_t\), and \(\nabla F_t = [\nabla f^1(x_t^1)^\mathrm{T}, ..., \nabla f^N(x_t^N)^\mathrm{T}]^\mathrm{T}\). Furthermore, we establish the following definitions:

```
\(\bar{x}_t = (\frac{1}{N} \mathbf{1}_N^\mathrm{T} \otimes I_d) x_t, \quad \bar{y}'_t = (\frac{1}{N} \mathbf{1}_N^\mathrm{T} \otimes I_d) y'_t.\)
```

Subsequently, by recalling (4.4) and Assumption 4.2(ii), the subsequent conclusions can be clearly inferred:

```
\(\frac{1}{N} (\mathbf{1}_N^\mathrm{T} \otimes I_d) \hat{e}_t^x = 0, \quad \frac{1}{N} (\mathbf{1}_N^\mathrm{T} \otimes I_d) \hat{e}_t^y = 0, \quad \forall t \ge 0.\)
```

Additionally, we revisit the matrix norm denoted as \(||\cdot||\) that was introduced in [34]. This norm possesses the subsequent characteristic:

```
\(\tau_w := ||\hat{W} - \frac{1}{N} \mathbf{1}_N \mathbf{1}_N^\mathrm{T} \otimes I_d|| < 1. \quad (4.10)\)
```