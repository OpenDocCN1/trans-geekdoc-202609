
## 9.12.2 梯度下降过程的局部收敛抽象结果

**命题 9.12.4.** 设 $\boldsymbol{d} \in \mathbb{N}$，$\mathbf{c} \in \mathbb{N}$，$\varepsilon, L, \mathfrak{C} \in (0, \infty)$，$\alpha \in (0, 1)$，$\gamma \in (0, L^{-1}]$，$\vartheta \in \mathbb{R}^\boldsymbol{d}$，设 $\mathbb{B} \subset \mathbb{R}^\boldsymbol{d}$ 满足 $\mathbb{B} = \{\theta \in \mathbb{R}^\boldsymbol{d} : \|\theta - \vartheta\|_2 < \varepsilon\}$，设 $\mathscr{L} \in C(\mathbb{R}^\boldsymbol{d}, \mathbb{R})$ 满足 $\mathscr{L}|_\mathbb{B} \in C^1(\mathbb{B}, \mathbb{R})$，设 $\mathfrak{G} : \mathbb{R}^\boldsymbol{d} \to \mathbb{R}^\boldsymbol{d}$ 满足对于所有 $\theta \in \mathbb{B}$ 都有 $\mathfrak{G}(\theta) = (\nabla \mathscr{L})(\theta)$，假设 $\mathfrak{G}(\vartheta) = 0$，假设对于所有 $\theta_1, \theta_2 \in \mathbb{B}$ 都有

$$\|\mathfrak{G}(\theta_1) - \mathfrak{G}(\theta_2)\|_2 \leq L \|\theta_1 - \theta_2\|_2,\tag{9.216}$$

设 $\Theta : \mathbb{N}_0 \to \mathbb{R}^\boldsymbol{d}$ 满足对于所有 $n \in \mathbb{N}_0$ 都有 $\Theta_{n+1} = \Theta_n - \gamma \mathfrak{G}(\Theta_n)$，并假设对于所有 $\theta \in \mathbb{B}$ 都有

$$\begin{aligned}
\left|\mathscr{L}(\theta) - \mathscr{L}(\vartheta)\right|^\alpha &\leq \mathbf{c} \|\mathfrak{G}(\theta)\|_2, \quad \mathbf{c} = \left|\mathscr{L}(\Theta_0) - \mathscr{L}(\vartheta)\right|, \quad 2 \mathfrak{C} (1-\alpha)^{-1} \mathbf{c}^{1-\alpha} + \|\Theta_0 - \vartheta\|_2 < \frac{\varepsilon}{\gamma L + 1},
\end{aligned}\tag{9.217}$$

且 $\inf_{n \in \{m \in \mathbb{N}_0 : \forall k \in \mathbb{N}_0 \cap [0, m] : \Theta_k \in \mathbb{B}\}} \mathscr{L}(\Theta_n) \geq \mathscr{L}(\vartheta)$（参见定义 3.9.4）。则存在 $\psi \in \mathscr{L}^{-1}\left(\{\mathscr{L}(\vartheta)\}\right) \cap \mathfrak{G}^{-1}\left(\{0\}\right) \cap \mathbb{B}$ 使得

- (i) 对于所有 $n \in \mathbb{N}_0$，有 $\Theta_n \in \mathbb{B}$，
- (ii) 对于所有 $n \in \mathbb{N}_0$，有 $0 \leq \mathscr{L}(\Theta_n) - \mathscr{L}(\psi) \leq 2 \mathfrak{C} \mathbf{c}^2 \mathfrak{C}^{-1}_{\{0\}}(\mathbf{c}) + \mathbf{c}^{2\alpha} n^\gamma + 2 \mathfrak{C} \mathbf{c}^{-1}$，且
- (iii) 对于所有 $n \in \mathbb{N}_0$，有

$$\begin{aligned}
\|\Theta_n - \psi\|_2 &\leq \sum_{k=n}^{\infty} \|\Theta_{k+1} - \Theta_k\|_2 \leq 2 \mathfrak{C} (1-\alpha)^{-1} \left[\mathscr{L}(\Theta_n) - \mathscr{L}(\psi)\right]^{1-\alpha} \\
&\leq 2^{2-\alpha} \mathfrak{C}^{3-2\alpha} \mathfrak{C}^{-2\alpha}_{\{0\}} (1-\alpha)^{-1} \mathfrak{C}^{-1}_{\{0\}}(\mathbf{c}) + \mathbf{c}^{2\alpha} n^\gamma + 2 \mathfrak{C} \mathbf{c}^{-1}\left[\mathbf{c}^{2\alpha} n^\gamma\right]^{\alpha - 1}.
\end{aligned}\tag{9.218}$$

**命题 9.12.4 的证明.** 在整个证明过程中，设 $T \in \mathbb{N}_0 \cup \{\infty\}$ 满足

$$T = \inf\left(\left\{n \in \mathbb{N}_0 : \Theta_n \notin \mathbb{B}\right\} \cup \{\infty\}\right),\tag{9.219}$$

设 $\mathtt{L} : \mathbb{N}_0 \to \mathbb{R}$ 满足对于所有 $n \in \mathbb{N}_0$ 都有 $\mathtt{L}(n) = \mathscr{L}(\Theta_n) - \mathscr{L}(\vartheta)$，并设 $\tau \in \mathbb{N}_0 \cup \{\infty\}$ 满足

$$\tau = \inf\left(\left\{n \in \mathbb{N}_0 \cap [0, T) : \mathtt{L}(n) = 0\right\} \cup \{T\}\right).\tag{9.220}$$

注意到假设 $\mathfrak{G}(\vartheta) = 0$ 意味着对于所有 $\theta \in \mathbb{B}$ 都有

$$\gamma \|\mathfrak{G}(\theta)\|_2 = \gamma \|\mathfrak{G}(\theta) - \mathfrak{G}(\vartheta)\|_2 \leq \gamma L \|\theta - \vartheta\|_2.\tag{9.221}$$

结合 $\|\Theta_0 - \vartheta\|_2 < \varepsilon$ 以及事实：

$$\begin{aligned}
\|\Theta_1 - \vartheta\|_2 &\leq \|\Theta_1 - \Theta_0\|_2 + \|\Theta_0 - \vartheta\|_2 = \gamma \|\mathfrak{G}(\Theta_0)\|_2 + \|\Theta_0 - \vartheta\|_2 \\
&\leq \gamma (L + 1) \|\Theta_0 - \vartheta\|_2 < \varepsilon
\end{aligned}\tag{9.222}$$

可知 $T \ge 2$。接下来注意到假设：

$$\inf_{n \in \{m \in \mathbb{N}_0: \ \forall k \in \mathbb{N}_0 \cap [0,m] \: \Theta_k \in \mathbb{B}\}} \mathcal{L} (\Theta_n) \ge \mathcal{L}(\vartheta)$$ (9.223)

表明对于所有 $n \in \mathbb{N}_0 \cap [0, T)$ 都有

$$\mathbb{L} (n) \ge 0.$$ (9.224)

此外，注意到事实：$\mathbb{B} \subseteq \mathbb{R}^d$ 是开凸集，结合推论 9.12.3 和 (9.217) 表明对于所有 $n \in \mathbb{N}_0 \cap [0, T-1)$ 都有

$\begin{align*}\mathbb{L}(n+1) - \mathbb{L}(n) &= \mathcal{L}(\Theta_{n+1}) - \mathcal{L}(\Theta_n) \le -\frac{\gamma}{2}\|\mathcal{G}(\Theta_n)\|_2^2 = -\frac{1}{2}\|\mathcal{G}(\Theta_n)\|_2\|\gamma \mathcal{G}(\Theta_n)\|_2 \\
&= -\frac{1}{2}\|\mathcal{G}(\Theta_n)\|_2\|\Theta_{n+1} - \Theta_n\|_2 \le -(2\mathfrak{C})^{-1}[\mathcal{L}(\Theta_n) - \mathcal{L}(\vartheta)]^{\alpha}\|\Theta_{n+1} - \Theta_n\|_2 \\
&= -(2\mathfrak{C})^{-1}[\mathbb{L}(n)]^{\alpha}\|\Theta_{n+1} - \Theta_n\|_2 \le 0.\end{align*}$ (9.225)

因此，我们得到映射

$$\mathbb{N}_0 \cap [0, T) \ni n \to \mathbb{L} (n) \in [0, \infty)$$ (9.226)

是非递增的。将此与 (9.220) 结合，确保对于所有 $n \in \mathbb{N}_0 \cap [\tau, T)$ 都有

$$\mathbb{L}(n) = 0.$$ (9.227)

结合上述结果与 (9.225) 表明对于所有 $n \in \mathbb{N}_0 \cap [\tau, T-1)$ 都有

$$0 = \mathbb{L}(n+1) - \mathbb{L}(n) \le -\frac{\gamma}{2}\|\mathcal{G}(\Theta_n)\|_2^2 \le 0.$$ (9.228)

由于 $\gamma > 0$，因此对于所有 $n \in \mathbb{N}_0 \cap [\tau, T-1)$ 都有 $\mathcal{G}(\Theta_n) = 0$。从而，我们得到对于所有 $n \in \mathbb{N}_0 \cap [\tau, T)$ 都有

$$\Theta_n = \Theta_\tau.$$ (9.229)

此外，注意到 (9.220) 和 (9.225) 确保对于所有 $n \in \mathbb{N}_0 \cap [0, \tau) \cap [0, T-1)$ 都有

$\begin{align*}\|\Theta_{n+1} - \Theta_n\|_2 &\le \frac{2\mathfrak{C}(\mathbb{L}(n) - \mathbb{L}(n+1))}{[\mathbb{L}(n)]^{\alpha}} = 2\mathfrak{C}\int_{\mathbb{L}(n+1)}^{\mathbb{L}(n)} [\mathbb{L}(n)]^{-\alpha} \, \mathrm{d}u \\
&\le 2\mathfrak{C}\int_{\mathbb{L}(n+1)}^{\mathbb{L}(n)} u^{-\alpha} \, \mathrm{d}u = \frac{2\mathfrak{C}([\mathbb{L}(n)]^{1-\alpha} - [\mathbb{L}(n+1)]^{1-\alpha})}{1-\alpha}.\end{align*}$ (9.230)

结合此结果与 (9.229)，对于所有 $n \in \mathbb{N}_0 \cap [0, T-1)$ 有

$$\|\Theta_{n+1} - \Theta_n\|_2 \le \frac{2\mathfrak{C}([\mathbb{L}(n)]^{1-\alpha} - [\mathbb{L}(n+1)]^{1-\alpha})}{1-\alpha}.$$ (9.231)

将此与三角不等式结合，证明了对于所有满足 $m \leq n$ 的 $m, n \in \mathbb{N}_0 \cap \, (0, T)$ 都有

$$\| \Theta _ {n} - \Theta _ {m} \| _ {2} \leq \sum _ {k = m} ^ {n - 1} \| \Theta _ {k + 1} - \Theta _ {k} \| _ {2} \leq \frac {2 \mathfrak { C } \left( \left[ \mathbb { L } ( n ) \right] ^ { 1 - \alpha } - \left[ \mathbb { L } ( m ) \right] ^ { 1 - \alpha } \right) } {1 - \alpha} \leq \frac {2 \mathfrak { C } \left[ \mathbb { L } ( n ) \right] ^ { 1 - \alpha } } {1 - \alpha} .$$

结合此结果与 (9.217)，表明对于所有 $n \in \mathbb{N}_0 \cap \, (0, T)$ 都有

$$\| \Theta _ {n} - \Theta _ {0} \| _ {2} \leq \frac {2 \mathfrak { C } \left[ \mathbb { L } ( 0 ) \right] ^ { 1 - \alpha } } {1 - \alpha} = \frac {2 \mathfrak { C } \left( \mathcal { L } \left( \Theta _ {0} \right) - \mathcal { L } \left( \vartheta \right) \right) ^ { 1 - \alpha } } {1 - \alpha} = 2 \mathfrak { C } \left( 1 - \alpha \right) ^ { - 1 } \mathbf { c } ^ { 1 - \alpha } .$$

将此与 (9.221)、(9.217) 以及三角不等式结合，推导出对于所有 $n \in \mathbb{N}_0 \cap \, (0, T)$ 都有

$$\begin{aligned} \| \Theta _ {n + 1} - \vartheta \| _ {2} \leq & \| \Theta _ {n + 1} - \Theta _ {n} \| _ {2} + \| \Theta _ {n} - \vartheta \| _ {2} = \| \gamma \mathcal { G } \left( \Theta _ {n} \right) \| _ {2} + \| \Theta _ {n} - \vartheta \| _ {2} \\ \leq & \left( \gamma L + 1 \right) \| \Theta _ {n} - \vartheta \| _ {2} \leq \left( \gamma L + 1 \right) \left( \| \Theta _ {n} - \Theta _ {0} \| _ {2} + \| \Theta _ {0} - \vartheta \| _ {2} \right) \\ \leq & \left( \gamma L + 1 \right) \left( 2 \mathfrak { C } \left( 1 - \alpha \right) ^ { - 1 } \mathbf { c } ^ { 1 - \alpha } + \| \Theta _ {0} - \vartheta \| _ {2} \right) < \varepsilon . \end{aligned}$$

因此，我们得到

$$T = \infty .$$

结合此结果与 (9.217)、(9.231) 以及 (9.226)，证明了

$$\sum _ {k = 0} ^ {\infty} \| \Theta _ {k + 1} - \Theta _ {k} \| _ {2} = \lim _ {n \rightarrow \infty} \left[ \sum _ {k = 0} ^ {n} \| \Theta _ {k + 1} - \Theta _ {k} \| _ {2} \right] \leq \frac {2 \mathfrak { C } \left[ \mathbb { L } ( 0 ) \right] ^ { 1 - \alpha } } {1 - \alpha } = \frac {2 \mathfrak { C } \mathbf { c } ^ { 1 - \alpha } } {1 - \alpha } < \varepsilon < \infty .$$

因此，我们得到存在 $\vartheta^* \in \mathbb{R}^{d}$ 满足

$$\limsup _ {n \rightarrow \infty} \| \Theta _ {n} - \vartheta^* \| _ {2} = 0 .$$

注意到 (9.234)、(9.235) 和 (9.237) 确保

$$\| \vartheta^* - \vartheta \| _ {2} \leq \left( \gamma L + 1 \right) \left( 2 \mathfrak { C } \left( 1 - \alpha \right) ^ { - 1 } \mathbf { c } ^ { 1 - \alpha } + \| \Theta _ {0} - \vartheta \| _ {2} \right) < \varepsilon .$$

因此，我们得到

$$\vartheta^* \in \mathbb{B} .$$

接下来注意到 (9.225)、(9.217) 以及对于所有 $n \in \mathbb{N}_0$ 都有 $\| \mathbb{L}(n) \leq \| \mathbb{L}(0) = \mathbf{c}$ 这一事实，确保了对于所有 $n \in \mathbb{N}_0 \cap \, [0, \tau)$ 都有

$$\| \mathbb { L } ( n + 1 ) - \mathbb { L } ( n ) \| \leq - \frac {\gamma} {2} \| \mathcal { G } \left( \Theta _ {n} \right) \| _ {2} ^ {2} \leq - \frac {\gamma} {2 \varepsilon ^ { 2 - 2 \alpha } } \| \mathbb { L } ( n ) \| ^ {2} .$$

