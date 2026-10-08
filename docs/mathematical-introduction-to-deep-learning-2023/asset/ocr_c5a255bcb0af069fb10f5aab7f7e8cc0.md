Proof of Lemma 6.1.4. Note that the fundamental theorem of calculus, the hypothesis that $\mathscr{G} \in C^{1}(\mathbb{R}^{9}, \mathbb{R}^{9})$, and (6.10) assure that for all $t \in (0, \infty)$ it holds that $\Theta \in C^{1}([0, \infty), \mathbb{R}^{9})$ and

$$\dot{\Theta}_{t} = \mathscr{G}(\Theta_{t}).\tag{6.13}$$

Combining this with the hypothesis that $\mathscr{G} \in C^{1}(\mathbb{R}^{9}, \mathbb{R}^{9})$ and the chain rule ensures that for all $t \in (0, \infty)$ it holds that $\Theta \in C^{2}([0, \infty), \mathbb{R}^{9})$ and

$$\ddot{\Theta}_{t} = \mathscr{G}^{\prime}(\Theta_{t})\dot{\Theta}_{t} = \mathscr{G}^{\prime}(\Theta_{t})\mathscr{G}(\Theta_{t}).\tag{6.14}$$

Theorem 6.1.3 and (6.13) therefore imply that

$$\begin{aligned} \Theta_{T+\gamma} &= \Theta_{T}+\gamma\dot{\Theta}_{T}+\int_{0}^{1}(1-r)\gamma^{2}\ddot{\Theta}_{T+r\gamma}\mathrm{d}r \\ &= \Theta_{T}+\gamma\mathscr{G}(\Theta_{T})+\gamma^{2}\int_{0}^{1}(1-r)\mathscr{G}^{\prime}(\Theta_{T+r\gamma})\mathscr{G}(\Theta_{T+r\gamma})\mathrm{d}r. \end{aligned}\tag{6.15}$$

This and (6.10) demonstrate that

$$\begin{aligned} &\left\|\Theta_{T+\gamma}-\theta\right\|_{2} \\ &=\left\|\Theta_{T}+\gamma\mathscr{G}(\Theta_{T})+\gamma^{2}\int_{0}^{1}(1-r)\mathscr{G}^{\prime}(\Theta_{T+r\gamma})\mathscr{G}(\Theta_{T+r\gamma})\mathrm{d}r-\left(\Theta_{T}+\gamma\mathscr{G}(\Theta_{T})\right)\right\|_{2} \\ &\leq \gamma^{2}\int_{0}^{1}(1-r)\|\mathscr{G}^{\prime}(\Theta_{T+r\gamma})\mathscr{G}(\Theta_{T+r\gamma})\|_{2}\mathrm{d}r \\ &\leq c^{2}\gamma^{2}\int_{0}^{1} r\mathrm{d}r = \frac{c^{2}\gamma^{2}}{2} \leq c^{2}\gamma^{2}. \end{aligned}\tag{6.16}$$

The proof of Lemma 6.1.4 is thus complete.

□

**Corollary 6.1.5** (Local error of the Euler method for **GF ODEs**). Let $\mathfrak{d} \in \mathbb{N}$, $T, \gamma, c \in [0, \infty)$, $\mathscr{L} \in C^{2}(\mathbb{R}^{9}, \mathbb{R})$, $\Theta \in C([0, \infty), \mathbb{R}^{9})$, $\theta \in \mathbb{R}^{9}$ *satisfy for all* $x, y \in \mathbb{R}^{9}$, $t \in [0, \infty)$ *that*

$$\Theta_{t} = \Theta_{0}-\int_{0}^{t}(\nabla\mathscr{L})(\Theta_{s})\mathrm{d}s, \quad \theta = \Theta_{T}-\gamma(\nabla\mathscr{L})(\Theta_{T}),\tag{6.17}$$

$$\| (\nabla\mathscr{L})(x)\|_{2} \leq c, \quad \text{and} \quad \|\text{Hess}\, \mathscr{L}(x) y\|_{2} \leq c\|y\|_{2}\tag{6.18}$$

(cf. Definition 3.3.4). *Then*

$$\|\Theta_{T+\gamma}-\theta\|_{2} \leq c^{2}\gamma^{2}.\tag{6.19}$$