where ∇\bar{φ}(w,·) is the gradient with respect to w. Since

\bar{φ}(\mathcal{A}(\mathcal{S}_n), \mathcal{S}_{n+1}) = \frac{n}{n+1}\bar{φ}(\mathcal{A}(\mathcal{S}_n), \mathcal{S}_n) + \frac{1}{n+1}φ(\mathcal{A}(\mathcal{S}_n), Z_{n+1}).

It follows that

∇\bar{φ}(\mathcal{A}(\mathcal{S}_n), \mathcal{S}_{n+1})^\top (\bar{\mathcal{A}}(\mathcal{S}_{n+1}) - \mathcal{A}(\mathcal{S}_n)) = \left(\frac{n}{n+1}∇\bar{φ}(\mathcal{A}(\mathcal{S}_n), \mathcal{S}_n) + \frac{1}{n+1}∇φ(\mathcal{A}(\mathcal{S}_n), Z_{n+1})\right)^\top (\bar{\mathcal{A}}(\mathcal{S}_{n+1}) - \mathcal{A}(\mathcal{S}_n)) ≥ \frac{1}{n+1}∇φ(\mathcal{A}(\mathcal{S}_n), Z_{n+1})^\top (\bar{\mathcal{A}}(\mathcal{S}_{n+1}) - \mathcal{A}(\mathcal{S}_n)) ≥ -\frac{G(Z_{n+1})}{n+1}||\bar{\mathcal{A}}(\mathcal{S}_{n+1}) - \mathcal{A}(\mathcal{S}_n)||_2.

The first inequality used (7.4). The second inequality used the Lipschitz property of φ. Since \bar{\mathcal{A}}(\mathcal{S}_{n+1}) is the minimizer of \bar{φ}(w,\mathcal{S}_{n+1}) over w ∈ Ω, we obtain from Proposition A.8 that

||\mathcal{A}(\mathcal{S}_n) - \bar{\mathcal{A}}(\mathcal{S}_{n+1})||_2 ≤ \frac{G(Z_{n+1})}{λ(n+1)}.

It follows that

φ(\mathcal{A}(\mathcal{S}_n), Z_{n+1}) - φ(\bar{\mathcal{A}}(\mathcal{S}_{n+1}), Z_{n+1}) ≤ G(Z_{n+1})||\mathcal{A}(\mathcal{S}_n) - \bar{\mathcal{A}}(\mathcal{S}_{n+1})||_2 ≤ \frac{G(Z_{n+1})^2}{λ(n+1)}.

This proves the leave-one-out stability result. Similarly, we can prove the uniform stability result, which we leave as an exercise.

Now Theorem 7.7 implies that

𝔼_{\mathcal{S}_n} φ(\mathcal{A}(\mathcal{S}_n), \mathcal{D}) ≤ 𝔼_{\mathcal{S}_{n+1}} φ(\bar{\mathcal{A}}(\mathcal{S}_{n+1}), \mathcal{S}_{n+1}) + 𝔼_{\mathcal{S}_{n+1}} \frac{1}{n+1} \sum_{Z ∈ \mathcal{S}_{n+1}} \frac{G(Z)^2}{λ(n+1)} ≤ inf_w [𝔼_{\mathcal{S}_{n+1}} φ(w, \mathcal{S}_{n+1}) + h(w)] + 𝔼_{\mathcal{S}_{n+1}} \frac{1}{n+1} \sum_{Z ∈ \mathcal{S}_{n+1}} \frac{G(Z)^2}{λ(n+1)} = inf_w [φ(w, \mathcal{D}) + h(w)] + \frac{𝔼_Z G(Z)^2}{λ(n+1)}.

In the derivation, the inequality used the fact that \bar{\mathcal{A}}(\mathcal{S}_{n+1}) is the minimizer of the regularized empirical risk, and h(w) ≥ 0.

# Example 7.9 We consider the binary linear support vector machine (SVM) formulation with y ∈ {±1}, which employs the hinge loss

L(f(w,x), y) = max(1 - f(w,x) y, 0),   g(w) = \frac{λ}{2} ||w||_2^2,