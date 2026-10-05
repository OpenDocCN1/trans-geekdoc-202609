# Spectral Pattern Discovery

```
$e_i \sim G(0, \sigma_F^2)\nd_i \sim G(0, \sigma_G^2) \quad (5.16)$
```

The BWH fidelity is defined as below, where w is the upper-bound threshold,

```
$e_i = \begin{cases} s_i - b_i & \text{if } s_i < b_i + w \ \infty & \text{otherwise} \end{cases} \quad (5.17)$
```

Based on the definition, $b_i + w$ defines a homogeneous upper-bound of noise above a baseline. Because of this, the noise from both sides of a baseline will be finally removed during a baseline estimation process for discovering peaks. Therefore, the likelihood of false signals can be minimised.

BWH has introduced an indicator for the peaks. If a wave number (a spectra analyser value) does not correspond to a peak, a unit value is assigned, otherwise a zero is assigned. The definition of this indicator is for incorporating peak information into a baseline estimation process. The indicator is defined as below,

```
$t_i = \begin{cases} 1 & \text{if } e_i < \infty \ 0 & \text{otherwise} \end{cases} \quad (5.18)$
```

Corresponding, a vector $\mathbf{t}$, which is also called an aligner vector, is used for all wave numbers (spectra analyser values). A density function of the fidelity is defined as below [Taylor, 1992], where $N$ stands for the spectral length, i.e., the number of wave numbers, is an error vector and $\Gamma = \text{diag}(\mathbf{t}),

```
$f_{\mathbf{E}|\mathbf{B}}(\mathbf{e}) = \frac{1}{(2\pi\sigma_F^2)^{N/2}} \exp\left( -\frac{\Gamma^T\Gamma}{2\sigma_F^2} \right) \quad (5.19)$
```

The prior of the smoothness is defined as a Gaussian distribution well [Taylor, 1992],

```
$f_{\mathbf{D}|\sigma_S^2}(\mathbf{d}) = \frac{1}{(2\pi\sigma_S^2)^{(N-1)/2}} \exp\left( -\frac{\mathbf{d}^T\mathbf{d}}{2\sigma_S^2} \right) \quad (5.20)$
```