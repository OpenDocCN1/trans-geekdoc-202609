To obtain the corresponding \(\tilde{P}_\omega\) from the conditional distribution of \(\phi(X,Y)\) given \(\mathcal{G}\), Lemma B.6(b) tells us that we can take \(\tilde{P}_\omega\) to be the distribution of \(\phi(U, y)\), where \(U \sim \mu\) and \(y := Y(\omega)\). In essence, the reason for this is that since \(Y\) is \(\mathcal{G}\)-measurable, we can think of \(Y\) as being ‘fixed’ once we have conditioned on \(\mathcal{G}\).

Proof. (a) The fact that \(R_\omega(\cdot)\) is a probability measure on \(\mathcal{A}\) for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega\) follows immediately from the corresponding facts for \(P_\omega(\cdot)\) and \(Q_\omega(\cdot)\). For each \(A \in \mathcal{A}\), the map \(\omega \mapsto R_\omega(A)\) is a composition of \(\mathcal{G}\)-measurable functions (since \(E \in \mathcal{G}\) by assumption), so is \(\mathcal{G}\)-measurable.

For \(A \in \mathcal{A}\), let \(\chi_A: \mathcal{X} \to \{0, 1\}\) denote the indicator function of \(A\).

Then

```
\(\chi_A \circ X = (\chi_A \circ X_1)\mathbb{1}_E + (\chi_A \circ X_2)\mathbb{1}_{E^c}.\)
```

Since \(\mathbb{1}_E\) and \(\mathbb{1}_{E^c}\) are \(\mathcal{G}\)-measurable, it follows that

```
\(\begin{aligned} \mathbb{P}(X^{-1}(A) \mid \mathcal{G})(\omega) \\ = \mathbb{E}((\chi_A \circ X_1)\mathbb{1}_E \mid \mathcal{G})(\omega) + \mathbb{E}((\chi_A \circ X_2)\mathbb{1}_{E^c} \mid \mathcal{G})(\omega) \\ = \mathbb{E}(\chi_A \circ X_1 \mid \mathcal{G})(\omega)\mathbb{1}_E(\omega) + \mathbb{E}((\chi_A \circ X_2) \mid \mathcal{G})(\omega)\mathbb{1}_{E^c}(\omega) \\ = P_\omega(A)\mathbb{1}_E(\omega) + Q_\omega(A)\mathbb{1}_{E^c}(\omega) = R_\omega(A) \end{aligned}\)
```

for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega\), as required.

(b) This can be deduced from Kallenberg (1997, Theorem 5.4) and part (a) above, but we give a direct proof here for completeness. Note that for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega_0\), the set function \(\tilde{P}_\omega\) is the push-forward (image measure) of \(P_\omega\) induced by the measurable map \(x \mapsto \phi \circ \iota_{Y(\omega)}(x)\) from \((\mathcal{X}, \mathcal{A})\) to \((\mathcal{Z}, \mathcal{C})\); thus, \(\tilde{P}_\omega\) is indeed a probability measure for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega_0\).

Now let \(\mathcal{D}\) denote the collection of all \(D \in \mathcal{A} \otimes \mathcal{B}\) for which \(\omega \mapsto P_\omega(D^{Y(\omega)})\) is \(\mathcal{G}\)-measurable and \(P_\omega(D^{Y(\omega)}) = \mathbb{P}((X,Y)^{-1}(D) \mid \mathcal{G})(\omega)\) for \(\mathbb{P}|_\mathcal{G}\)-almost every \(\omega \in \Omega_0\). If \(D = A \times B\) for some \(A \in \mathcal{A}\) and \(B \in \mathcal{B}\), then \(D^{Y(\omega)} = A\) if \(Y(\omega) \in B\), and \(D^{Y(\omega)} = \emptyset\) if