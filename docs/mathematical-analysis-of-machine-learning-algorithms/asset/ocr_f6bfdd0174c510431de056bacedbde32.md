The confidence interval estimate in Lemma 17.8 can be used to obtain a regret bound for the UCB method in Algorithm 17.2, and the proof is similar to that of Theorem 16.3.

# **Theorem 17.11**

*Assume that in the stochastic linear bandit model, \(r_t(x_t,a_t)\in[0,1]\) and \(\|w_*\|_2\le B\) for some constant \(B\). Let \(\mu_t(x,a)=\mathbb{E}_{\epsilon_t(x,a)}r_t(x,a)=w_*^\top\psi(x,a)\). Let \(a_*(x)\in\arg\max_a\mu_t(x,a)\) be the optimal arm for each context \(x\). Then in Algorithm 17.2, with probability at least \(1-\delta\),*

$$\mathbb{E}\sum_{t=1}^{T}[\mu_t(x_t,a_*(x_t))-\mu_t(x_t,a_t)]\le 3\sqrt{\left|\ln\frac{|A_T|}{\lambda}\right|\sum_{t=1}^{T}\beta_{t-1}^2+2\ln\frac{|A_T|}{\lambda}}.$$

where \(\{\beta_t\}\) is any sequence that satisfies (17.9).

**Proof**  We have for \(t\ge 1\),

$$\begin{aligned}
w_*^\top\psi(x_t,a_*(x_t))
&\le w_{t-1}^\top\psi(x_t,a_*(x_t))+\beta_{t-1}\sqrt{\psi(x_t,a_*(x_t))^\top A_{t-1}^{-1}\psi(x_t,a_*(x_t))}\\
&\le w_{t-1}^\top\psi(x_t,a_t)+\beta_{t-1}\sqrt{\psi(x_t,a_t)^\top A_{t-1}^{-1}\psi(x_t,a_t)}\\
&\le w_*^\top\psi(x_t,a_t)+2\beta_{t-1}\sqrt{\psi(x_t,a_t)^\top A_{t-1}^{-1}\psi(x_t,a_t)}.
\end{aligned}$$

where the first and the third inequalities used Lemma 17.8. The second inequality is due to the UCB choice of \(a_t\) in Algorithm 17.2.

Let \(E_t\) be the event of \(\|\psi(x_t,a_t)\|_{A_{t-1}}\le 1\). Since \(w_*^\top\psi(x_t,a)\in[0,1]\), we have

$$w_*^\top\psi(x_t,a_*(x_t))-w_*^\top\psi(x_t,a_t)\le 2\beta_{t-1}\|\psi(x_t,a_t)\|_{A_{t-1}^{-1}}\mathbf{1}(E_t)+\mathbf{1}(E_t^c).$$

By summing over \(t=1\) to \(t=T\), we obtain

$$\begin{aligned}
\sum_{t=1}^{T}[\mu_t(x_t,a_*(x_t))-\mu_t(x_t,a_t)]
&\le 2\sum_{t=1}^{T}\beta_{t-1}\|\psi(x_t,a_t)\|_{A_{t-1}^{-1}}\mathbf{1}(E_t)+\sum_{t=1}^{T}\mathbf{1}(E_t^c)\\
&\le 2\sum_{t=1}^{T}\beta_{t-1}\sqrt{\frac{2\|\psi(x_t,a_t)\|_{A_{t-1}^{-1}}^2}{1+\|\psi(x_t,a_t)\|_{A_{t-1}^{-1}}^2}}+2\sum_{t=1}^{T}\frac{\psi(x_t,a_t)^\top A_{t-1}^{-1}\psi(x_t,a_t)}{1+\psi(x_t,a_t)^\top A_{t-1}^{-1}\psi(x_t,a_t)}\\
&\le 3\sqrt{\sum_{t=1}^{T}\beta_{t-1}^2}\sqrt{\sum_{t=1}^{T}\frac{\psi(x_t,a_t)^\top A_{t-1}^{-1}\psi(x_t,a_t)}{1+\psi(x_t,a_t)^\top A_{t-1}^{-1}\psi(x_t,a_t)}}+2\ln\frac{|A_T|}{\lambda}.
\end{aligned}$$

The second inequality used simple algebraic inequalities under \(E_t\) and \(E_t^c\). The third inequality used the Cauchy–Schwarz inequality and Lemma 13.9. We can now apply Lemma 13.9 again to obtain the desired bound. □