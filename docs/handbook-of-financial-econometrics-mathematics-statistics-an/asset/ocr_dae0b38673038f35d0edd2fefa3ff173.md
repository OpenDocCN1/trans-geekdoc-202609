# **Remark 41.3.10:**

The optimal level $L^*$ in (41.39) coincides with that in Hiberink and Rogers (2002). Our ODE approach also works for the perpetual American put option. Indeed, we determine the optimal stopping times when only downward jumps are allowed. Also we calculate exactly the price of the perpetual American put option.

For general two-sided jump distributions, we get a necessary condition for the coefficient constant $Q$. This necessary condition will play an important role in Section 41.4.

# **Proposition 41.3.11:**

*If $(\alpha_+, B_+)$ is minimal, $Z_{(-)}$ is separable, and $p > 0$, then the constant vector $Q$ for $\phi$ satisfies $\sum_{i=1}^S Q_i = g(0)$ and*

$\alpha_+\left(\int_0^\infty g(-y)e^{B_+ y}dy\right)e^{xB_+}b_+^T = \alpha_+\left[\sum_{i=1}^S Q_i(\rho_i I - B_+)^{-1}\right]e^{xB_+}b_+^T,\quad \forall x > 0.\tag{41.44}$

**Proof.** Please refer to Appendix 41A.

# **41.4 The Constant Vector $Q$: The Second Method**

In this section, we consider a more general process whose upward jumps are determined by a general Levy measure and downward jumps by a compound Poisson process with a mixture of exponential jump distributions, we show that a vector $Q$ satisfies a system of linear equations, then a conjectured function must be the desired function $\phi$. To find a solution to the system of equations, instead of directly inverting the system of equations, we exploit the technique in Dufresne and Gerber (1989) to obtain an explicit solution for $\phi$. With this explicit formula, we compute especially in Example 41.4.6 the optimal default-triggering level. We also provide an example (Example 41.4.7) which shows that we can calculate certain option prices with finite maturity up to a Fourier transform.

Let $X = (X_t, \{P_x\}_{x\in R})$ be the Levy process given by

$X_t = X_0 + X_t^{(+)} - Z_t,\; t \ge 0.\tag{41.45}$

Here $X^{(+)} = (X_t^{(+)}; t \ge 0)$ is a Levy process on $R$ such that it starts at and has a nontrivial diffusion part and no downward jumps, and $Z$ is a compound Poisson process that is independent of $X^{(+)}$ with jump distribution given by $f_{(+)} = PH(\alpha_+, B_+)$. As before, under $P_x, X_0 = x$ a.s. Clearly, the process in (41.45) is a generalization of (41.4).