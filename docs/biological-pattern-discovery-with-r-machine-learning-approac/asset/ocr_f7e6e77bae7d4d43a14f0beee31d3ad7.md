# 234 Biological Pattern Discovery with R

as below, where $\Theta$ stands for a set of model parameters and $\mathcal{H}$ stands for a set of hyper-parameters,

```
$f_{B|E}(\mathbf{B}) \propto f_{E|B}(\mathbf{E})f_B(\Theta)f_{	heta|\mathcal{H}}(\Theta) \quad (5.36)$
```

The posterior for monitoring replicated spectra is defined as below,

```
$f_{B|E}(\mathbf{B}) \propto \prod_{m=1}^M (\sigma_{m,S}^2)^{-\omega_S}(\sigma_{m,F}^2)^{-\omega_F} \exp\left-\sum_{m=1}^M v_m\right) \quad (5.37)$
```

```
\prod_{m=1}^M w_m^{\alpha_w-1} \exp(-eta_w w_m)$
```

In the above equation, $v_m$ is defined as below,

```
$v_m = \frac{e_t^m \Gamma_m}{\sigma_{m,F}^2} + \frac{\hat{d}_t^m}{\sigma_{m,S}^2} + \frac{\beta_{m,F}}{\sigma_{m,S}^2} \quad (5.38)$
```

The noise threshold variable $\mathbf{w}$ can be estimated by maximising the posterior and is shown below,

```
$w_m = \beta_w + \frac{1}{2M} \kappa_{\sigma_{m,F}}^{-2} \mathbf{e}_m^t \mathbf{He}_m}{\alpha_w-1} \quad (5.39)$
```

In the above equation, $\mathbf{H}$ is an entropy matrix and is defined as

```
$$\mathbf{H} = \text{diag}(\{[r_i(1-r_i)]_{i=1}^N\) \quad (5.40)$
```

The next is the derivative of the error term $t_i(s_i-b_i)^2$. Because there is a sigmoid term in the expression of $t_i$, the derivative is slightly complicated. Therefore, a linear approximation is used in BWH which is shown below,

```
$t_i(s_i-b_i) + r_i(1-r_i)(s_i-b_i)^2 \approx t_i(s_i-b_i) \quad (5.41)$
```

Figure 5.18 shows the hierarchical structure of BWH. The Bayesian Whittaker-Henderson package can request an alignment of a peak across multiple replicates via an email.

Figure 5.19 shows an spectra of the first peak from multiple replicates in a replicated spectra