**Lemma 3.1.2** (Elementary properties of moduli of continuity). *Let $A \subseteq \mathbb{R}$ be a set and let $f : A \rightarrow \mathbb{R}$ be a function. Then*

+   *   (i) it holds that $w_f$ is non-decreasing,
*   (ii) it holds that $f$ is uniformly continuous if and only if $\lim_{h\searrow 0} w_f(h) = 0$,
*   (iii) it holds that $f$ is globally bounded if and only if $w_f(\infty) < \infty$, and
*   (iv) it holds for all $x, y \in A$ that $|f(x) - f(y)| \leq w_f(|x - y|)$

*(cf. Definition 3.1.1).*

*Proof of Lemma 3.1.2.* Observe that (3.1) proves items (i), (ii), (iii), and (iv). The proof of Lemma 3.1.2 is thus complete. $\Box$

**Lemma 3.1.3** (Subadditivity of moduli of continuity). *Let $a \in [-\infty, \infty]$, $b \in [a, \infty]$, let $f : ([a, b] \cap \mathbb{R}) \rightarrow \mathbb{R}$ be a function, and let $h, \mathfrak{h} \in [0, \infty]$. Then*

$$w_f(h + \mathfrak{h}) \leq w_f(h) + w_f(\mathfrak{h}) \tag{3.2}$$

*(cf. Definition 3.1.1).*

*Proof of Lemma 3.1.3.* Throughout this proof, assume without loss of generality that $\mathfrak{h} \leq h < \infty$. Note that the fact that for all $x, y \in [a, b] \cap \mathbb{R}$ with $|x - y| \leq h + \mathfrak{h}$ it holds that $[x - h, x + h] \cap [y - \mathfrak{h}, y + \mathfrak{h}] \cap [a, b] \neq \emptyset$ ensures that for all $x, y \in [a, b] \cap \mathbb{R}$ with $|x - y| \leq h + \mathfrak{h}$ there exists $z \in [a, b] \cap \mathbb{R}$ such that

$$|x - z| \leq h \quad \text{and} \quad |y - z| \leq \mathfrak{h}. \tag{3.3}$$

Items (i) and (iv) in Lemma 3.1.2 therefore imply that for all $x, y \in [a, b] \cap \mathbb{R}$ with $|x - y| \leq h + \mathfrak{h}$ there exists $z \in [a, b] \cap \mathbb{R}$ such that

$$\begin{align*}
|f(x) - f(y)| &\leq |f(x) - f(z)| + |f(y) - f(z)| \\
&\leq w_f(|x - z|) + w_f(|y - z|) \leq w_f(h) + w_f(\mathfrak{h})
\end{align*} \tag{3.4}$$

*(cf. Definition 3.1.1). Combining this with (3.1) demonstrates that*

$$w_f(h + \mathfrak{h}) \leq w_f(h) + w_f(\mathfrak{h}). \tag{3.5}$$

The proof of Lemma 3.1.3 is thus complete. $\Box$

**Lemma 3.1.4** (Properties of moduli of continuity of Lipschitz continuous functions). *Let $A \subseteq \mathbb{R}$, $L \in [0, \infty)$, let $f : A \rightarrow \mathbb{R}$ satisfy for all $x, y \in A$ that*

$$|f(x) - f(y)| \leq L|x - y|, \tag{3.6}$$

*and let $h \in [0, \infty)$. Then*

$$w_f(h) \leq Lh \tag{3.7}$$

*(cf. Definition 3.1.1).*