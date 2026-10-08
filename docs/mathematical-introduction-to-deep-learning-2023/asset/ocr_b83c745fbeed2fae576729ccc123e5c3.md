(*iv*) it holds for all $x \in E$ that

$\| F(x) - f(x) \| \le 2L \left[ \inf_{y \in \mathcal{M}} \delta(x, y) \right]$.  (4.15)

*Proof of Corollary 4.1.4*. Note that Proposition **4.1.3** establishes items **(i)**, **(ii)**, **(iii)**, and **(iv)**. The proof of Corollary **4.1.4** is thus complete. $\square$

*Exercise* **4.1.1**. Prove or disprove the following statement: There exists $\Phi \in \mathbf{N}$ such that $\mathcal{I}(\Phi) = 2$, $\mathcal{O}(\Phi) = 1$, $\mathcal{P}(\Phi) \le 3 \, 000 \, 000 \, 000$, and

$\sup_{x, y \in [0, 2\pi]} \left| \sin(x) \sin(y) - (\mathcal{R}_{\mathfrak{r}}^{\mathbf{N}}(\Phi))(x, y) \right| \le \frac{1}{5}$. (4.16)

# ## **4.2** ANN representations

# ### **4.2.1** ANN representations for the 1-norm

**Definition 4.2.1** (1-norm ANN representations). *We denote by* $(\mathbb{L}_d)_{d \in \mathbb{N}} \subseteq \mathbf{N}$ *the fully-connected feedforward ANN*s *which satisfy that*

(*i*) it holds that

$\mathbb{L}_1 = \left( \left( \begin{pmatrix} 1 \\ -1 \end{pmatrix} \right), \left( \begin{pmatrix} 0 \\ 0 \end{pmatrix} \right), \left( \begin{pmatrix} 1 & 1 \\ 0 & 0 \end{pmatrix} \right) \right) \in (\mathbb{R}^{2 \times 1} \times \mathbb{R}^{2}) \times (\mathbb{R}^{1 \times 2} \times \mathbb{R}^1)$ (4.17)

and

(*ii*) it holds for all $d \in \{2, 3, 4, \ldots\}$ that $\mathbb{L}_d = \mathbb{S}_{1, d} \bullet \mathbf{P}_d(\mathbb{L}_1, \mathbb{L}_1, \ldots, \mathbb{L}_1)$

(*cf. Definitions* **1.3.1**, **2.1.1**, **2.2.1**, *and* **2.4.1** *).*

**Proposition 4.2.2** (Properties of fully-connected feedforward 1-norm ANNs). *Let* $d \in \mathbb{N}$. *Then*

(*i*) it holds that $\mathcal{D}(\mathbb{L}_d) = (d, 2d, 1)$,

(*ii*) it holds that $\mathcal{R}_{\mathfrak{r}}^{\mathbf{N}}(\mathbb{L}_d) \in C(\mathbb{R}^d, \mathbb{R})$, *and*

(*iii*) it holds for all $x \in \mathbb{R}^d$ that $(\mathcal{R}_{\mathfrak{r}}^{\mathbf{N}}(\mathbb{L}_d))(x) = \|x\|_1$

(*cf. Definitions* **1.2.4**, **1.3.1**, **1.3.4**, **3.3.4**, *and* **4.2.1** *).*