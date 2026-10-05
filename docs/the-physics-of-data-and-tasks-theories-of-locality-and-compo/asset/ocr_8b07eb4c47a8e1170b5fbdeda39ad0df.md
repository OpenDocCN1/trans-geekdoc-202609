# B.5 STATISTICAL MECHANICS OF GENERALIZATION IN KERNEL REGRESSION 193

Equation 265 has been validated numerically for both synthetic and real datasets.

In Equation 264, $\kappa_\lambda(P)/P$ plays the role of a threshold: the modal contributions to the error term 0 for $ho$ such that $\Lambda_ho \gg \kappa_\lambda(P)/P$, and $\mathbb{E}[c_ho^2]$ for $ho$ such that $\Lambda_ho \ll \kappa_\lambda(P)/P$. This is equivalent to saying that kernel regression can capture modes corresponding to the eigenvalues larger than $\kappa_\lambda(P)/P$ (see [jac20a; Jac20b]).

In the rigidless limit $\lambda ightarrow 0^+$, this threshold asymptotically approaches to the P-th eigenvalue of the student, resulting in the intuitive picture presented in the main text. Given $P$ training points, ridgeless regression learns only the highest eigenvalues. In particular, we assume that the kernel and the target function projections follow power laws. $\Lambda_ho \sim ho^{-a}$ and $\mathbb{E}[c_ho^2] \sim ho^{-b}$. Furthermore, we can approximate the summations over $ho$ with an integral using the Euler-Maclaurin formula. Hence, we estimate the eigenvalues with their asymptotic limit $\Lambda_ho = Aho^{-a}$. Since, $\kappa_0(P)/P ightarrow 0$ as $P ightarrow \infty$, the two operations result in an error that is asymptotically independent of P. In particular,

```
$$\frac{\kappa_0(P)}{P} = \frac{\kappa_0(P)}{P} \int_0^{\infty} \frac{\rho}{\Lambda_ho + \kappa_0(P)/P} d\rho + O(1)\\n=\frac{\kappa_0(P)}{P} \left( \frac{\kappa_0(P)}{P} \right) \int_0^{\infty} \frac{\sigma}{\sigma^2-1} \frac{1}{1+\sigma} a^{a-1} d\sigma + O(1). \quad (266)$
```

Since the integration over $\sigma$ is finite and independent of $P$, we obtain $\kappa_0(P)/P = O(P^{-a})$. Similarly, we find that the mode-independent prefactor $\delta_\lambda$ $(\kappa_\lambda(P)/P |_{\lambdaightarrow 0}) = O(1)$.

As a result, we have

```
$$\mathbb{E}(P) \sim \sum_{\rho} \frac{P^{-2a}}{(\Lambda_ho + P^{-a})^2} \mathbb{E}[c_ho^2]. \quad (267)$
```

Following the intuitive argument about the thresholding of action, we can split the summation in Equation 267 into modes where $\Lambda_ho \gg \kappa_0(P)/P$, $\Lambda_ho \sim \kappa_0(P)/P$ and $\Lambda_ho \ll \kappa_0(P)/P$,

```
$$\mathbb{E}(P) \sim \sum_{\rho \gg P} \frac{P^{-2a}}{(\Lambda_ho + P^{-a})^2} \mathbb{E}[c_ho^2] + \sum_{\rho \ll P} \frac{1}{2} \mathbb{E}[c_ho^2] + \quad (268)$
```

Finally, Equation 61 is obtained by noting that, under the assumption on the decay of $\mathbb{E}[c_ho^2]$, for $ho \ll P$ is subleading in $P$, whereas the contribution of the summation over $ho \ll P$ can be merged together.