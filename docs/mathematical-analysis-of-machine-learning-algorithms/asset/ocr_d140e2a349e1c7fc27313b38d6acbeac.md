Using this logarithmic moment generating function, we can now obtain the following statement from Theorem 13.11, by taking a uniform bound over $\mathcal{G}_\epsilon \times \mathcal{F}_\epsilon$, and consider both under- and overestimation (for the absolute value on the left-hand side). With probability at least $1-\delta/2$, for all $f_\epsilon \in \mathcal{F}_\epsilon$, $g_\epsilon \in \mathcal{G}_\epsilon$ and $t \ge 0$,

$$\underbrace{\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f_\epsilon,g_\epsilon)\epsilon_s^h(f_\epsilon)}_{A}\leq \sum_{s=1}^{t}\sum_{h=1}^{H}\frac{\Delta_s^h(f_\epsilon,g_\epsilon)^2}{8}+\ln(4M_1M_2/\delta). \tag{18.4}$$

In the following, for each $f \in \mathcal{F}$, we choose $f_\epsilon \in \mathcal{F}_\epsilon$ so that $\|f-f_\epsilon\|_\infty \leq \epsilon$. Similarly, for each $g \in \mathcal{G}$, we choose $g_\epsilon \in \mathcal{G}_\epsilon$ so that $\|g-g_\epsilon\|_\infty \leq \epsilon$. Then

$$\begin{aligned}
\left|\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f,g)\epsilon_s^h(f)\right|
&\leq \left|\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f,g_\epsilon)\epsilon_s^h(f_\epsilon)\right|+2\epsilon\sum_{s=1}^{t}\sum_{h=1}^{H}|\Delta_s^h(f,g)|\\
&\leq \left|\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f,g_\epsilon)\epsilon_s^h(f_\epsilon)\right|+4H\epsilon t.
\end{aligned}$$

The first inequality used $|\epsilon_s^h(f)-\epsilon_s^h(f_\epsilon)|\leq 2\epsilon$. The second inequality used the $\epsilon$-covering property $|\Delta_s^h(f,g)-\Delta_s^h(f,g_\epsilon)|\leq 2\epsilon$, $|\epsilon_s^h(f_\epsilon)|\leq 1$, and $|\Delta_s^h(f,g)|\leq 1$. We also have

$$\begin{aligned}
A &\leq \frac{1}{8}\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f_\epsilon,g_\epsilon)^2+\ln(4M_1M_2/\delta)\\
&\leq \frac{1}{8}\sum_{s=1}^{t}\sum_{h=1}^{H}\bigl(\Delta_s^h(f,g)+2\epsilon\bigr)^2+\ln(4M_1M_2/\delta)\\
&\leq \frac{1}{4}\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f,g)^2+\epsilon^2Ht+\ln(4M_1M_2/\delta).
\end{aligned}$$

The first inequality used (18.4). The second inequality used the $\epsilon$-covering property $|\Delta_s^h(f,g)-\Delta_s^h(f,g_\epsilon)|\leq 2\epsilon$. The last inequality used standard algebra inequalities $|a+2\epsilon|^2/8\leq (a^2/4)+\epsilon^2$ to simplify the terms.

That is, we have shown that with probability at least $1-\delta/2$, for all $f\in\mathcal{F}$ and $g\in\mathcal{G}$ and $t\geq 0$,

$$\left|\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f,g)\epsilon_s^h(f)\right|\leq \frac{1}{4}\sum_{s=1}^{t}\sum_{h=1}^{H}\Delta_s^h(f,g)^2+\epsilon tH(4+\epsilon)+\ln(4M_1M_2/\delta). \tag{18.5}$$

Similarly, with probability at least $1-\delta/2$, for all $f\in\mathcal{F}$ and $t\geq 0$,