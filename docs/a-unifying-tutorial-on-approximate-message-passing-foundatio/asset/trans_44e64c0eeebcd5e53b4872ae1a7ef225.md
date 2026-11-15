

要从给定 \(\mathcal{G}\) 下的 \(\phi(X,Y)\) 的条件分布中得到相应的 \(\tilde{P}_\omega\)，引理 B.6(b) 告诉我们可以取 \(\tilde{P}_\omega\) 为 \(\phi(U, y)\) 的分布，其中 \(U \sim \mu\) 且 \(y := Y(\omega)\)。本质上，这样做的原因是，由于 \(Y\) 是 \(\mathcal{G}\)-可测的，我们可以在条件化于 \(\mathcal{G}\) 后将 \(Y\) 视为“固定”。

证明. (a) \(R_\omega(\cdot)\) 在 \(\mathcal{A}\) 上是概率测度，对 \(\mathbb{P}|_\mathcal{G}\)-几乎处处 \(\omega \in \Omega\) 成立，这一事实直接从 \(P_\omega(\cdot)\) 和 \(Q_\omega(\cdot)\) 的相应事实得出。对每个 \(A \in \mathcal{A}\)，映射 \(\omega \mapsto R_\omega(A)\) 是 \(\mathcal{G}\)-可测函数的复合（因为根据假设 \(E \in \mathcal{G}\)），因此也是 \(\mathcal{G}\)-可测的。

对于 \(A \in \mathcal{A}\)，令 \(\chi_A: \mathcal{X} \to \{0, 1\}\) 表示 \(A\) 的指示函数。

Then
\[
\chi_A \circ X = (\chi_A \circ X_1)\mathbb{1}_E + (\chi_A \circ X_2)\mathbb{1}_{E^c}.
\]

Since \(\mathbb{1}_E\) and \(\mathbb{1}_{E^c}\) are \(\mathcal{G}\)-measurable, it follows that
\[
\begin{aligned}
\mathbb{P}(X^{-1}(A) \mid \mathcal{G})(\omega)
&= \mathbb{E}((\chi_A \circ X_1)\mathbb{1}_E \mid \mathcal{G})(\omega) + \mathbb{E}((\chi_A \circ X_2)\mathbb{1}_{E^c} \mid \mathcal{G})(\omega) \\
&= \mathbb{E}(\chi_A \circ X_1 \mid \mathcal{G})(\omega)\mathbb{1}_E(\omega) + \mathbb{E}((\chi_A \circ X_2) \mid \mathcal{G})(\omega)\mathbb{1}_{E^c}(\omega) \\
&= P_\omega(A)\mathbb{1}_E(\omega) + Q_\omega(A)\mathbb{1}_{E^c}(\omega) = R_\omega(A)
\end{aligned}
\]

for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega\), as required.

(b) 这可以从 Kallenberg (1997, Theorem 5.4) 和上文 (a) 部分推导出来，但为了完整性，此处给出一个直接证明。注意，对 \(\mathbb{P}|_\mathcal{G}\)-几乎处处 \(\omega \in \Omega_0\)，集合函数 \(\tilde{P}_\omega\) 是由从 \((\mathcal{X}, \mathcal{A})\) 到 \((\mathcal{Z}, \mathcal{C})\) 的可测映射 \(x \mapsto \phi \circ \iota_{Y(\omega)}(x)\) 诱导的 \(P_\omega\) 的前推（像测度）；因此，\(\tilde{P}_\omega\) 确实是对 \(\mathbb{P}|_\mathcal{G}\)-几乎处处 \(\omega \in \Omega_0\) 的概率测度。

Now let \(\mathcal{D}\) denote the collection of all \(D \in \mathcal{A} \otimes \mathcal{B}\) for which \(\omega \mapsto P_\omega(D^{Y(\omega)})\) is \(\mathcal{G}\)-measurable and \(P_\omega(D^{Y(\omega)}) = \mathbb{P}((X,Y)^{-1}(D) \mid \mathcal{G})(\omega)\) for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega_0\). If \(D = A \times B\) for some \(A \in \mathcal{A}\) and \(B \in \mathcal{B}\), then \(D^{Y(\omega)} = A\) if \(Y(\omega) \in B\), and \(D^{Y(\omega)} = \emptyset\) if \(Y(\omega) \notin B\). Thus,
\[
\begin{aligned}
P_\omega(D^{Y(\omega)}) &= P_\omega(A)\mathbb{1}_{\{Y(\omega)\in B\}} = \mathbb{P}(X^{-1}(A) \mid \mathcal{G})(\omega)\mathbb{1}_{\{Y(\omega)\in B\}} \\
&= \mathbb{E}(\chi_A \circ X \mid \mathcal{G})(\omega) \cdot (\chi_B \circ Y)(\omega) \\
&= \mathbb{E}((\chi_A \circ X) \cdot (\chi_B \circ Y) \mid \mathcal{G})(\omega) \\
&= \mathbb{P}((X, Y)^{-1}(D) \mid \mathcal{G})(\omega)
\end{aligned}
\]

for \(\mathbb{P}|_{\mathcal{G}}\)-almost every \(\omega \in \Omega_0\), where we have used the fact that \(\chi_B \circ Y\) is \(\mathcal{G}\)-measurable in the penultimate equality. Thus \(\mathcal{D} \supseteq \{A \times B : A \in \mathcal{A}, B \in \mathcal{B}\}\), which is a \(\pi\)-system that generates \(\mathcal{D}\).

Now suppose that \(D_1, D_2 \in \mathcal{D}\) with \(D_1 \subseteq D_2\). Then
\[
\begin{aligned}
P_\omega((D_2 \setminus D_1)^{Y(\omega)})
&= P_\omega(D_2^{Y(\omega)} \setminus D_1^{Y(\omega)}) = P_\omega(D_2^{Y(\omega)}) - P_\omega(D_1^{Y(\omega)}) \\
&= \mathbb{P}((X, Y)^{-1}(D_2) \mid \mathcal{G})(\omega) - \mathbb{P}((X, Y)^{-1}(D_1) \mid \mathcal{G})(\omega) \\
&= \mathbb{P}((X, Y)^{-1}(D_2 \setminus D_1) \mid \mathcal{G})(\omega)
\end{aligned}
\]

for \(\mathbb{P}|_{\mathcal{G}}\)-almost every \(\omega \in \Omega_0\), so \(D_2 \setminus D_1 \in \mathcal{D}\). Finally, let \((D_n)\) be an increasing sequence of sets in \(\mathcal{D}\), and let \(D := \bigcup_{n=1}^\infty D_n\). Then \(D^{Y(\omega)} = \bigcup_{n=1}^\infty D_n^{Y(\omega)}\) and \((X, Y)^{-1}(D) = \bigcup_{n=1}^\infty (X, Y)^{-1}(D_n)\), so that
\[
\begin{aligned}
P_\omega(D^{Y(\omega)}) &= \lim_{n\to\infty} P_\omega(D_n^{Y(\omega)}) = \lim_{n\to\infty} \mathbb{P}((X, Y)^{-1}(D_n) \mid \mathcal{G})(\omega) \\
&= \mathbb{P}((X, Y)^{-1}(D) \mid \mathcal{G})(\omega)
\end{aligned}
\]

for \(\mathbb{P}|_{\mathcal{G}}\)-almost every \(\omega \in \Omega_0\), where we have used the conditional monotone convergence theorem in the final equality (Dudley, 2002, Theorem 10.1.7). Thus, \(D \in \mathcal{D}\), and it follows from Dynkin's lemma that \(\mathcal{D} = \mathcal{A} \otimes \mathcal{B}\).

Finally, if \(C \in \mathcal{C}\), then \(D := \phi^{-1}(C) \in \mathcal{A} \otimes \mathcal{B}\), so that for \(\mathbb{P}|_{\mathcal{G}}\)- almost every \(\omega \in \Omega_0\),
\[
\begin{aligned}
P_\omega(\phi^{-1}(C)^{Y(\omega)})
&= P_\omega(D^{Y(\omega)}) = \mathbb{P}((X, Y)^{-1}(D) \mid \mathcal{G})(\omega) \\
&= \mathbb{P}((X, Y)^{-1}(D) \mid \mathcal{G})(\omega) \cdot \mathbb{1}_{\Omega_0}(\omega) = \mathbb{P}((X, Y)^{-1}(D) \cap \Omega_0 \mid \mathcal{G})(\omega) \\
&= \mathbb{P}(Z^{-1}(C) \cap \Omega_0 \mid \mathcal{G})(\omega) = \mathbb{P}(Z^{-1}(C) \mid \mathcal{G})(\omega),
\end{aligned}
\]
as required, since \(\Omega_0 \in \mathcal{G}\).

- (c) 通过取 \(\Omega_0 = \Omega\)，直接从 (b) 得出。

The following useful result is a special case of Kallenberg (1997, Theorem 5.4) and can be derived using the definition of conditional expectation (Dudley, 2002, Problem 10.1.9), or alternatively using regular conditional distributions and standard measure-theoretic devices (similarly to the proofs of Lemma B.6(b) above and Dudley (2002, Theorem 10.2.5)).

### 引理 B.7.

Let \(X, Y\) be measurable functions from \((\Omega, \mathcal{F}, \mathbb{P})\) to measurable spaces \((\mathcal{X}, \mathcal{A}), (\mathcal{Y}, \mathcal{B})\) respectively, and let \(\phi: (\mathcal{X} \times \mathcal{Y}, \mathcal{A} \otimes \mathcal{B}) \to \mathbb{R}\) be a measurable function satisfying \(\mathbb{E}(|\phi(X, Y)|) < \infty\). Let \(\mathcal{G} \subseteq \mathcal{F}\) be a \(\sigma\)-algebra, and suppose that \(Y\) is \(\mathcal{G}\)-measurable. If \(X\) has distribution \(Q\) on \((\mathcal{X}, \mathcal{A})\) and is independent of \(\mathcal{G}\), then \(\mathbb{E}(\phi(X, Y) \mid \mathcal{G})(\omega) = \int_{\mathcal{X}} \phi(x, Y(\omega)) \, dQ(x)\) for \(\mathbb{P}|_{\mathcal{G}}\)-almost every \(\omega \in \Omega\).

Next, for \(\sigma\)-algebras \(\mathcal{G}_1, \mathcal{G}_2, \mathcal{G}_3 \subseteq \mathcal{F}\), we say that \(\mathcal{G}_1\) and \(\mathcal{G}_2\) are *conditionally independent given* \(\mathcal{G}_3\), and write \(\mathcal{G}_1 \perp \mathcal{G}_2 \mid \mathcal{G}_3\), if \(\mathbb{P}(A_1 \cap A_2 \mid \mathcal{G}_3) = \mathbb{P}(A_1 \mid \mathcal{G}_3)\mathbb{P}(A_2 \mid \mathcal{G}_3)\) almost surely for all \(A_1 \in \mathcal{G}_1\) and \(A_2 \in \mathcal{G}_2\), or equivalently if \(\mathbb{P}(A_1 \mid \sigma(\mathcal{G}_2, \mathcal{G}_3)) = \mathbb{P}(A_1 \mid \mathcal{G}_3)\) almost surely for all \(A_1 \in \mathcal{G}_1\) (Kallenberg, 1997, Proposition 5.6). If this holds with \(\mathcal{G}_1 = \sigma(X)\) for some random variable \(X\), we also say that \(X\) and \(\mathcal{G}_2\) are conditionally independent given \(\mathcal{G}_3\), and write \(X \perp \mathcal{G}_2 \mid \mathcal{G}_3\) (and similarly for \(\mathcal{G}_2\) and \(\mathcal{G}_3\)). The following basic facts follow straightforwardly from the definition of conditional independence.

### 引理 B.8 (Kallenberg, 1997, Corollary 5.7(i)).

We have \(\mathcal{G}_1 \perp \mathcal{G}_2 \mid \mathcal{G}_3\) if and only if \(\sigma(\mathcal{G}_1, \mathcal{G}_3) \perp \mathcal{G}_2 \mid \mathcal{G}_3\).

### 引理 B.9.

Let \((\mathcal{X}, \mathcal{A})\) and \((\mathcal{Y}, \mathcal{B})\) be measurable spaces and let \(\mathcal{G} \subseteq \mathcal{F}\) be a \(\sigma\)-algebra.

- (a) For \(i = 1, 2\), let \(X_i: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A})\) and \(Y_i: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{Y}, \mathcal{B})\) be measurable functions such that \(X_i \perp Y_i \mid \mathcal{G}\). For \(E \in \mathcal{G}\), let \(X: (\Omega, \mathcal{F}, \mathbb{P}) \to (\mathcal{X}, \mathcal{A})\) be the measurable function satisfying \(X = X_1\) on \(E\) and \(X = X_2\) on \(E^c\), and define \(Y\) similarly. Then \(X \perp Y \mid \mathcal{G}\).

