Now, for each $n$, define a $C_0^2(R_-)$-function $h_n$ such that $h_n = g_n$ on $(-\infty, 1/n)$, $h_n(0)=g(0)$ and $(h_n)$ is uniformly bounded. Then it is obvious that $(h_n)$ is the desired sequence. This completes the proof.

# Lemma 41.A.2: The following distributions are absolutely continuous with respect to Lebesgue measure:

+   (1) The distribution $P_x[X_{\tilde\tau}<0, X_{\tilde\tau}\in\bullet]$, where $X$ is defined by (41.4), and $\tilde\tau$ is defined as in the proof of Theorem 41.2.4.
+   (2) the distribution $P_x[X_\tau<0, X_\tau\in\bullet]$ for $x>0$, where $X$ is defined by (41.45).

Proof. We only show (2), and the proof of (1) follows similarly. Let $N$ be a Borel set in $(-\infty,0)$ with Lebesgue measure zero. Write $J_n$ for the $n$th jump tie of the compound Poisson process $Z$. Observe that, for $x>0$,

$$P_x[X_\tau<0, X_\tau\in N] = \sum_{n=1}^{\infty} P_x[X_\tau<0, X_\tau\in N, \tau=J_n].$$

We first show that $P_x[X_\tau<0, X_\tau\in N, \tau=J_1]=0$. Note that since $X^{(+)}$, $J_1$ and $Y_1$ are independent, so are $X_{J_1}^{(+)}$ and $Y_1$. Hence, we have

$$P_x[X_\tau<0, X_\tau\in N, \tau=J_1] = P_x\big[X_{J_1}^{(+)}-Y_1\in N, X_{J_1}^{(+)}-Y_1<0, \tau=J_1\big] \le P_x\big[X_{J_1}^{(+)}-Y_1\in N\big] = \int P_x[z-Y_1\in N]\,dG(z),$$

where $G$ is the distribution of $X_{J_1}^{(+)}$. Since $Y_1$ has an absolutely continuous distribution, from the last inequality we deduce that $P_x[X_\tau<0, X_\tau\in N, \tau=J_1]=0$. In general, for each $n\ge2$, we have by the strong Markov property that $P_x[X_\tau<0, X_\tau\in N, \tau=J_n]=E_x[\mathbf{1}_{\tau>J_{n-1}}P_{X_{J_{n-1}}}[X_\tau<0, X_\tau\in N, \tau=J_1]]=0$, since $J_{n-1}$ is an $(F_t)$-stopping time and $X_{J_{n-1}}>0$ on $\{\tau>J_{n-1}\}$. This implies that $P_x[X_\tau<0, X_\tau\in\bullet]$ is absolutely continuous with respect to Lebesgue measure for every $x>0$.

# Theorem 41.A.3 (Dynkin's formula). Let $X=(X(t))$ be an $R^n$-valued jump-diffusion, and let $k\in C_0^2(R^n)$. If $\eta$ is a stopping time such that $E_x(\eta)<\infty$, then