
引理 6.1.4 的证明。注意，微积分基本定理、假设 $\mathscr{G} \in C^{1}(\mathbb{R}^{9}, \mathbb{R}^{9})$ 以及 (6.10) 确保了对于所有 $t \in (0, \infty)$，都有 $\Theta \in C^{1}([0, \infty), \mathbb{R}^{9})$ 且

$$\dot{\Theta}_{t} = \mathscr{G}(\Theta_{t}).\tag{6.13}$$

将此与假设 $\mathscr{G} \in C^{1}(\mathbb{R}^{9}, \mathbb{R}^{9})$ 以及链式法则相结合，确保了对于所有 $t \in (0, \infty)$，都有 $\Theta \in C^{2}([0, \infty), \mathbb{R}^{9})$ 且

$$\ddot{\Theta}_{t} = \mathscr{G}^{\prime}(\Theta_{t})\dot{\Theta}_{t} = \mathscr{G}^{\prime}(\Theta_{t})\mathscr{G}(\Theta_{t}).\tag{6.14}$$

因此，定理 6.1.3 和 (6.13) 意味着

$$\begin{aligned} \Theta_{T+\gamma} &= \Theta_{T}+\gamma\dot{\Theta}_{T}+\int_{0}^{1}(1-r)\gamma^{2}\ddot{\Theta}_{T+r\gamma}\mathrm{d}r \\ &= \Theta_{T}+\gamma\mathscr{G}(\Theta_{T})+\gamma^{2}\int_{0}^{1}(1-r)\mathscr{G}^{\prime}(\Theta_{T+r\gamma})\mathscr{G}(\Theta_{T+r\gamma})\mathrm{d}r. \end{aligned}\tag{6.15}$$

这以及 (6.10) 表明

$$\begin{aligned} &\left\|\Theta_{T+\gamma}-\theta\right\|_{2} \\ &=\left\|\Theta_{T}+\gamma\mathscr{G}(\Theta_{T})+\gamma^{2}\int_{0}^{1}(1-r)\mathscr{G}^{\prime}(\Theta_{T+r\gamma})\mathscr{G}(\Theta_{T+r\gamma})\mathrm{d}r-\left(\Theta_{T}+\gamma\mathscr{G}(\Theta_{T})\right)\right\|_{2} \\ &\leq \gamma^{2}\int_{0}^{1}(1-r)\|\mathscr{G}^{\prime}(\Theta_{T+r\gamma})\mathscr{G}(\Theta_{T+r\gamma})\|_{2}\mathrm{d}r \\ &\leq c^{2}\gamma^{2}\int_{0}^{1} r\mathrm{d}r = \frac{c^{2}\gamma^{2}}{2} \leq c^{2}\gamma^{2}. \end{aligned}\tag{6.16}$$

引理 6.1.4 的证明到此结束。

□

**推论 6.1.5** （**广义常微分方程**中欧拉方法的局部误差）。设 $\mathfrak{d} \in \mathbb{N}$，$T, \gamma, c \in [0, \infty)$，$\mathscr{L} \in C^{2}(\mathbb{R}^{9}, \mathbb{R})$，$\Theta \in C([0, \infty), \mathbb{R}^{9})$，$\theta \in \mathbb{R}^{9}$，*对于所有* $x, y \in \mathbb{R}^{9}$，$t \in [0, \infty)$，*满足*

$$\Theta_{t} = \Theta_{0}-\int_{0}^{t}(\nabla\mathscr{L})(\Theta_{s})\mathrm{d}s, \quad \theta = \Theta_{T}-\gamma(\nabla\mathscr{L})(\Theta_{T}),\tag{6.17}$$

$$\| (\nabla\mathscr{L})(x)\|_{2} \leq c, \quad \text{以及} \quad \|\text{Hess}\, \mathscr{L}(x) y\|_{2} \leq c\|y\|_{2}\tag{6.18}$$

（参见定义 3.3.4）。*则*

$$\|\Theta_{T+\gamma}-\theta\|_{2} \leq c^{2}\gamma^{2}.\tag{6.19}$$

*推论 6.1.5 的证明。* 在整个证明过程中，设 $\mathcal{G}: \mathbb{R}^\mathfrak{d} \to \mathbb{R}^\mathfrak{d}$ 满足对于所有 $\theta \in \mathbb{R}^\mathfrak{d}$，有

$$\mathcal{G}(\theta) = - (\nabla\mathcal{L})(\theta)。(6.20)$$

注意，对于所有 $t \in [0, \infty)$ 有 $\Theta_t = \Theta_0 + \int_0^t \mathcal{G}(\Theta_s) \, \mathrm{d}s$，以及 $\theta = \Theta_T + \gamma \mathcal{G}(\Theta_T)$，对于所有 $x \in \mathbb{R}^\mathfrak{d}$ 有 $\|\mathcal{G}(x)\|_2 \leq c$，对于所有 $x, y \in \mathbb{R}^\mathfrak{d}$ 有 $\|\mathcal{G}'(x) y\|_2 \leq c \|\mathcal{G}(y)\|_2$，以及引理 6.1.4 意味着 $\|\Theta_{T+\gamma} - \theta\|_2 \leq c^2 \gamma^2$。推论 6.1.5 的证明到此结束。

## 6.1.3 GD 优化的李雅普诺夫型稳定性

第 5 章 5.6.2 节中的推论 5.6.3 和 5.6.3 节中的推论 5.6.5，特别是说明了如何利用李雅普诺夫型函数来建立 GFBs 的收敛性质。粗略地说，下面两个结果，命题 6.1.6 和推论 6.1.7，分别是推论 5.6.3 和推论 5.6.5 的离散时间对应物。

**命题 6.1.6** （*离散时间动态系统的李雅普诺夫型稳定性*）。设 $\mathfrak{n} \in \mathbb{N}$，$\xi \in \mathbb{R}^\mathfrak{d}$，$c \in (0, \infty)$，$(\gamma_n)_{n \in \mathbb{N}} \subset [0, c]$，设 $V\colon \mathbb{R}^\mathfrak{d} \to \mathbb{R}$，$\Phi\colon \mathbb{R}^\mathfrak{d} \times [0, \infty) \to \mathbb{R}^\mathfrak{d}$，以及 $\varepsilon\colon [0, c] \to [0, \infty)$ 满足对于所有 $\theta \in \mathbb{R}^\mathfrak{d}$，$t \in [0, c]$，有

$$V(\Phi(\theta, t)) \leq \varepsilon(t) V(\theta),$$ (6.21)

并且设 $\Theta\colon \mathbb{N}_0 \to \mathbb{R}^\mathfrak{d}$ 满足对于所有 $n \in \mathbb{N}$，有

$$\Theta_0 = \xi \quad \text{且} \quad \Theta_n = \Phi(\Theta_{n-1}, \gamma_n)。(6.22)$$

则对于所有 $n \in \mathbb{N}_0$，有

$$V(\Theta_n) \leq \biggl[\prod_{k=1}^{n} \varepsilon(\gamma_k)\biggr] V(\xi)。(6.23)$$

*命题 6.1.6 的证明。* 我们对 $n \in \mathbb{N}_0$ 进行归纳证明 (6.23)。对于基始情况 $n=0$，注意假设 $\Theta_0 = \xi$ 确保了 $V(\Theta_0) = V(\xi)$。这建立了基始情况 $n=0$ 下的 (6.23)。在归纳步骤中，观察到 (6.22) 和 (6.21) 确保了对于所有满足 $V(\Theta_n) \leq (\prod_{k=1}^{n} \varepsilon(\gamma_k)) V(\xi)$ 的 $n \in \mathbb{N}_0$，有

$$\begin{align*} V(\Theta_{n+1}) &= V(\Phi(\Theta_n, \gamma_{n+1})) \leq \varepsilon(\gamma_{n+1}) V(\Theta_n) \\ &\leq \varepsilon(\gamma_{n+1}) \biggl[\prod_{k=1}^{n} \varepsilon(\gamma_k)\biggr] V(\xi) = \biggl[\prod_{k=1}^{n+1} \varepsilon(\gamma_k)\biggr] V(\xi). \end{align*}$$ (6.24)

因此，归纳法建立了 (6.23)。命题 6.1.6 的证明到此结束。

**推论 6.1.7** （关于 GD 优化方法中二次李雅普诺夫型函数）。设 $\mathfrak{d} \in \mathbb{N}$，$\vartheta, \xi \in \mathbb{R}^{\mathfrak{d}}$，$c \in (0, \infty)$，$(\gamma_{n})_{n \in \mathbb{N}} \subseteq [0, c]$，$\mathscr{L} \in C^{1}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$，设 $\|\cdot\| : \mathbb{R}^{\mathfrak{d}} \rightarrow [0, \infty)$ 是一个范数，设 $\varepsilon : [0, c] \rightarrow [0, \infty)$ 满足对于所有 $\theta \in \mathbb{R}^{\mathfrak{d}}$，$t \in [0, c]$，有

$$\|\theta - t(\nabla \mathscr{L})(\theta) - \vartheta\|^{2} \leq \varepsilon(t)\|\theta - \vartheta\|^{2}, \quad(6.25)$$

并且设 $\Theta: \mathbb{N}_{0} \rightarrow \mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $n \in \mathbb{N}$，有

$$\Theta_{0} = \xi \quad\quad\text{且}\quad\quad\Theta_{n} = \Theta_{n - 1} - \gamma_{n}(\nabla \mathscr{L})(\Theta_{n - 1}). \quad(6.26)$$

则对于所有 $n \in \mathbb{N}_{0}$，有

$$\|\Theta_{n} - \vartheta\| \leq \bigg[\prod_{k = 1}^{n}\varepsilon(\gamma_{k})\bigg]^{1/2}\|\xi - \vartheta\|. \quad(6.27)$$

*推论 6.1.7 的证明。* 在整个证明过程中，设 $V : \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ 和 $\Phi : \mathbb{R}^{\mathfrak{d}} \times [0, \infty) \rightarrow \mathbb{R}^{\mathfrak{d}}$ 满足对于所有 $\theta \in \mathbb{R}^{\mathfrak{d}}$，$t \in [0, \infty)$，有

$$V(\theta) = \|\theta - \vartheta\|^{2}\quad\quad\text{且}\quad\quad\Phi(\theta, t) = \theta - t(\nabla \mathscr{L})(\theta). \quad(6.28)$$

观察到命题 6.1.6（在命题 6.1.6 的记法中应用 $V \curvearrowright V$，$\Phi \curvearrowright \Phi$）和 (6.28) 意味着对于所有 $n \in \mathbb{N}_{0}$，有

$$\|\Theta_{n} - \vartheta\|^{2} = V(\Theta_{n}) \leq \bigg[\prod_{k = 1}^{n}\varepsilon(\gamma_{k})\bigg]V(\xi) = \bigg[\prod_{k = 1}^{n}\varepsilon(\gamma_{k})\bigg]\|\xi - \vartheta\|^{2}. \quad(6.29)$$

这就建立了 (6.27)。推论 6.1.7 的证明到此结束。

特别是，推论 6.1.7 说明了 (6.25) 中的单步李雅普诺夫稳定性假设可以为我们提供与 GD 优化方法相关的近似误差的合适估计；参见上文 (6.27)。下一个结果，即下文引理 6.1.8，现在为我们提供了确保 (6.25) 中的单步李雅普诺夫稳定性条件成立的充分条件，从而使我们能够应用上述推论 6.1.7 来获得与 GD 优化方法相关的近似误差估计。引理 6.1.8 使用了上述推论 5.7.5 中 (5.189) 的增长条件和强制型条件。与引理 6.1.8 类似的结果可以在 [103, Remark 2.1] 和 [221, Lemma 2.1] 中找到。我们将在下文 6.1.4 节中关于 GD 优化方法的误差分析中应用引理 6.1.8 的陈述。

**引理 6.1.8** （单步李雅普诺夫型稳定性条件的充分条件）。设 $\mathfrak{d} \in \mathbb{N}$，设 $\langle\cdot, \cdot\rangle : \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ 是一个内积，设 $\|\cdot\| : \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ 满足对于所有 $v \in \mathbb{R}^{\mathfrak{d}}$，有 $\|v\| = \sqrt{\langle v, v\rangle}$，且设 $c, L \in (0, \infty)$，$r \in (0, \infty]$，$\vartheta \in \mathbb{R}^{\mathfrak{d}}$，$\mathbb{B} = \{w \in \mathbb{R}^{\mathfrak{d}} : \|w - \vartheta\| \leq r\}$，$\mathscr{L} \in C^{1}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ 满足对于所有 $\theta \in \mathbb{B}$，有

$$\langle\theta - \vartheta, (\nabla \mathscr{L})(\theta)\rangle \geq c\|\theta - \vartheta\|^{2}\quad\quad\text{且}\quad\quad\|(\nabla \mathscr{L})(\theta)\| \leq L\|\theta - \vartheta\|. \quad(6.30)$$

则
