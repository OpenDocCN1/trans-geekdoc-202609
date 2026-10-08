Proof of Lemma 9.13.2. Throughout this proof, let $A_1: \mathbb{R}^{l_1} \to \mathbb{R}^{l_1} \times \mathbb{R}^{l_2}$ and $A_2: \mathbb{R}^{l_2} \to \mathbb{R}^{l_1} \times \mathbb{R}^{l_2}$ satisfy for all $x_1 \in \mathbb{R}^{l_1}, x_2 \in \mathbb{R}^{l_2}$ that

$$ A_1(x_1) = (x_1, 0) \quad \text{and} \quad A_2(x_2) = (0, x_2) \quad\quad\quad (9.262) $$

and for every $k \in \{1, 2\}$ let $B_k: \mathbb{R}^{l_1} \times \mathbb{R}^{l_2} \to \mathbb{R}^{l_k}$ satisfy for all $x_1 \in \mathbb{R}^{l_1}, x_2 \in \mathbb{R}^{l_2}$ that

$$ B_k(x_1, x_2) = x_k. \quad\quad\quad (9.263) $$

Note that item **(i)** in Lemma 5.3.1 shows that

$$ f = A_1 \circ F_1 \circ B_1 + A_2 \circ F_2 \circ B_2. \quad\quad\quad (9.264) $$

This, the fact that $A_1$, $A_2$, $F_1$, $F_2$, $B_1$, and $B_2$ are analytic, and Proposition 9.13.1 establishes that $f$ is differentiable. The proof of Lemma 9.13.2 is thus complete. $\square$*

**Lemma 9.13.3.** *Let $\mathfrak{d}_1, \mathfrak{d}_2, l_0, l_1, l_2 \in \mathbb{N}$, for every $k \in \{1, 2\}$ let $F_k: \mathbb{R}^{\mathfrak{d}_k} \times \mathbb{R}^{l_k - 1} \to \mathbb{R}^{l_k}$ be analytic, and let $f: \mathbb{R}^{\mathfrak{d}_1} \times \mathbb{R}^{\mathfrak{d}_2} \times \mathbb{R}^{l_0} \to \mathbb{R}^{l_2}$ satisfy for all $\theta_1 \in \mathbb{R}^{\mathfrak{d}_1}, \theta_2 \in \mathbb{R}^{\mathfrak{d}_2}$, $x \in \mathbb{R}^{l_0}$ that

$$ f(\theta_1, \theta_2, x) = \big(F_2(\theta_2, \cdot) \circ F_1(\theta_1, \cdot)\big)(x) \quad\quad\quad (9.265) $$

(cf. Definition 9.7.1). Then $f$ is analytic.*

Proof of Lemma 9.13.3. Throughout this proof, let $A: \mathbb{R}^{\mathfrak{d}_1} \times \mathbb{R}^{\mathfrak{d}_2} \times \mathbb{R}^{l_0} \to \mathbb{R}^{\mathfrak{d}_2} \times \mathbb{R}^{\mathfrak{d}_1 + l_0}$ and $B: \mathbb{R}^{\mathfrak{d}_2} \times \mathbb{R}^{\mathfrak{d}_1 + l_0} \to \mathbb{R}^{\mathfrak{d}_2} \times \mathbb{R}^{l_1}$ satisfy for all $\theta_1 \in \mathbb{R}^{\mathfrak{d}_1}$, $\theta_2 \in \mathbb{R}^{\mathfrak{d}_2}$, $x \in \mathbb{R}^{l_0}$ that

$$ A(\theta_1, \theta_2, x) = (\theta_2, (\theta_1, x)) \quad \text{and} \quad B(\theta_2, (\theta_1, x)) = (\theta_2, F_1(\theta_1, x)), \quad\quad\quad (9.266) $$

Observe that item **(i)** in Lemma 5.3.2 proves that

$$ f = F_2 \circ B \circ A. \quad\quad\quad (9.267) $$

Furthermore, note that Lemma 9.13.2 (with $\mathfrak{d}_1 \frown \mathfrak{d}_2$, $\mathfrak{d}_2 \frown \mathfrak{d}_1 + l_1$, $l_1 \frown \mathfrak{d}_2$, $l_2 \frown l_1$, $F_1 \frown (\mathbb{R}^{\mathfrak{d}_2} \ni \theta_2 \mapsto \theta_2 \in \mathbb{R}^{\mathfrak{d}_2})$, $F_2 \frown (\mathbb{R}^{\mathfrak{d}_1 + l_1} \ni (\theta_1, x) \mapsto F_1(\theta_1, x) \in \mathbb{R}^{l_1})$ in the notation of Lemma 9.13.2) implies that $B$ is analytic. Combining this, the fact that $A$ is analytic, the fact that $F_2$ is analytic, and (9.267) with Proposition 9.13.1 demonstrates that $f$ is analytic. The proof of Lemma 9.13.3 is thus complete. $\square$*

**Corollary 9.13.4** (Analyticity of realization functions of ANNs). *Let $L \in \mathbb{N}$, $l_0, l_1, \ldots, l_L \in \mathbb{N}$ and for every $k \in \{1, 2, \ldots, L\}$ let $\Psi_k: \mathbb{R}^{l_k} \to \mathbb{R}^{l_k}$ be analytic (cf. Definition 9.7.1). Then

$$ \mathbb{R}^{\sum_{k=1}^{L} l_k(l_k - 1) + 1} \times \mathbb{R}^{l_0} \ni (\theta, x) \mapsto \big(\mathcal{N}^{\mathfrak{d}_0}_{\Psi_1, \Psi_2, \ldots, \Psi_L}\big)(x) \in \mathbb{R}^{l_L} \quad\quad\quad (9.268) $$

is analytic (cf. Definition 1.1.3).*