Proof We prove this result by induction. The result holds for n = 0. Assume that the result holds for n = k, then when n = k + 1, we have

\[ \mathbb{E}_{\sigma_1,\dots,\sigma_{k+1}} \sup_w \left[ c(w) + \sum_{i=1}^{k+1} \sigma_i g_i(w) \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{g_{k+1}(w_1)-g_{k+1}(w_2)}{2} \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{|g_{k+1}(w_1)-g_{k+1}(w_2)|}{2} \right] \]
\[ \le \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{|\tilde g_{k+1}(w_1)-\tilde g_{k+1}(w_2)|}{2} \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \sup_{w_1,w_2} \left[ \frac{c(w_1)+c(w_2)}{2} + \sum_{i=1}^{k} \sigma_i \frac{g_i(w_1)+g_i(w_2)}{2} + \frac{\tilde g_{k+1}(w_1)-\tilde g_{k+1}(w_2)}{2} \right] \]
\[ = \mathbb{E}_{\sigma_1,\dots,\sigma_k} \mathbb{E}_{\sigma_{k+1}} \sup_w \left[ c(w) + \sigma_{k+1} \tilde g_{k+1}(w) + \sum_{i=1}^{k} \sigma_i g_i(w) \right] \]
\[ \le \mathbb{E}_{\sigma_1,\dots,\sigma_k} \mathbb{E}_{\sigma_{k+1}} \sup_w \left[ c(w) + \sigma_{k+1} \tilde g_{k+1}(w) + \sum_{i=1}^{k} \sigma_i \tilde g_i(w) \right]. \]

The last inequality follows from the induction hypothesis.

The following example shows an application of Theorem 6.28.

# Example 6.30

Consider binary classification with y ∈ {±1}, and let ℱ = {f(w, x) = wᵀ ψ(x)} be the class of linear classifiers. Consider the smoothed classification loss function L(f(x), y) = min(1, max(0, 1−γ f(x) y)) for some γ > 0, as in Figure 6.1. Let 𝒢 = {L(f(w, x), y)}. Then L(f, y) is γ Lipschitz in f. Consider the regularizer in Example 6.12 with h(w) = h₀(w) = 0.5 λ ‖w‖₂² in (6.3). We obtain from Theorem 6.28,

\[ R^{h}(\mathcal{G}, \mathcal{S}_n) \le \gamma R^{h/\gamma}(\mathcal{F}, \mathcal{S}_n), \]

which implies that

\[ R^{h}(\mathcal{G}, \mathcal{S}_n) \le \frac{\gamma^{2}}{\lambda n^{2}} \sum_{i=1}^{n} \|\psi(X_i)\|_{2}^{2}. \]