proves that for all $\mathbf{z} = (z_1, \dots, z_d) \in [0, \infty)^d$ with $\sum_{i=1}^d z_i = \sum_{i=1}^d y_i$ and $\forall i \in J: z_i = y_i$ it holds that $\mathbf{z} = \mathbf{y}$. The assumption that $\sum_{i=1}^d x_i = \sum_{i=1}^d y_i$ and $\mathbf{x} \neq \mathbf{y}$ therefore ensures that there exists $i \in J$ such that $x_i \neq y_i > 0$. Combining this with (5.60) shows that for all $h \in [0, 1)$ it holds that

$$g''(h) > 0. \tag{5.62}$$

The fundamental theorem of calculus hence implies that for all $h \in (0, 1)$ it holds that

$$g'(h) = g'(0) + \int_0^h g''(b) \, \mathrm{d}b > g'(0). \tag{5.63}$$

In addition, note that (5.59) and the assumption that $\sum_{i=1}^d x_i = \sum_{i=1}^d y_i$ demonstrate that

$\begin{align*} g'(0) &= -\sum_{i \in J} \frac{y_i (x_i - y_i)}{y_i} = \sum_{i \in J} (y_i - x_i) = \left[ \sum_{i \in J} y_i \right] - \left[ \sum_{i \in J} x_i \right] \\ &= \left[ \sum_{i \in \{1,2,\dots,d\}} y_i \right] - \left[ \sum_{i \in J} x_i \right] = \left[ \sum_{i \in \{1,2,\dots,d\}} x_i \right] - \left[ \sum_{i \in J} x_i \right] = \left[ \sum_{i \in \{1,2,\dots,d\} \setminus J} x_i \right] \ge 0. \end{align*} \tag{5.64}

Combining this and (5.63) establishes that for all $h \in (0, 1)$ it holds that

$$g'(h) > 0. \tag{5.65}$$

Therefore, we obtain that $g$ is strictly increasing. This and (5.55) prove that $f|_{[0,1]}$ is strictly decreasing. Next observe that (5.55) and (5.58) ensure that for all $h \in (0, 1]$ it holds that

$$f(h) = -\sum_{i \in J} \ln(y_i + (1-h)(x_i - y_i)) y_i = -\sum_{i \in J} \ln(x_i + h(y_i - x_i)) y_i \in \mathbb{R}. \tag{5.66}$$

Furthermore, note that items (i) and (ii) in Lemma 5.4.6 show that

$$\left[ f(0) = \infty \right] \lor \left[ f(0) = -\sum_{i \in J} \ln(x_i + 0(y_i - x_i)) y_i \in \mathbb{R} \right]. \tag{5.67}$$

Combining this with (5.66) implies that

$$\left[ f(0) = \infty \right] \lor \left[ \forall h \in [0, 1]: f(h) \in \mathbb{R} \right] \land \left( [0, 1] \ni h \mapsto f(h) \in \mathbb{R} \right) \in C([0, 1], \mathbb{R}]). \tag{5.68}$$

This and the fact that $f|_{[0,1]}$ is strictly decreasing demonstrate that $f$ is strictly decreasing. The proof of Lemma 5.4.7 is thus complete.

**Corollary 5.4.8.** *Let $d \in \mathbb{N} \setminus \{1\}$, let $A = \{ \mathbf{x} = (x_1, \dots, x_d) \in [0, 1]^d: \sum_{i=1}^d x_i = 1 \}$, let $\mathbf{L}$ be the $d$-dimensional cross-entropy loss function, and let $\mathbf{y} \in A$ (cf. Definition 5.4.5). Then*