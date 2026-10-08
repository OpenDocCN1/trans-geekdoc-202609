
*Proof of Corollary 5.6.3.* Note that Proposition 5.6.2 and (5.106) establish (5.107). The proof of Corollary 5.6.3 is thus complete. $\square$

## **5.6.3 On Lyapunov-type functions and coercivity-type conditions**

**Lemma 5.6.4** *(Derivative of the standard norm).* Let $\mathfrak{d} \in \mathbb{N}$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$ and let $V: \mathbb{R}^{\mathfrak{d}} \to \mathbb{R}$ satisfy for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that

$$ V(\theta) = \lVert \theta - \vartheta \rVert_{2}^{2} \quad (5.108) $$

*(cf. Definition 3.3.4).* Then it holds for all $\theta \in \mathbb{R}^{\mathfrak{d}}$ that $V \in C^{\infty}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ and

$$ (\nabla V)(\theta) = 2(\theta - \vartheta). \quad (5.109) $$

*Proof of Lemma 5.6.4.* Throughout this proof, let $\vartheta_{1}, \vartheta_{2}, \ldots, \vartheta_{\mathfrak{d}} \in \mathbb{R}$ satisfy $\vartheta = (\vartheta_{1}, \vartheta_{2}, \ldots, \vartheta_{\mathfrak{d}})$. Note that the fact that for all $\theta = (\theta_{1}, \theta_{2}, \ldots, \theta_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$ it holds that

$$ V(\theta) = \sum_{i=1}^{\mathfrak{d}}(\theta_{i} - \vartheta_{i})^{2} \quad (5.110) $$

implies that for all $\theta = (\theta_{1}, \theta_{2}, \ldots, \theta_{\mathfrak{d}}) \in \mathbb{R}^{\mathfrak{d}}$ it holds that $V \in C^{\infty}(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$ and

$$ (\nabla V)(\theta) = \begin{pmatrix} \frac{\partial V}{\partial \theta_{1}}(\theta) \\ \vdots \\ \frac{\partial V}{\partial \theta_{\mathfrak{d}}}(\theta) \end{pmatrix} = \begin{pmatrix} 2(\theta_{1} - \vartheta_{1}) \\ \vdots \\ 2(\theta_{\mathfrak{d}} - \vartheta_{\mathfrak{d}}) \end{pmatrix} = 2(\theta - \vartheta). \quad (5.111) $$

The proof of Lemma 5.6.4 is thus complete. $\square$

**Corollary 5.6.5** *(On quadratic Lyapunov-type functions and coercivity-type conditions).* Let $\mathfrak{d} \in \mathbb{N}$, $c \in \mathbb{R}$, $T \in (0, \infty)$, $\vartheta \in \mathbb{R}^{\mathfrak{d}}$, let $O \subseteq \mathbb{R}^{\mathfrak{d}}$ be open, let $\mathcal{L}: O \to \mathbb{R}$ satisfy for all $\theta \in O$ that

$$ \langle \theta - \vartheta, (\nabla \mathcal{L})(\theta) \rangle \geq c \lVert \theta - \vartheta \rVert_{2}^{2}, \quad (5.112) $$

and let $\Theta \in C([0, T], O)$ satisfy for all $t \in [0, T]$ that $\Theta_{t} = \Theta_{0} - \int_{0}^{t}(\nabla \mathcal{L})(\Theta_{s}) \, \mathrm{d}s$ *(cf. Definitions 1.4.7 and 3.3.4).* Then it holds for all $t \in [0, T]$ that

$$ \lVert \Theta_{t} - \vartheta \rVert_{2} \leq e^{-ct} \lVert \Theta_{0} - \vartheta \rVert_{2}. \quad (5.113) $$

*Proof of Corollary 5.6.5.* Throughout this proof, let $\mathcal{F}: O \to \mathbb{R}^{\mathfrak{d}}$ satisfy for all $\theta \in O$ that

$$ \mathcal{F}(\theta) = -(\nabla \mathcal{L})(\theta) \quad (5.114) $$

and let $V: O \to \mathbb{R}$ satisfy for all $\theta \in O$ that

$$ V(\theta) = \lVert \theta - \vartheta \rVert_{2}^{2}. \quad (5.115) $$

Observe that Lemma 5.6.4 and (5.112) ensure that for all $\theta \in O$ it holds that $V \in C^{1}(O, \mathbb{R})$ and

$$ V^{\prime}(\theta)\mathcal{F}(\theta) = \langle (\nabla V)(\theta), \mathcal{F}(\theta)\rangle = \langle 2(\theta-\vartheta), \mathcal{F}(\theta)\rangle $$
$$ = -2\langle(\theta-\vartheta),(\nabla\mathcal{L})(\theta)\rangle \leq -2c\|\theta-\vartheta\|_{2}^{2} = -2cV(\theta). $$

Corollary 5.6.3 hence proves that for all $t \in [0, T]$ it holds that

$$ \|\Theta_{t}-\vartheta\|_{2}^{2} = V(\Theta_{t}) \leq e^{-2ct} V(\Theta_{0}) = e^{-2ct}\|\Theta_{0}-\vartheta\|_{2}^{2}. $$

The proof of Corollary 5.6.5 is thus complete. $\square$

## **5.6.4 Sufficient and necessary conditions for local minimum points**

**Lemma 5.6.6.** Let $\mathfrak{d} \in \mathbb{N}$, let $O \subseteq \mathbb{R}^{\mathfrak{d}}$ be open, let $\vartheta \in O$, let $\mathscr{L}: O \to \mathbb{R}$ be a function, assume that $\mathscr{L}$ is differentiable at $\vartheta$, and assume that $(\nabla\mathscr{L})(\vartheta) \neq 0$. Then there exists $\theta \in O$ such that $\mathscr{L}(\theta) < \mathscr{L}(\vartheta)$.

*Proof of Lemma 5.6.6.* Throughout this proof, let $v \in \mathbb{R}^{\mathfrak{d}}\setminus\{0\}$ satisfy $v = -(\nabla\mathscr{L})(\vartheta)$, let $\delta \in (0, \infty)$ satisfy for all $t \in (-\delta, \delta)$ that

$$ \vartheta + tv = \vartheta - t(\nabla\mathscr{L})(\vartheta) \in O, $$

and let $L: (-\delta, \delta) \to \mathbb{R}$ satisfy for all $t \in (-\delta, \delta)$ that

$$ L(t) = \mathscr{L}(\vartheta+tv). $$

Note that for all $t \in (0, \delta)$ it holds that

$$ \left|\left|\frac{L(t)-L(0)}{t} + \frac{L(t)-L(0)}{t} \langle(\nabla\mathscr{L})(\vartheta), v\rangle\right|\right| = \left|\left|\frac{\mathscr{L}(\vartheta+tv)-\mathscr{L}(\vartheta)}{t} + \langle(\nabla\mathscr{L})(\vartheta), (\nabla\mathscr{L})(\vartheta)\rangle\right|\right| $$
$$ = \left|\left|\frac{\mathscr{L}(\vartheta+tv)-\mathscr{L}(\vartheta)}{t} - \|(\nabla\mathscr{L})(\vartheta)\|_{2}^{2}\right|\right|. $$

The assumption that $\mathscr{L}$ is differentiable at $\vartheta$ hence demonstrates that

$$ \limsup_{t \searrow 0} \bigg[\frac{L(t) - L(0)}{t} + \|v\|_2^2 \bigg] = 0. $$

The fact that $\|v\|_2^2 > 0$ therefore demonstrates that there exists $t \in (0, \delta)$ such that

$$ \bigg|\bigg[\frac{L(t) - L(0)}{t} + \|v\|_2^2 \bigg] < \frac{\|v\|_2^2}{2}. $$

The triangle inequality and the fact that $\|v\|_2^2 > 0$ hence prove that

$$ \begin{aligned} \frac{L(t) - L(0)}{t} &= \bigg[\frac{L(t) - L(0)}{t} + \|v\|_2^2 \bigg] - \|v\|_2^2 \\ &\le \bigg|\frac{L(t) - L(0)}{t} + \|v\|_2^2 \bigg| - \|v\|_2^2 \\ &< \frac{\|v\|_2^2}{2} - \|v\|_2^2 = -\frac{\|v\|_2^2}{2} < 0. \end{aligned} $$

This ensures that

$$ \mathscr{L}(\vartheta + tv) = L(t) < L(0) = \mathscr{L}(\vartheta). \quad \square $$

The proof of Lemma 5.6.6 is thus complete.

**Lemma 5.6.7** (A necessary condition for a local minimum point).

Let $\mathfrak{d} \in \mathbb{N}$, let $O \subseteq \mathbb{R}^\mathfrak{d}$ be open, let $\vartheta \in O$, let $\mathscr{L} : O \rightarrow \mathbb{R}$ be a function, assume that $\mathscr{L}$ is differentiable at $\vartheta$, and assume

$$ \mathscr{L}(\vartheta) = \inf_{\theta \in O} \mathscr{L}(\theta). \quad (5.126) $$

Then $(\nabla \mathscr{L})(\vartheta) = 0.$

*Proof of Lemma 5.6.7.* We prove Lemma 5.6.7 by contradiction. We thus assume that $(\nabla \mathscr{L})(\vartheta) \neq 0$. Lemma 5.6.6 then implies that there exists $\theta \in O$ such that $\mathscr{L}(\theta) < \mathscr{L}(\vartheta)$. Combining this with (5.126) shows that

$$ \mathscr{L}(\theta) < \mathscr{L}(\vartheta) = \inf_{w \in O} \mathscr{L}(w) \le \mathscr{L}(\theta). $$

The proof of Lemma 5.6.7 is thus complete.

**Lemma 5.6.8** (A sufficient condition for a local minimum point).

Let $\mathfrak{d} \in \mathbb{N}$, $c \in (0, \infty)$, $r \in (0, \infty]$, $\vartheta \in \mathbb{R}^\mathfrak{d}$, $\mathbb{B} = \{w \in \mathbb{R}^\mathfrak{d} \mid \|w - \vartheta\|_2 \le r\}$, $\mathscr{L} \in C^1(\mathbb{R}^\mathfrak{d}, \mathbb{R})$ satisfy for all $\theta \in \mathbb{B}$ that

$$ \langle \theta - \vartheta, (\nabla \mathscr{L})(\theta) \rangle \ge c \|\theta - \vartheta\|_2^2 \quad (5.128) $$

(*cf.* Definitions 1.4.7 and 3.3.4). *Then*

- *(i)* it holds for all $\theta \in \mathbb{B}$ that $\mathscr{L}(\theta) - \mathscr{L}(\vartheta) \ge \frac{c}{2} \|\theta - \vartheta\|_2^2$,
- *(ii)* it holds that $\{ \theta \in \mathbb{B}: \mathscr{L}(\theta) = \inf_{w \in \mathbb{B}} \mathscr{L}(w) \} = \{ \vartheta \}$, and
- *(iii)* it holds that $(\nabla \mathscr{L})(\vartheta) = 0$.

Proof of Lemma 5.6.8. Throughout this proof, let $B$ be the set given by

$$ B = \{ w \in \mathbb{R}^\mathfrak{d}: \| w - \vartheta \|_2 < r \}. \quad (5.129) $$

Note that (5.128) implies that for all $v \in \mathbb{R}^\mathfrak{d}$ with $\| v \|_2 \le r$ it holds that

$$ \langle (\nabla \mathscr{L})(\vartheta + v), v \rangle \ge c \| v \|_2^2. \quad (5.130) $$

The fundamental theorem of calculus hence demonstrates that for all $\theta \in \mathbb{B}$ it holds that

$$ \begin{aligned} \mathscr{L}(\theta) - \mathscr{L}(\vartheta) &= [\mathscr{L}(\vartheta + t(\theta - \vartheta))]_{t=0}^{t=1} \\ &= \int_0^1 \mathscr{L}'(\vartheta + t(\theta - \vartheta))(\theta - \vartheta) \, \mathrm{d}t \\ &= \int_0^1 \langle (\nabla \mathscr{L})(\vartheta + t(\theta - \vartheta)), (\theta - \vartheta) \rangle \, \mathrm{d}t \\ &= \int_0^1 \frac{\langle (\nabla \mathscr{L})(\vartheta + t(\theta - \vartheta)), t(\theta - \vartheta) \rangle}{t} \, \mathrm{d}t \\ &\ge \int_0^1 c \| t(\theta - \vartheta) \|_2^2 \frac{1}{t} \, \mathrm{d}t = c \| \theta - \vartheta \|_2^2 \left[ \int_0^1 t \, \mathrm{d}t \right] = \tfrac{c}{2} \| \theta - \vartheta \|_2^2 . \end{aligned} \quad (5.131) $$

This proves item *(i)*. Next observe that (5.131) ensures that for all $\theta \in \mathbb{B} \setminus \{ \vartheta \}$ it holds that

$$ \mathscr{L}(\theta) \ge \mathscr{L}(\vartheta) + \tfrac{c}{2} \| \theta - \vartheta \|_2^2 > \mathscr{L}(\vartheta). \quad (5.132) $$

Hence, we obtain for all $\theta \in \mathbb{B} \setminus \{ \vartheta \}$ that

$$ \inf_{w \in \mathbb{B}} \mathscr{L}(w) = \mathscr{L}(\vartheta) < \mathscr{L}(\theta). \quad (5.133) $$

This establishes item *(ii)*. It thus remains to prove item *(iii)*. For this observe that item *(ii)* ensures that

$$ \{ \theta \in B: \mathscr{L}(\theta) = \inf_{w \in B} \mathscr{L}(w) \} = \{ \vartheta \}. \quad (5.134) $$

Combining this, the fact that $B$ is open, and Lemma 5.6.7 (applied with $\mathfrak{d} \curvearrowright \mathfrak{d}$, $\mathcal{O} \curvearrowright B$, $\vartheta \curvearrowright \vartheta$, $\mathscr{L} \curvearrowright \mathscr{L}|_B$ in the notation of Lemma 5.6.7) assures that $(\nabla \mathscr{L})(\vartheta) = 0$. This establishes item *(iii)*. The proof of Lemma 5.6.8 is thus complete. ∎
