

*命题 9.11.4 的证明。* 注意到 (9.166) 意味着 $[0, \infty) \ni t \mapsto \mathscr{L}(\Theta_t) \in \mathbb{R}$ 是非递增的。因此，我们得到存在 $\mathbf{m} \in [-\infty, \infty)$ 满足

$$
\mathbf{m}=\operatorname*{lim sup}_{t \rightarrow \infty} \mathscr{L}\left(\Theta_t\right)=\operatorname*{lim inf}_{t \rightarrow \infty} \mathscr{L}\left(\Theta_t\right)=\operatorname*{inf}_{t \in[0, \infty)} \mathscr{L}(\Theta_t) . \quad (9.168)
$$

此外，注意到假设 $\lim \inf _{t \rightarrow \infty}\left\|\Theta_t\right\|_2<\infty$ 表明存在 $\vartheta \in \mathbb{R}^9$ 和 $\delta=\left(\delta_n\right)_{n \in \mathbb{N}}: \mathbb{N} \rightarrow[0, \infty)$，使得

$$
\lim \inf _{n \rightarrow \infty} \delta_n=\infty \quad \text { 且 } \quad \lim _{n \rightarrow \infty}\left\|\Theta_{\delta_n}-\vartheta\right\|_2=0 . \quad (9.169)
$$

注意到 (9.168)、(9.169) 以及 $\mathscr{L}$ 是连续的事实确保了

$$
\mathscr{L}(\vartheta)=\mathbf{m} \in \mathbb{R} \quad \text { 且 } \quad \forall t \in[0, \infty): \mathscr{L}\left(\Theta_t\right) \geq \mathscr{L}(\vartheta) . \quad (9.170)
$$

接下来，令 $\varepsilon, \mathbf{c} \in(0, \infty), \alpha \in(0,1)$ 满足对于所有满足 $\|\theta-\vartheta\|_2<\varepsilon$ 的 $\theta \in \mathbb{R}^9$，有

$$
\left|\mathscr{L}(\theta)-\mathscr{L}(\vartheta)\right|^\alpha \leq \mathbf{c}\left\|\mathscr{G}(\theta)\right\|_2 . \quad (9.171)
$$

注意到 (9.169) 和 $\mathscr{L}$ 是连续的事实表明，存在 $n \in \mathbb{N}$ 和 $\mathbf{c} \in[0,1]$ 满足

$$
\mathbf{c}=\left|\mathscr{L}\left(\Theta_{\delta_n}\right)-\mathscr{L}(\vartheta)\right| \quad \text { 且 } \quad \mathbf{c}\left(1-\alpha\right)^{-1} \mathbf{c}^{1-\alpha}+\left\|\Theta_{\delta_n}-\vartheta\right\|_2<\varepsilon . \quad (9.172)
$$

接下来，令 $\Phi: [0, \infty) \rightarrow \mathbb{R}^9$ 满足对于所有 $t \in[0, \infty)$，有

$$
\Phi_t=\Theta_{\delta_n+t} . \quad (9.173)
$$

注意到 (9.166)、(9.170) 和 (9.173) 建立了对于所有 $t \in[0, \infty)$，成立以下等式

$$
\begin{gathered}
\mathscr{L}\left(\Phi_t\right)=\mathscr{L}\left(\Phi_0\right)-\int_0^t\left\|\mathscr{G}\left(\Phi_s\right)\right\|_2^2 \mathrm{~d} s, \quad \Phi_t=\Phi_0-\int_0^t \mathscr{G}\left(\Phi_s\right) \mathrm{d} s, \\
\text { 且 } \mathscr{L}\left(\Phi_t\right) \geq \mathscr{L}(\vartheta) .
\end{gathered} \quad (9.174)
$$

结合 (9.171)、(9.172)、(9.173) 以及推论 9.11.3（在推论 9.11.3 的记号中应用 $\Theta \wedge \Phi$），可证得存在 $\psi \in \mathbb{R}^9$ 满足对于所有 $t \in[0, \infty)$，有

$$
0 \leq \mathscr{L}\left(\Phi_t\right)-\mathscr{L}(\psi) \leq\left(1+\mathbf{c}^{-2} t\right)^{-1}, \quad \left\|\Phi_t-\psi\right\|_2 \leq \mathbf{c}(1-\alpha)^{-1}\left(1+\mathbf{c}^{-2} t\right)^{\alpha-1}, \quad (9.175)
$$

且 $\mathscr{L}(\psi)=\mathscr{L}(\vartheta)$。注意到 (9.173) 和 (9.175) 表明，对于所有 $t \in[0, \infty)$，$0 \leq$ $\mathscr{L}\left(\Theta_{\delta_n+t}\right)-\mathscr{L}(\psi) \leq\left(1+\mathbf{c}^{-2} t\right)^{-1}$ 且 $\left\|\Theta_{\delta_n+t}-\psi\right\|_2 \leq \mathbf{c}(1-\alpha)^{-1}\left(1+\mathbf{c}^{-2} t\right)^{\alpha-1}$。因此，我们得到对于所有 $\tau \in\left[\delta_n, \infty\right), t \in[\tau, \infty)$，有

$$
\begin{gathered}
0 \leq \mathscr{L}\left(\Theta_t\right)-\mathscr{L}(\psi) \leq\left(1+\mathbf{c}^{-2}\left(t-\delta_n\right)\right)^{-1}=\left(1+\mathbf{c}^{-2}(t-\tau)+\mathbf{c}^{-2}\left(\tau-\delta_n\right)\right)^{-1} \\
\leq\left(1+\mathbf{c}^{-2}(t-\tau)\right)^{-1}
\end{gathered} \quad (9.176)
$$

以及

$$
\begin{aligned}
\left\|\Theta_{t} - \psi\right\|_{2} &\leq \mathfrak{C}(1 - \alpha)^{-1}(1 + \mathfrak{C}^{-2}(t - \delta_{n}))^{\alpha - 1} \\
&= \left[\left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{\alpha - 1}}(1 + \mathfrak{C}^{-2}(t - \delta_{n}))\right]^{\alpha - 1} \\
&= \left[\left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{\alpha - 1}}\left[1 + \mathfrak{C}^{-2}(\tau - \delta_{n})\right] + \left[\left(\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{1 - \alpha}}\mathfrak{C}^{2}\right]^{-1}(t - \tau)\right]^{\alpha - 1} .
\end{aligned} \quad (9.177)
$$

接下来，令 $\mathfrak{C}$ 和 $\tau \in (0, \infty)$ 满足

$$
\mathfrak{C} = \max\{\mathfrak{C}^{2}, \left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{1 - \alpha}}\mathfrak{C}^{2}\} \quad \text{且} \quad \tau = \delta_{n} + \mathfrak{C}^{2}\left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{1 - \alpha}} . \quad (9.178)
$$

注意到 (9.176)、(9.177) 和 (9.178) 表明，对于所有 $t \in [\tau, \infty)$，有

$$
0 \leq \mathcal{L}(\Theta_{t}) - \mathcal{L}(\psi) \leq (1 + \mathfrak{C}^{-2}(t - \tau))^{-1} \leq (1 + \mathfrak{C}^{-1}(t - \tau))^{-1} \quad (9.179)
$$

以及

$$
\begin{aligned}
\left\|\Theta_{t} - \psi\right\|_{2} &\leq \left[\left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{\alpha - 1}}\left[1 + \mathfrak{C}^{-2}(\tau - \delta_{n})\right] + \mathfrak{C}^{-1}(t - \tau)\right]^{\alpha - 1} \\
&= \left[\left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{\alpha - 1}}\left[1 + \left[\mathfrak{C}(1 - \alpha)^{-1}\right]^{\frac{1}{1 - \alpha}}\right] + \mathfrak{C}^{-1}(t - \tau)\right]^{\alpha - 1} \\
&\leq \left[1 + \mathfrak{C}^{-1}(t - \tau)\right]^{\alpha - 1} .
\end{aligned} \quad (9.180)
$$

至此，命题 9.11.4 的证明完毕。

### **推论 9.11.5。**

设 $\varrho \in \mathbb{N}$，$\Theta \in C([0, \infty), \mathbb{R}^{\varrho})$，$\mathcal{L} \in C(\mathbb{R}^{\varrho}, \mathbb{R})$，设 $\mathfrak{G}: \mathbb{R}^{\varrho} \rightarrow \mathbb{R}^{\varrho}$ 是 $\mathcal{B}(\mathbb{R}^{\varrho})/\mathcal{B}(\mathbb{R}^{\varrho})$-可测的，假设对于所有 $\vartheta \in \mathbb{R}^{\varrho}$，存在 $\varepsilon, \mathfrak{C} \in (0, \infty)$，$\alpha \in (0, 1)$，使得对于所有满足 $\|\theta - \vartheta\|_{2} < \varepsilon$ 的 $\theta \in \mathbb{R}^{\varrho}$，有

$$
|\mathcal{L}(\theta) - \mathcal{L}(\vartheta)|^{\alpha} \leq \mathfrak{C}\|\mathfrak{G}(\vartheta)\|_{2}, \quad (9.181)
$$

假设对于所有 $t \in [0, \infty)$，有

$$
\mathcal{L}(\Theta_{t}) = \mathcal{L}(\Theta_{0}) - \int_{0}^{t}\|\mathfrak{G}(\Theta_{s})\|_{2}^{2}\mathrm{d}s \quad \text{且} \quad \Theta_{t} = \Theta_{0} - \int_{0}^{t}\mathfrak{G}(\Theta_{s})\mathrm{d}s, \quad (9.182)
$$

且假设 $\liminf_{t \rightarrow \infty}\|\Theta_{t}\|_{2} < \infty$（参见定义 3.3.4）。则存在 $\vartheta \in \mathbb{R}^{\varrho}$，$\mathfrak{C}$，$\beta \in (0, \infty)$，使得对于所有 $t \in [0, \infty)$，有

$$
\|\Theta_{t} - \vartheta\|_{2} \leq \mathfrak{C}(1 + t)^{-\beta} \quad \text{且} \quad 0 \leq \mathcal{L}(\Theta_{t}) - \mathcal{L}(\vartheta) \leq \mathfrak{C}(1 + t)^{-1} . \quad (9.183)
$$

*推论 9.11.5 的证明。* 注意到命题 9.11.4 表明，存在 $\vartheta \in \mathbb{R}^{\mathfrak{d}}$，$\mathfrak{C}, \tau, \beta \in (0, \infty)$，使得对于所有 $t \in [\tau, \infty)$，有

$$
\|\Theta_{t}-\vartheta\|_{2} \leq\left(1+\mathfrak{C}(t-\tau)\right)^{-\beta}\quad \mathrm{且} \quad 0 \leq \mathcal{L}\left(\Theta_{t}\right)-\mathcal{L}(\vartheta) \leq\left(1+\mathfrak{C}(t-\tau)\right)^{-1}. \quad (9.184)
$$

在下文中，令 $\mathcal{K} \in (0, \infty)$ 满足

$$
\mathcal{K}=\max \left\{1+\tau,\left(1+\tau\right)^{\beta}, \mathfrak{C} \tau^{-1}, \mathfrak{C} \tau^{-\beta},\left(1+\tau\right)^{\beta}\left(\sup _{s \in[0, \tau]}\left\|\Theta_{s}-\vartheta\right\|_{2}\right),(1+\tau)\left(\mathcal{L}\left(\Theta_{0}\right)-\mathcal{L}(\vartheta)\right)\right\}. \quad (9.185)
$$

注意到 (9.184)、(9.185) 以及事实 $[0, \infty) \ni t \mapsto \mathcal{L}\left(\Theta_{t}\right) \in \mathbb{R}$ 是非递增的，证明了对于所有 $t \in[0, \tau]$，有

$$
\|\Theta_{t}-\vartheta\|_{2} \leq \sup _{s \in[0, \tau]}\left\|\Theta_{s}-\vartheta\right\|_{2} \leq \mathcal{K}\left(1+\tau\right)^{-\beta} \leq \mathcal{K}\left(1+t\right)^{-\beta} \quad (9.186)
$$

且

$$
0 \leq \mathcal{L}\left(\Theta_{t}\right)-\mathcal{L}(\vartheta) \leq \mathcal{L}\left(\Theta_{0}\right)-\mathcal{L}(\vartheta) \leq \mathcal{K}\left(1+\tau^{-1}\right) \leq \mathcal{K}\left(1+t^{-1}\right). \quad (9.187)
$$

此外，注意到 (9.184) 和 (9.185) 意味着，对于所有 $t \in[\tau, \infty)$，有

$$
\begin{gathered}
\|\Theta_{t}-\vartheta\|_{2} \leq\left(1+\mathfrak{C}(t-\tau)\right)^{-\beta}=\mathcal{K}\left(\mathfrak{C}^{1 / \beta}+\mathfrak{C}^{1 / \beta} \mathfrak{C}(t-\tau)\right)^{-\beta} \\
\leq \mathcal{K}\left(\mathfrak{C}^{1 / \beta}+t-\tau\right)^{-\beta} \leq \mathcal{K}\left(1+t\right)^{-\beta} .
\end{gathered} \quad (9.188)
$$

而且，注意到 (9.184) 和 (9.185) 表明，对于所有 $t \in[\tau, \infty)$，有

$$
0 \leq \mathcal{L}\left(\Theta_{t}\right)-\mathcal{L}(\vartheta) \leq \mathcal{K}\left(\mathcal{K}+\mathfrak{C} \mathfrak{C}(t-\tau)\right)^{-1} \leq \mathcal{K}\left(\mathcal{K}-\tau+t\right)^{-1} \leq \mathcal{K}\left(1+t^{-1}\right). \quad (9.189)
$$

至此，推论 9.11.5 的证明完毕。 $\square$

### **推论 9.11.6。**

*设* $\mathfrak{d} \in \mathbb{N}$，$\Theta \in C([0, \infty), \mathbb{R}^{\mathfrak{d}})$，$\mathcal{L} \in C^{1}\left(\mathbb{R}^{\mathfrak{d}}, \mathbb{R}\right)$，*假设对于所有* $\vartheta \in \mathbb{R}^{\mathfrak{d}}$ *存在* $\varepsilon, \mathfrak{C} \in (0, \infty)$，$\alpha \in (0, 1)$ *使得对于所有* $\theta \in \mathbb{R}^{\mathfrak{d}}$ *满足* $\|\theta-\vartheta\|_{2} < \varepsilon$ *有*

$$
|\mathcal{L}(\theta)-\mathcal{L}(\vartheta)|^{\alpha} \leq \mathfrak{C}\|\langle\nabla \mathcal{L}\rangle(\theta)\|_{2}, \quad (9.190)
$$

*假设对于所有* $t \in [0, \infty)$ *有*

$$
\Theta_{t}=\Theta_{0}-\int_{0}^{t}(\nabla \mathcal{L})(\Theta_{s}) \mathrm{d} s, \quad (9.191)
$$

*且假设* $\operatorname{lim}\inf_{t \rightarrow \infty}\left\|\Theta_{t}\right\|_{2}<\infty$ *（参见定义 3.3.4）。则存在* $\vartheta \in \mathbb{R}^{\mathfrak{d}}$，$\mathcal{K}, \beta \in(0, \infty)$ *使得对于所有* $t \in[0, \infty)$ *有*

$$
\left\|\Theta_{t}-\vartheta\right\|_{2} \leq \mathcal{K}\left(1+t\right)^{-\beta} , \quad 0 \leq \mathcal{L}\left(\Theta_{t}\right)-\mathcal{L}(\vartheta) \leq \mathcal{K}\left(1+t\right)^{-1}, \text { 且 } \quad(\nabla \mathcal{L})(\vartheta)=0 . \quad (9.192)
$$

