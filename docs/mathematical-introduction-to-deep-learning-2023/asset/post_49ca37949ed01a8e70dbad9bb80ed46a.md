
As discussed in Section 6.1 above, the GD optimization method can be viewed as an Euler discretization of the associated GF ODE in Theorem 5.7.4 in Chapter 5. In the literature also more sophisticated methods than the Euler method have been employed to approximate the GF ODE. In particular, higher order Runge-Kutta methods have been used to approximate local minimum points of optimization problems (cf., for example, Zhang et al. [433]). In this section we illustrate this in the case of the explicit midpoint method.

### Definition 6.2.1
(Explicit midpoint GD optimization method)
Let $\mathfrak{d} \in \mathbb{N}$, $(\gamma_n)_{n \in \mathbb{N}} \subseteq [0, \infty)$, $\xi \in \mathbb{R}^{\mathfrak{d}}$ and let $\mathcal{L} : \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ and $\mathscr{G} : \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}^{\mathfrak{d}}$ satisfy for all $U \in \{V \subseteq \mathbb{R}^{\mathfrak{d}}: V \text{ is open}\}$, $\theta \in U$ with $\mathcal{L}|_U \in C^1(U, \mathbb{R}^{\mathfrak{d}})$ that

$$\mathscr{G}(\theta) = (\nabla \mathcal{L})(\theta). \tag{6.166}$$

Then we say that $\Theta$ is the explicit midpoint GD process for the objective function $\mathcal{L}$ with generalized gradient $\mathscr{G}$, learning rates $(\gamma_n)_{n \in \mathbb{N}}$, and initial value $\xi$ (we say that $\Theta$ is the explicit midpoint GD process for the objective function $\mathcal{L}$ with learning rates $(\gamma_n)_{n \in \mathbb{N}}$ and initial value $\xi$) if and only if it holds that $\Theta : \mathbb{N}_0 \rightarrow \mathbb{R}^{\mathfrak{d}}$ is the function from $\mathbb{N}_0$ to $\mathbb{R}^{\mathfrak{d}}$ which satisfies for all $n \in \mathbb{N}$ that

$$\Theta_0 = \xi \quad\quad\text{and}\quad\quad\Theta_n = \Theta_{n-1} - \gamma_n \mathscr{G}(\Theta_{n-1} - \tfrac{\gamma_n}{2} \mathscr{G}(\Theta_{n-1})). \tag{6.167}$$

## 6.2.1 Explicit midpoint discretizations for GF ODEs

### Lemma 6.2.2
(Local error of the explicit midpoint method)
Let $\mathfrak{d} \in \mathbb{N}$, $T, \gamma, c \in [0, \infty)$, $\mathscr{G} \in C^2(\mathbb{R}^{\mathfrak{d}}, \mathbb{R}^{\mathfrak{d}})$, $\Theta \in C([0, \infty), \mathbb{R}^{\mathfrak{d}})$, $\theta \in \mathbb{R}^{\mathfrak{d}}$ satisfy for all $x, y, z \in \mathbb{R}^{\mathfrak{d}}$, $t \in [0, \infty)$ that

$$\Theta_t = \Theta_0 + \int_0^t \mathscr{G}(\Theta_s)\,\mathrm{d}s, \qquad\theta = \Theta_T + \gamma \mathscr{G}(\Theta_T + \tfrac{\gamma}{2} \mathscr{G}(\Theta_T)), \tag{6.168}$$

$$\|\mathscr{G}(x)\|_2 \leq c, \qquad\|\mathscr{G}'(x) y\|_2 \leq c\|y\|_2, \quad\quad\text{and}\quad\quad\|\mathscr{G}''(x)(y, z)\|_2 \leq c\|y\|_2\|z\|_2 \tag{6.169}$$

(cf. Definition 3.3.4). Then

$$\|\Theta_{T+\gamma} - \theta\|_2 \leq c^3 \gamma^3. \tag{6.170}$$

**Proof of Lemma 6.2.2.** Note that the fundamental theorem of calculus, the assumption that $\mathscr{G} \in C^2(\mathbb{R}^{\mathfrak{d}}, \mathbb{R}^{\mathfrak{d}})$, and (6.168) assure that for all $t \in [0, \infty)$ it holds that $\Theta \in C^1([0, \infty), \mathbb{R}^{\mathfrak{d}})$ and

$$\dot{\Theta}_t = \mathscr{G}(\Theta_t). \tag{6.171}$$

Combining this with the assumption that $\mathscr{G} \in C^{2}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R}^{\mathfrak{d}})$ and the chain rule ensures that for all $t \in [0, \infty)$ it holds that $\Theta \in C^{2}([0, \infty), \mathbb{R}^{\mathfrak{d}})$ and

$$\ddot{\Theta}_{t} = \mathscr{G}'(\Theta_{t})\dot{\Theta}_{t} = \mathscr{G}'(\Theta_{t})\mathscr{G}(\Theta_{t}). \tag{6.172}$$

Theorem 6.1.3 and (6.171) hence ensure that

$$\begin{aligned}\Theta_{T+\frac{\gamma}{2}} &= \Theta_{T} + \frac{\gamma}{2}\dot{\Theta}_{T} + \int_{0}^{1}(1-r)^{2}\frac{\gamma}{2}\ddot{\Theta}_{T+r\gamma/2}\,\mathrm{d}r \\&= \Theta_{T} + \frac{\gamma}{2}\mathscr{G}(\Theta_{T}) + \frac{\gamma^{2}}{4}\int_{0}^{1}(1-r)\mathscr{G}'(\Theta_{T+r\gamma/2})\mathscr{G}(\Theta_{T+r\gamma/2})\,\mathrm{d}r.\end{aligned} \tag{6.173}$$

Therefore, we obtain that

$$\Theta_{T+\frac{\gamma}{2}} - \Theta_{T} - \frac{\gamma}{2}\mathscr{G}(\Theta_{T}) = \frac{\gamma^{2}}{4}\int_{0}^{1}(1-r)\mathscr{G}'(\Theta_{T+r\gamma/2})\mathscr{G}(\Theta_{T+r\gamma/2})\,\mathrm{d}r. \tag{6.174}$$

Combining this, the fact that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$ it holds that $\|\mathscr{G}(x) - \mathscr{G}(y)\|_{2} \leq c\|x - y\|_{2}$, and (6.169) ensures that

$$\begin{aligned}\left\|\mathscr{G}\left(\Theta_{T+\frac{\gamma}{2}}\right) - \mathscr{G}\left(\Theta_{T} + \frac{\gamma}{2}\mathscr{G}(\Theta_{T})\right)\right\|_{2} &\leq c\left\|\Theta_{T+\frac{\gamma}{2}} - \Theta_{T} - \frac{\gamma}{2}\mathscr{G}(\Theta_{T})\right\|_{2}\\&\leq \frac{c\gamma^{2}}{4}\int_{0}^{1}(1-r)\left\|\mathscr{G}'(\Theta_{T+r\gamma/2})\mathscr{G}(\Theta_{T+r\gamma/2})\right\|_{2}\,\mathrm{d}r\\&\leq \frac{c^{3}\gamma^{2}}{4}\int_{0}^{1}(1-r)\,\mathrm{d}r = \frac{c^{3}\gamma^{2}}{8}.\end{aligned} \tag{6.175}$$

Furthermore, observe that (6.171), (6.172), the hypothesis that $\mathscr{G} \in C^{2}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R}^{\mathfrak{d}})$, the product rule, and the chain rule assure that for all $t \in [0, \infty)$ it holds that $\Theta \in C^{3}([0, \infty), \mathbb{R}^{\mathfrak{d}})$ and

$$\begin{aligned}\dddot{\Theta}_{t} &= \mathscr{G}''(\Theta_{t})(\dot{\Theta}_{t}, \dot{\Theta}_{t}) + \mathscr{G}'(\Theta_{t})\mathscr{G}'(\Theta_{t})\dot{\Theta}_{t}\\&= \mathscr{G}''(\Theta_{t})(\mathscr{G}(\Theta_{t}), \mathscr{G}(\Theta_{t})) + \mathscr{G}'(\Theta_{t})\mathscr{G}'(\Theta_{t})\mathscr{G}(\Theta_{t}).\end{aligned} \tag{6.176}$$

Theorem 6.1.3, (6.171), and (6.172) hence imply that for all $s, t \in [0, \infty)$ it holds that

$$\begin{aligned}\Theta_{s} &= \Theta_{t} + (s - t)\dot{\Theta}_{t} + \frac{(s - t)^{2}}{2}\ddot{\Theta}_{t} + \int_{0}^{1}\left[\frac{(1 - r)^{2}(s - t)^{3}}{6}\right]\dddot{\Theta}_{t + r(s - t)}\,\mathrm{d}r\\&= \Theta_{t} + (s - t)\mathscr{G}(\Theta_{t}) + \frac{(s - t)^{2}}{2}\mathscr{G}'(\Theta_{t})\mathscr{G}(\Theta_{t})\\&\quad + \frac{(s - t)^{3}}{6}\int_{0}^{1}(1 - r)^{2}\left(\mathscr{G}''(\Theta_{t + r(s - t)})(\mathscr{G}(\Theta_{t + r(s - t)}), \mathscr{G}(\Theta_{t + r(s - t)})) \\&\qquad + \mathscr{G}'(\Theta_{t + r(s - t)})\mathscr{G}'(\Theta_{t + r(s - t)})\mathscr{G}(\Theta_{t + r(s - t)})\right)\,\mathrm{d}r.\end{aligned} \tag{6.177}$$

This assures that

$$\begin{align*} &\Theta_{T+\gamma} - \Theta_{T}\\ &= \Theta_{T+\frac{\gamma}{2}} - \frac{\gamma}{2}\mathscr{G}(\Theta_{T+\frac{\gamma}{2}}) + \frac{\gamma^{2}}{8}\mathscr{G}'(\Theta_{T+\frac{\gamma}{2}})\mathscr{G}(\Theta_{T+\frac{\gamma}{2}})\\ &\quad + \frac{\gamma^{3}}{48}\int_{0}^{1}\left(1-r\right)^{2}\left(\mathscr{G}''(\Theta_{T+(1+r)\gamma/2})\langle\mathscr{G}(\Theta_{T+(1+r)\gamma/2}),\mathscr{G}(\Theta_{T+(1+r)\gamma/2})\rangle\\ &\quad + \mathscr{G}'(\Theta_{T+(1+r)\gamma/2})\mathscr{G}'(\Theta_{T+(1+r)\gamma/2})\mathscr{G}(\Theta_{T+(1+r)\gamma/2})\right)\mathrm{d}r\\ &\quad - \left[\Theta_{T+\frac{\gamma}{2}} - \frac{\gamma}{2}\mathscr{G}(\Theta_{T+\frac{\gamma}{2}}) + \frac{\gamma^{2}}{8}\mathscr{G}'(\Theta_{T+\frac{\gamma}{2}})\mathscr{G}(\Theta_{T+\frac{\gamma}{2}})\right]\\ &\quad + \frac{\gamma^{3}}{48}\int_{0}^{1}\left(1-r\right)^{2}\left(\mathscr{G}''(\Theta_{T+(1-r)\gamma/2})\langle\mathscr{G}(\Theta_{T+(1-r)\gamma/2}),\mathscr{G}(\Theta_{T+(1-r)\gamma/2})\rangle\\ &\quad + \mathscr{G}'(\Theta_{T+(1-r)\gamma/2})\mathscr{G}'(\Theta_{T+(1-r)\gamma/2})\mathscr{G}(\Theta_{T+(1-r)\gamma/2})\right)\mathrm{d}r\\ &= \gamma\mathscr{G}(\Theta_{T+\frac{\gamma}{2}}) + \frac{\gamma^{3}}{48}\int_{0}^{1}\left(1-r\right)^{2}\left(\mathscr{G}''(\Theta_{T+(1+r)\gamma/2})\langle\mathscr{G}(\Theta_{T+(1+r)\gamma/2}),\mathscr{G}(\Theta_{T+(1+r)\gamma/2})\rangle\right.\\ &\quad \left. + \mathscr{G}'(\Theta_{T+(1+r)\gamma/2})\mathscr{G}'(\Theta_{T+(1+r)\gamma/2})\mathscr{G}(\Theta_{T+(1+r)\gamma/2})\right.\\ &\quad \left. + \mathscr{G}''(\Theta_{T+(1-r)\gamma/2})\langle\mathscr{G}(\Theta_{T+(1-r)\gamma/2}),\mathscr{G}(\Theta_{T+(1-r)\gamma/2})\rangle\right.\\ &\quad \left. + \mathscr{G}'(\Theta_{T+(1-r)\gamma/2})\mathscr{G}'(\Theta_{T+(1-r)\gamma/2})\mathscr{G}(\Theta_{T+(1-r)\gamma/2})\right)\mathrm{d}r.\end{align*} \tag{6.178}$$

This, (6.169), and (6.175) assure that

$$\begin{align*} &\|\Theta_{T+\gamma}-\theta\|_{2} = \left\|\Theta_{T+\gamma}-\Theta_{T}-\gamma\mathscr{G}\left(\Theta_{T}+\frac{\gamma}{2}\mathscr{G}(\Theta_{T})\right)\right\|_{2}\\ &\quad\leq\left\|\Theta_{T+\gamma}-\left[\Theta_{T}+\gamma\mathscr{G}\left(\Theta_{T+\frac{\gamma}{2}}\right)\right]\right\|_{2}+\gamma\left\|\gamma\mathscr{G}\left(\Theta_{T+\frac{\gamma}{2}}\right)-\mathscr{G}\left(\Theta_{T}+\frac{\gamma}{2}\mathscr{G}(\Theta_{T})\right)\right\|_{2}\\ &\quad\leq\gamma\left\|\mathscr{G}\left(\Theta_{T+\frac{\gamma}{2}}\right)-\mathscr{G}\left(\Theta_{T}+\frac{\gamma}{2}\mathscr{G}(\Theta_{T})\right)\right\|_{2}\\ &\quad\quad+\frac{\gamma^{3}}{48}\int_{0}^{1}\left(1-r\right)^{2}\left(\left\|\mathscr{G}''\left(\Theta_{T+(1+r)\gamma/2}\right)\langle\mathscr{G}\left(\Theta_{T+(1+r)\gamma/2}\right),\mathscr{G}\left(\Theta_{T+(1+r)\gamma/2}\right)\rangle\right\|_{2}\right.\\ &\quad\quad\left.+\left\|\mathscr{G}'\left(\Theta_{T+(1+r)\gamma/2}\right)\mathscr{G}'\left(\Theta_{T+(1+r)\gamma/2}\right)\mathscr{G}\left(\Theta_{T+(1+r)\gamma/2}\right)\right\|_{2}\right.\\ &\quad\quad\left.+\left\|\mathscr{G}''\left(\Theta_{T+(1-r)\gamma/2}\right)\langle\mathscr{G}\left(\Theta_{T+(1-r)\gamma/2}\right),\mathscr{G}\left(\Theta_{T+(1-r)\gamma/2}\right)\rangle\right\|_{2}\right.\\ &\quad\quad\left.+\left\|\mathscr{G}'\left(\Theta_{T+(1-r)\gamma/2}\right)\mathscr{G}'\left(\Theta_{T+(1-r)\gamma/2}\right)\mathscr{G}\left(\Theta_{T+(1-r)\gamma/2}\right)\right\|_{2}\right)\mathrm{d}r\\ &\quad\leq\frac{c^{3}\gamma^{3}}{8}+\frac{c^{3}\gamma^{3}}{48}\int_{0}^{1}(1-r)^{2}\mathrm{d}r=\frac{c^{3}\gamma^{3}}{8}+\frac{c^{3}\gamma^{3}}{144}=\frac{19c^{3}\gamma^{3}}{144}\leq c^{3}\gamma^{3}.\end{align*}$$

The proof of Lemma 6.2.2 is thus complete. \qquad \square
