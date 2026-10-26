![](bbox=[0.07, 0.09, 0.44, 0.26])

![](bbox=[0.49, 0.09, 0.8, 0.26])

Figure 6.2. Experimental results for the heat equation. The generalization error $\mathcal{E}_G$ and the training error $\mathcal{E}_T$ are shown in terms of the number of residual points $N_{\text{int}}$ ((a), and compared with the bound from Theorem 6.7) and also in terms of each other (b). Figure from Molinaro (2023).

![](bbox=[0.27, 0.42, 0.55, 0.6])

Figure 6.3. Relative generalization percentage error $\mathcal{E}_G$ in terms of the parameter dimension $d$ for the heat equation with a parametrized initial condition. Figure from Molinaro (2023).

In more detail, the initial condition considered is parametrized by $\mu$ and given by

$u_0(x; \mu) = \sum_{i=1}^{d} \frac{-1}{d m^2} \sin(m\pi(x - \mu_i)). \tag{6.11}$

Figure 6.3 demonstrates that the generalization error $\mathcal{E}_G$ does not grow exponentially (but rather sub-quadratically) in the parameter dimension $d$, and that therefore the curse of dimensionality is mitigated. Even for very large $d$ the relative generalization error is less than 2%.