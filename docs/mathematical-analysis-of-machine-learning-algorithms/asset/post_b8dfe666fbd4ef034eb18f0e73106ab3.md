
**Proof.** We obtain from Lemma 2.15 and Theorem 13.2 that with probability at least $1-\delta$,

$$
\begin{aligned}
-\sum_{i=1}^{n}\xi_i
&< \frac{\ln(1/\delta)}{\lambda}+\frac{1}{\lambda}\sum_{i=1}^{n}\ln\left(1+(e^{-\lambda}-1)\mathbb{E}_{Z_i^{(y)}}\xi_i\right) \\
&\leq \frac{\ln(1/\delta)}{\lambda}+\frac{1}{\lambda}\sum_{i=1}^{n}(e^{-\lambda}-1)\mathbb{E}_{Z_i^{(y)}}\xi_i.
\end{aligned}
$$

This implies the first bound. Moreover, with probability at least $1-\delta$,

$$
-\sum_{i=1}^{n}[1-\xi_i]<\frac{\ln(1/\delta)}{\lambda}+\frac{1}{\lambda}\sum_{i=1}^{n}\ln\left(1+(e^{-\lambda}-1)\mathbb{E}_{Z_i^{(y)}}[1-\xi_i]\right)
$$

implies that

$$
\begin{aligned}
\sum_{i=1}^{n}\xi_i
&< \frac{\ln(1/\delta)}{\lambda}+\frac{1}{\lambda}\sum_{i=1}^{n}\ln\left(1+(e^{\lambda}-1)\mathbb{E}_{Z_i^{(y)}}\xi_i\right) \\
&\leq \frac{\ln(1/\delta)}{\lambda}+\frac{1}{\lambda}\sum_{i=1}^{n}(e^{\lambda}-1)\mathbb{E}_{Z_i^{(y)}}\xi_i.
\end{aligned}
$$

This implies the second bound.

We can also obtain the following Bennett/Bernstein-style inequality, which is often referred to as the Freedman’s inequality (Freedman, 1975).

### Theorem 13.6 (Freedman’s Inequality)

*Consider a sequence of random functions $\xi_1(S_1),\ldots,\xi_n(S_n)$. Assume that $\xi_i\geq\mathbb{E}_{Z_i^{(y)}}\xi_i-b$ for some constant $b>0$.*

Then for any $\lambda\in(0,3/b)$, with probability at least $1-\delta$,

$$
\forall n>0:\quad \sum_{i=1}^{n}\mathbb{E}_{Z_i^{(y)}}\xi_i<\sum_{i=1}^{n}\xi_i+\frac{\lambda\sum_{i=1}^{n}\operatorname{Var}_{Z_i^{(y)}}(\xi_i)}{2(1-\lambda b/3)}+\frac{\ln(1/\delta)}{\lambda}.
$$

*This implies that for all $\sigma>0$, with probability at least $1-\delta$:*

$$
\forall n>0:\quad \sum_{i=1}^{n}\mathbb{E}_{Z_i^{(y)}}\xi_i<\sum_{i=1}^{n}\xi_i+\sigma\sqrt{2\ln(1/\delta)}+\frac{b\ln(1/\delta)}{3}\quad\text{or}\quad\sum_{i=1}^{n}\operatorname{Var}_{Z_i^{(y)}}(\xi_i)>\sigma^2.
$$

**Proof.** Using the logarithmic moment generating function (2.13), we obtain the first inequality directly from the first inequality of Theorem 13.2.

Moreover, we can obtain from the second inequality of Theorem 13.2 with $A_n=\{S_n:\sum_{i=1}^{n}\operatorname{Var}_{Z_i^{(y)}}(\xi_i)\leq\sigma^2\}$, $z_n=\sum_{i=1}^{n}\mathbb{E}_{Z_i^{(y)}}\xi_i-\epsilon-\epsilon^2b/(6\sigma^2)$, and the rate function estimate corresponding to the third inequality of Lemma 2.9:

$$
\Pr\left[\exists n>0:\sum_{i=1}^{n}\xi_i\leq z_n\text{ and }S_n\in A_n\right]\leq\exp\left(-\frac{\epsilon^2}{2\sigma^2}\right).
$$

This implies the second desired inequality with $\epsilon=\sigma\sqrt{2\ln(1/\delta)}$.

Under the conditions of Theorem 13.6, we may also obtain (see Exercise 13.1) for $V_0>0$, with probability at least $1-\delta$:

$$
\mathbb{E}\exp\left(\lambda\left\|\sum_{s=1}^{t}\epsilon_s X_s\right\|_{\Lambda_t^{-1}}^2\right)\leq\left|\Lambda_0^{-1}\Lambda_t\right|^{1/2}.
$$

Using Markov inequality, we obtain

$$
\Pr\left(\left\|\sum_{s=1}^{t}\epsilon_s X_s\right\|_{\Lambda_t^{-1}}^2\geq z\right)\exp(\lambda z)\leq\left|\Lambda_0^{-1}\Lambda_t\right|^{1/2}.
$$

Now we can take $\lambda=\sigma^{-2}/2$ and $\exp(\lambda z)=|\Lambda_0^{-1}\Lambda_t|^{1/2}/\delta$ to obtain the desired bound.

The main application of self-normalizing vector martingale inequality is to bound the confidence interval for linear sequential prediction problems, shown by the following example. Such a result can be used to analyze the regret of linear contextual bandits (see Section 17.2).

### Example 13.8

Consider a sequence of observations $\{(X_1,Y_1),\ldots,(X_t,Y_t),\ldots\}$, and at each time $t$, $X_t$ may depend on $S_{t-1}=\{(X_1,Y_1),\ldots,(X_{t-1},Y_{t-1})\}$. Assume that $Y_t\mid X_t$ is independent of $S_{t-1}$, and generated according to a model

$$
Y_t=f_*(X_t)+\epsilon_t,\qquad f_*(X_t)=w_*^\top X_t,
$$

where $\epsilon_t$ is a zero-mean sub-Gaussian noise as in Theorem 13.7. Assume that at each time $t$, we solve

$$
\widehat w_t=\mathop{\arg\min}_{w}\left[\sum_{s=1}^{t}(X_s^\top w-Y_s)^2+\lambda\|w\|^2\right].
$$

We can take $\Lambda_0=\lambda I$ in Theorem 13.7, $\widehat f_t(x)=\widehat w_t^\top x$, and obtain the following bound of prediction confidence interval (see the proof of Theorem 17.8):

$$
|\widehat f_t(X)-f_*(X)|\leq\left[\sqrt{\lambda}\|w_*\|+\left\|\sum_{s=1}^{t}\epsilon_sX_s\right\|_{\Lambda_t^{-1}}\right]\|X\|_{\Lambda_t^{-1}}.
$$

The result is analogous to the result of Lemma 9.34. We note that due to the dependency of $X_s$ and $S_{s-1}$, Lemma 9.34 cannot be applied. Self-normalizing martingale inequality can be used to obtain a confidence interval estimation. However, for independent data, the bound from Theorem 13.7 is worse than that of Lemma 9.34 by an extra factor $\sqrt{\ln|\Lambda_t/\lambda|}$. We know from Proposition 15.8 that this log-determinant term is $\widetilde{O}(\sqrt d)$ for $d$-dimensional problems.

One may also obtain a Bennett-style self-normalizing vector martingale inequality. We first introduce a lemma.

### Lemma 13.9

Let $\Sigma_0$ be a $d\times d$ symmetric positive definite matrix, and $\{\psi(X_t)\}$ be a sequence of vectors in $\mathbb{R}^d$. Let $\Sigma_t=\Sigma_0+\sum_{s=1}^{t}\psi(X_s)\psi(X_s)^\top$, then

$$
\sum_{s=1}^{t}\frac{\psi(X_s)^\top\Sigma_{s-1}^{-1}\psi(X_s)}{1+\psi(X_s)^\top\Sigma_{s-1}^{-1}\psi(X_s)}\leq\ln\left|\Sigma_0^{-1}\Sigma_t\right|.
$$

By setting $\lambda = 0.5\alpha^{-2}$, we obtain

$$
\sum_{s=1}^{t} \frac{2\epsilon_s f_s - f_s^2}{b_s} \le 2\alpha^2 \ln(2/\delta). \tag{13.3}
$$

Moreover, since

$$
(1 - b_s^{-1})\epsilon_s^2 \le \alpha^2,
$$

we obtain with probability at least $1 - \delta/2$,

$$
\sum_{s=1}^{t}(1 - b_s^{-1})\epsilon_s^2 \le \frac{1}{\lambda\alpha^2}\sum_{s=1}^{t}(e^{\lambda\alpha^2} - 1)(1 - b_s^{-1})\mathbb{E}_{\epsilon_s}\epsilon_s^2 + \frac{\ln(2/\delta)}{\lambda}.
$$

The inequality uses the second inequality of Theorem 13.5. We now set $\lambda = 0.5\alpha^{-2}$, and obtain

$$
\begin{aligned}
\sum_{s=1}^{t}(1 - b_s^{-1})\epsilon_s^2
&\le 1.3\sigma^2\sum_{s=1}^{t}(1 - b_s^{-1}) + 2\alpha^2\ln(2/\delta) \\
&\le 1.3\sigma^2\ln|\Lambda_0^{-1}\Lambda_t| + 2\alpha^2\ln(2/\delta).\tag{13.4}
\end{aligned}
$$

The second inequality used Lemma 13.9.

The result of the theorem follows by taking the union bound of the two events corresponding to (13.3) and (13.4) with probability $1 - \delta/2$ each, and (13.2). $\square$

A similar proof can be used to obtain a more refined result, with an even weaker dependence on the range of $\epsilon_t$. Such a result is useful for the analysis of variance-weighted linear regression. We leave it as Exercise 13.7.

## 13.3 Uniform Convergence

Similar to iid problems, it is possible to derive martingale uniform convergence results. Such results are useful for analyzing statistical estimation in the sequential decision setting, such as estimation problems in online learning, bandits, and reinforcement learning.

Consider a real-valued function class $\mathcal{F}$ on $\mathcal{Z}$, and a sequence of observations $Z_1,\dots,Z_n \in \mathcal{Z}$, and let $\mathcal{S}_n = \{Z_1,\dots,Z_n\}$. We assume that each $Z_t$ may depend on $\mathcal{S}_{t-1}$. In uniform convergence, we are generally interested in estimating the following quantity:

$$
\sup_{f\in\mathcal{F}}\left[\frac{1}{n}\sum_{i=1}^{n}\left[-f(Z_i)+\mathbb{E}_{Z_i^{(y)}}f(Z_i)\right]\right].
$$

However, by using logarithmic moment generating function directly, one can get a more general and simplified result as a direct consequence of Theorem 13.2. In the following theorem, $M(\epsilon,\mathcal{F},\|\cdot\|_\infty)$ is the $\epsilon L_\infty$ packing number of $\mathcal{F}$ defined in Chapter 5, with the metric $\|f\|_\infty = \sup_Z |f(Z)|$.

### Theorem 13.11

*We have for any $\lambda>0$, with probability at least $1-\delta$, for all $n\ge 1$ and $f\in\mathcal F$,*

$$
\left[-\sum_{i=1}^{n}f(Z_i)-\frac{1}{\lambda}\sum_{i=1}^{n}\ln\mathbb E_{Z_i^{(y)}}e^{-\lambda f(Z_i)}\right]\le \inf_{\epsilon>0}\left[2n\epsilon+\frac{\ln\bigl(M(\epsilon,\mathcal F,\|\cdot\|_\infty)/\delta\bigr)}{\lambda}\right].
$$

*Moreover, for all $n\ge 1$,*

$$
\mathbb E\sup_{f\in\mathcal F}\left[-\sum_{i=1}^{n}f(Z_i)-\frac{1}{\lambda}\sum_{i=1}^{n}\ln\mathbb E_{Z_i^{(y)}}e^{-\lambda f(Z_i)}\right]\le \inf_{\epsilon>0}\left[2n\epsilon+\frac{\ln\bigl(M(\epsilon,\mathcal F,\|\cdot\|_\infty)\bigr)}{\lambda}\right].
$$

**Proof.** Let $\mathcal F_\epsilon\subset\mathcal F$ be an $\epsilon$ maximal packing of $\mathcal F$, with $|\mathcal F_\epsilon|\le M(\epsilon,\mathcal F,\|\cdot\|_\infty)$. We obtain from Theorem 13.2, and the uniform bound over $\mathcal F_\epsilon$, that with probability at least $1-\delta$,

$$
\sup_{f\in\mathcal F_\epsilon}\left[-\sum_{i=1}^{n}f(Z_i)-\frac{1}{\lambda}\sum_{i=1}^{n}\ln\mathbb E_{Z_i^{(y)}}e^{-\lambda f(Z_i)}\right]\le \frac{\ln\bigl(M(\epsilon,\mathcal F,\|\cdot\|_\infty)/\delta\bigr)}{\lambda}.
$$

Since $\mathcal F_\epsilon$ is also an $\epsilon$-$L_\infty$ cover of $\mathcal F$ (see Theorem 5.2), we obtain

$$
\sup_{f\in\mathcal F}\left[-\sum_{i=1}^{n}f(Z_i)-\frac{1}{\lambda}\sum_{i=1}^{n}\ln\mathbb E_{Z_i^{(y)}}e^{-\lambda f(Z_i)}\right]
$$

$$
\le 2n\epsilon+\sup_{f\in\mathcal F_\epsilon}\left[-\sum_{i=1}^{n}f(Z_i)-\frac{1}{\lambda}\sum_{i=1}^{n}\ln\mathbb E_{Z_i^{(y)}}e^{-\lambda f(Z_i)}\right].
$$

This implies the first inequality. The second inequality is left as an exercise. $\square$

If the loss function satisfies the variance condition, then we can obtain the following uniform convergence result.

### Corollary 13.12

*Assume that for all $f\in\mathcal F$ and $Z_t$: $-f(Z_t)+\mathbb E_{Z_t^{(y)}}f(Z_t)\le b$, and the following variance condition holds for all $f\in\mathcal F$ and $S_t$:*

$$
\operatorname{Var}_{Z_t^{(y)}}[f(Z_t)]\le c_0^2+c_1\mathbb E_{Z_t^{(y)}}[f(Z_t)],
$$

*then with probability at least $1-\delta$, for all $f\in\mathcal F$,*

$$
(1-\lambda c_1\phi(\lambda b))\sum_{t=1}^{n}\mathbb E_{Z_t^{(y)}}[f(Z_t)]\le \sum_{t=1}^{n}f(Z_t)+\lambda n c_0^2\phi(\lambda b)
$$

$$
\qquad +\inf_{\epsilon>0}\left[2n\epsilon+\frac{\ln\bigl(M(\epsilon,\mathcal F,\|\cdot\|_\infty)/\delta\bigr)}{\lambda}\right],
$$

*where $\phi(z)=(e^z-z-1)/z^2$.*
