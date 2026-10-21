we get the system of linear equations

$$\sum_{i=1}^{m+1} Q_i = g(0),$$
$$\sum_{i=1}^{m+1} \frac{Q_i \eta_j}{\rho_i + \eta_j} = \int_{-\infty}^0 g(y)\eta_j e^{\eta_j y} dy, \quad 1 \le j \le m. \tag{41.48}$$

The following proposition confirms our conjecture.

# Proposition 41.4.2: If $Q$ satisfies (41.48) for some bounded Borel-measurable function $g$, then

$$\Phi(x) = E_x[e^{-r\tau} g(X_\tau)] = \sum_{i=1}^S Q_i e^{\rho_i x}, \text{ for } x \ge 0. \tag{41.49}$$

**Proof.** Please refer to Appendix 41A.

In fact, the coefficient matrix of equations (41.48) is invertible. Hence, we can write $Q$ in a general matrix form. Instead of the matrix form, we exploit the technique in Dufresne and Gerber (1989) to get an explicit formula for $Q$.

# Theorem 41.4.3: Assume that $X$ satisfies (41.45) and $f_{(+) }(y)$ is given by (41.46). Then, for any bounded Borel function $g : R_- \to R$, we have $\Phi = E_x[e^{-r\tau} g(X_\tau)] = \sum_{i=1}^S Q_i e^{\rho_i x}$ on $R_+$, where, for $1 \le h \le m + 1$,

$$Q_h = \frac{1}{\rho_h \prod_{i=1, i \ne h}^{m+1} (-\rho_h + \rho_i)} \sum_{j=1}^{m+1} R_j \left( \prod_{k=1}^{m+1} (\eta_j + \rho_k) \right) \prod_{i=1, i \ne j}^{m+1} \frac{-\rho_h - \eta_i}{\eta_j - \eta_i} \tag{41.50}$$

and
$$R_j = g(0) - \int_0^{\infty} g(-y)\eta_j e^{-\eta_j y} dy. \tag{41.51}$$
Here we set $\eta_{m+1}=0.$

**Proof.** Clearly, the system (41.48) is equivalent to the system of linear equations
$$\sum_{i=1}^{m+1} \frac{Q_i \rho_i}{\rho_i + \eta_j} = R_j, \ 1 \le j \le m + 1, \tag{41.52}$$

where the $R_j$ are given by (41.51). Since the system (41.48) admits at most one solution, so does (41.52).