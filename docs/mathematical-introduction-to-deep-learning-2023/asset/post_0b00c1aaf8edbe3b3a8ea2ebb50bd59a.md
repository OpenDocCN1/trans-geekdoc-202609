
and we call $(\mathscr{D}\mathscr{L})(x)$ the set limiting Fréchet subgradients of $f$ at $x$ (cf. Definitions 1.4.7 and 3.3.4).

### Lemma 9.15.2 (Convex differentials)

Let $\mathfrak{d} \in \mathbb{N}$, $\mathscr{L} \in C(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$, $x, a \in \mathbb{R}^{\mathfrak{d}}$, $b \in \mathbb{R}$, $\varepsilon \in (0, \infty)$ and let $A: \mathbb{R}^{\mathfrak{d}} \rightarrow \mathbb{R}$ satisfy for all $y \in \{z \in \mathbb{R}^{\mathfrak{d}}: \|z - x\|_2 < \varepsilon\}$ that

$$ A(y) = \langle a, y \rangle + b \le \mathscr{L}(y) \quad \text{and} \quad A(x) = \mathscr{L}(x) \quad\quad (9.285) $$

(cf. Definitions 1.4.7 and 3.3.4). Then

- (i) it holds for all $y \in \{z \in \mathbb{R}^{\mathfrak{d}}: \|z - x\|_2 < \varepsilon\}$ that $A(y) = \langle a, y - x \rangle + \mathscr{L}(x)$ and
- (ii) it holds that $a \in (\mathcal{D}\mathscr{L})(x)$

(cf. Definition 9.15.1).

Proof of Lemma 9.15.2. Note that (9.285) shows for all $y \in \{z \in \mathbb{R}^{\mathfrak{d}}: \|z - x\|_2 < \varepsilon\}$ that

$$ \begin{aligned} A(y) &= [A(y) - A(x)] + A(x) = [(\langle a, y \rangle + b) - (\langle a, x \rangle + b)] + A(x) \\ &= \langle a, y - x \rangle + A(x) = \langle a, y - x \rangle + \mathscr{L}(x). \end{aligned} \quad\quad (9.286) $$

This establishes item (i). Observe that (9.285) and item (i) ensure for all $h \in \{z \in \mathbb{R}^{\mathfrak{d}}: 0 < \|z\|_2 < \varepsilon\}$ that

$$ \frac{\mathscr{L}(x + h) - \mathscr{L}(x) - \langle a, h \rangle}{\|h\|_2} = \frac{\mathscr{L}(x + h) - A(x + h)}{\|h\|_2} \ge 0. \quad\quad (9.287) $$

This and (9.283) establish item (ii). The proof of Lemma 9.15.2 is thus complete. $\square$

### Lemma 9.15.3 (Properties of Fréchet subgradients)

Let $\mathfrak{d} \in \mathbb{N}$, $\mathscr{L} \in C(\mathbb{R}^{\mathfrak{d}}, \mathbb{R})$. Then

- (i) it holds for all $x \in \mathbb{R}^{\mathfrak{d}}$ that
$$ (\mathscr{D}\mathscr{L})(x) = \big\{ y \in \mathbb{R}^{\mathfrak{d}}: \exists z = (z_1, z_2): \mathbb{N} \rightarrow \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}: (\forall k \in \mathbb{N}: z_2(k) \in (\mathcal{D}\mathscr{L})(z_1(k)) \wedge [\lim\sup_{k \to \infty}(\|z_1(k) - x\|_2 + \|z_2(k) - y\|_2) = 0]) \big\}, $$
- (ii) it holds for all $x \in \mathbb{R}^{\mathfrak{d}}$ that $(\mathcal{D}\mathscr{L})(x) \subseteq (\mathscr{D}\mathscr{L})(x)$,
- (iii) it holds for all $x \in \{y \in \mathbb{R}^{\mathfrak{d}}: \mathscr{L} \text{ is differentiable at } y\}$ that $(\mathcal{D}\mathscr{L})(x) = \{(\nabla \mathscr{L})(x)\}$,
- (iv) it holds for all $x \in \bigcup_{\substack{U \subseteq \mathbb{R}^{\mathfrak{d}}, U \text{ is open}, \mathscr{L}|_U \in C^1(U, \mathbb{R})}} U$ that $(\mathscr{D}\mathscr{L})(x) = \{(\nabla \mathscr{L})(x)\}$, and
- (v) it holds for all $x \in \mathbb{R}^{\mathfrak{d}}$ that $(\mathscr{D}\mathscr{L})(x)$ is closed.

(cf. Definitions 3.3.4 and 9.15.1).

Proof of Lemma 9.15.3. Throughout this proof, for every $x, y \in \mathbb{R}^{\mathfrak{d}}$ let $Z^{x, y} = (Z_1^{x, y}$, $Z_2^{x, y}) : \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ satisfy for all $k \in \mathbb{N}$ that

$Z_1^{x, y}(k) = x \quad \text{and} \quad Z_2^{x, y}(k) = y$. (9.289)

Note that (9.284) proves that for all $x \in \mathbb{R}^{\mathfrak{d}}$, $y \in (\mathcal{D}\mathcal{L})(x)$, $\varepsilon \in (0, \infty)$ it holds that

$y \in \overline{\bigcup_{v \in \{w \in \mathbb{R}^{\mathfrak{d}}: \|x-w\|_2 < \varepsilon\}} (\mathcal{D}\mathcal{L})(v)}$. (9.290)

This implies that for all $x \in \mathbb{R}^{\mathfrak{d}}$, $y \in (\mathcal{D}\mathcal{L})(x)$ and all $\varepsilon, \delta \in (0, \infty)$ there exists $Y \in$ $(\bigcup_{v \in \{w \in \mathbb{R}^{\mathfrak{d}}: \|x-w\|_2 \leq \varepsilon\}} (\mathcal{D}\mathcal{L})(v))$ such that

$\|y-Y\|_2 < \delta$. (9.291)

Hence, we obtain that for all $x \in \mathbb{R}^{\mathfrak{d}}$, $y \in (\mathcal{D}\mathcal{L})(x)$, $\varepsilon, \delta \in (0, \infty)$ there exist $v \in \{w \in \mathbb{R}^{\mathfrak{d}} : \|x-w\|_2 < \varepsilon\}$, $Y \in (\mathcal{D}\mathcal{L})(v)$ such that $\|y-Y\|_2 < \delta$. This demonstrates that for all $x \in \mathbb{R}^{\mathfrak{d}}$, $y \in (\mathcal{D}\mathcal{L})(x)$, $\varepsilon, \delta \in (0, \infty)$ there exist $X \in \mathbb{R}^{\mathfrak{d}}$, $Y \in (\mathcal{D}\mathcal{L})(X)$ such that

$\|x-X\|_2 < \varepsilon \quad \text{and} \quad \|y-Y\|_2 < \delta$. (9.292)

Therefore, we obtain that for all $x \in \mathbb{R}^{\mathfrak{d}}$, $y \in (\mathcal{D}\mathcal{L})(x)$, $k \in \mathbb{N}$ there exist $z_1, z_2 \in \mathbb{R}^{\mathfrak{d}}$ such that

$z_2 \in (\mathcal{D}\mathcal{L})(z_1) \quad \text{and} \quad \|z_1-x\|_2 + \|z_2-y\|_2 < \frac{1}{k}$. (9.293)

Furthermore, observe that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$, $\varepsilon \in (0, \infty)$ and all $z = (z_1, z_2) : \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ with $\operatorname{lim}\sup_{k \to \infty}(\|z_1(k)-x\|_2 + \|z_2(k)-y\|_2) = 0$ and $\forall k \in \mathbb{N} : z_2(k) \in (\mathcal{D}\mathcal{L})(z_1(k))$ there exist $X, Y \in \mathbb{R}^{\mathfrak{d}}$ such that

$Y \in (\mathcal{D}\mathcal{L})(X) \quad \text{and} \quad \|X-x\|_2 + \|Y-y\|_2 < \varepsilon$. (9.294)

Hence, we obtain that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$, $\varepsilon, \delta \in (0, \infty)$ and all $z = (z_1, z_2) : \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ with $\operatorname{lim}\sup_{k \to \infty}(\|z_1(k)-x\|_2 + \|z_2(k)-y\|_2) = 0$ and $\forall k \in \mathbb{N} : z_2(k) \in (\mathcal{D}\mathcal{L})(z_1(k))$ there exist $X, Y \in \mathbb{R}^{\mathfrak{d}}$ such that

$Y \in (\mathcal{D}\mathcal{L})(X), \quad \|x-X\|_2 < \varepsilon, \quad \text{and} \quad \|y-Y\|_2 < \delta$. (9.295)

This ensures that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$, $\varepsilon, \delta \in (0, \infty)$ and all $z = (z_1, z_2) : \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ with $\operatorname{lim}\sup_{k \to \infty}(\|z_1(k)-x\|_2 + \|z_2(k)-y\|_2) = 0$ and $\forall k \in \mathbb{N} : z_2(k) \in (\mathcal{D}\mathcal{L})(z_1(k))$ there exist $v \in \mathbb{R}^{\mathfrak{d}} : \|x-v\|_2 < \varepsilon\}$, $Y \in (\mathcal{D}\mathcal{L})(v)$ such that $\|y-Y\|_2 < \delta$. Therefore, we obtain that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$, $\varepsilon, \delta \in (0, \infty)$ and all $z = (z_1, z_2) : \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ with $\operatorname{lim}\sup_{k \to \infty}(\|z_1(k)-x\|_2 + \|z_2(k)-y\|_2) = 0$ and $\forall k \in \mathbb{N} : z_2(k) \in (\mathcal{D}\mathcal{L})(z_1(k))$ there exists $Y \in \overline{\bigcup_{v \in \{w \in \mathbb{R}^{\mathfrak{d}} : \|x-w\|_2 \leq \varepsilon\}} (\mathcal{D}\mathcal{L})(v)}$ such that

$\|y-Y\|_2 < \delta$. (9.296)

This establishes that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$, $\varepsilon \in (0, \infty)$ and all $z = (z_1, z_2): \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ with $\lim \sup_{k \to \infty} (\|z_1(k) - x\|_2 + \|z_2(k) - y\|_2) = 0$ and $\forall k \in \mathbb{N}: z_2(k) \in (\mathcal{D}\mathcal{L})(z_1(k))$ it holds that

$y \in \overline{\bigcup_{v \in \{w \in \mathbb{R}^{\mathfrak{d}} : \|x - w\|_2 < \varepsilon\}} (\mathcal{D}\mathcal{L})(v)}.$ (9.297)

This and (9.284) show that for all $x, y \in \mathbb{R}^{\mathfrak{d}}$ and all $z = (z_1, z_2): \mathbb{N} \to \mathbb{R}^{\mathfrak{d}} \times \mathbb{R}^{\mathfrak{d}}$ with $\lim \sup_{k \to \infty} (\|z_1(k) - x\|_2 + \|z_2(k) - y\|_2) = 0$ and $\forall k \in \mathbb{N}: z_2(k) \in (\mathcal{D}\mathcal{L})(z_1(k))$ it holds that

$y \in (\mathcal{D}\mathcal{L})(x),$ (9.298)

Combining this with (9.293) proves item (i). Note that (9.289) implies that for all $x \in \mathbb{R}^{\mathfrak{d}}$, $y \in (\mathcal{D}\mathcal{L})(x)$ it holds that

$\left[ \forall k \in \mathbb{N}: \left(Z_2^x,y(k) \in (\mathcal{D}\mathcal{L})(Z_1^{x,y}(k)) \right) \right] \wedge \left[ \lim \sup_{k \to \infty} \left(\|Z_1^{x,y}(k) - x\|_2 + \|Z_2^{x,y}(k) - y\|_2 \right) = 0 \right]$ (9.299)

(cf. Definitions 3.3.4 and 9.15.1). Combining this with item (i) establishes item (ii). Observe that the fact that for all $a \in \mathbb{R}$ it holds that $-a \leq |a|$ demonstrates that for all $x \in \{y \in \mathbb{R}^{\mathfrak{d}} : \mathcal{L} \text{ is differentiable at } y\}$ it holds that

$\lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\langle \mathcal{L}(x + h) - \mathcal{L}(x) - \langle (\nabla \mathcal{L})(x), h \rangle}{\|h\|_2} \geq \left| -\lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\langle \mathcal{L}(x + h) - \mathcal{L}(x) - \langle (\nabla \mathcal{L})(x), h \rangle}{\|h\|_2} \right|$ (9.300)

$\geq \left[ -\lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\left| \mathcal{L}(x + h) - \mathcal{L}(x) - \langle (\nabla \mathcal{L})(x), h \rangle \right|}{\|h\|_2} \right] = 0$

(cf. Definition 1.4.7). This demonstrates that for all $x \in \{y \in \mathbb{R}^{\mathfrak{d}} : \mathcal{L} \text{ is differentiable at } y\}$ it holds that

$(\nabla \mathcal{L})(x) \in (\mathcal{D}\mathcal{L})(x).$ (9.301)

Moreover, note that for all $v \in \mathbb{R}^{\mathfrak{d}} \setminus \{0\}$ it holds that

$\lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\langle v, h \rangle}{\|h\|_2} = \sup_{\varepsilon \in (0, \infty)} \inf_{h \in \{w \in \mathbb{R}^{\mathfrak{d}} : \|w\|_2 \leq \varepsilon\}} \frac{\langle v, h \rangle}{\|h\|_2}$

$\leq \sup_{\varepsilon \in (0, \infty)} \frac{\langle v, -\varepsilon \|v\| \frac{v}{\|v\|} \rangle}{\left| -\varepsilon \|v\| \frac{v}{\|v\|} \right|_2} = \sup_{\varepsilon \in (0, \infty)} \langle v, -\varepsilon \|v\|^{-1}_2 v \rangle = -\|v\|_2 < 0.$ (9.302)

Hence, we obtain for all $x \in \{y \in \mathbb{R}^{\mathfrak{d}} : \mathcal{L} \text{ is differentiable at } y\}$, $w \in (\mathcal{D}\mathcal{L})(x)$ that

$0 \leq \lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\left( \mathcal{L}(x + h) - \mathcal{L}(x) - \langle w, h \rangle \right)}{\|h\|_2}$

$= \lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\left( \mathcal{L}(x + h) - \mathcal{L}(x) - \langle (\nabla \mathcal{L})(x), h \rangle - \langle w - (\nabla \mathcal{L})(x), h \rangle \right)}{\|h\|_2}$

$\leq \lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\left| \mathcal{L}(x + h) - \mathcal{L}(x) - \langle (\nabla \mathcal{L})(x), h \rangle + \langle (\nabla \mathcal{L})(x) - w, h \rangle \right|}{\|h\|_2}$

$\leq \left[ \lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\langle (\nabla \mathcal{L})(x) - w, h \rangle}{\|h\|_2} \right] + \left[ \lim \sup_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\left| \mathcal{L}(x + h) - \mathcal{L}(x) - \langle (\nabla \mathcal{L})(x), h \rangle \right|}{\|h\|_2} \right]$

$= \lim \inf_{\substack{\mathbb{R}^{\mathfrak{d}} \setminus \{0\} \ni h \to 0}} \frac{\langle (\nabla \mathcal{L})(x) - w, h \rangle}{\|h\|_2} \leq -\| (\nabla \mathcal{L})(x) - w \|_2.$ (9.303)
