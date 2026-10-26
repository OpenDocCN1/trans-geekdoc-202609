# **Theorem 18.43**

Assume that Assumption 18.36 holds. Consider function class 𝓕 = {fʰ(M′, xʰ, aʰ): 𝓜 × 𝓧 × 𝓐 → ℝ} that contains {𝓔ʰ(M, ·, ·, ·): M ∈ 𝓜}. Assume that in Algorithm 18.4, we set

$$\beta_t^2 \ge \inf_{\epsilon>0}\left[4\epsilon tH\left(1+4\epsilon\right)+3\ln\left(2\mathcal{N}(\epsilon,\mathcal{F},\|\cdot\|_\infty)/\delta\right)\right].$$

where ‖f‖∞ = supₘ′,ₓʰ,ₐʰ |fʰ(M′, xʰ, aʰ)|. Then

$$\mathbb{E}\sum_{t=2}^{T}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right]\leq \delta HT+\sqrt{d\left(\epsilon HT+\delta HT^2+4\sum_{t=2}^{T}\beta_{t-1}^2\right)},$$

where Vᵢₜ¹ is the true value function of policy πₜ, and d = ECQ−VT(ε, 𝓜, T).

# **Proof.**

Let fₜ = f_{Mₜ}. For t ≥ 2, we have

$$\begin{aligned} V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1) &= V_*^1(x_t)-f_t(x_t^1)+f_t(x_t^1)-V_{\pi_t}^1(x_t^1) \\ &\leq \mathbf{1}(M_*\notin\mathcal{M}_{t-1})+f_t(x_t^1)-V_{\pi_t}^1(x_t^1) \\ &= \mathbf{1}(M_*\notin\mathcal{M}_{t-1})+\mathbb{E}_{(x_t,a_t,r_t)\sim\pi_t\mid x_t^1}\sum_{h=1}^{H}\mathcal{E}^h(M_t,x_t^h,a_t^h). \end{aligned}$$

The inequality used the fact that if M* ∈ 𝓜ₜ₋₁, then fₜ(xₜ¹) = max_{M∈𝓜ₜ₋₁} f(xₜ¹) ≥ V*¹(xₜ); if M* ∉ 𝓜ₜ₋₁, then V*¹(xₜ) − fₜ(xₜ¹) ≤ 1. The second equality used Theorem 18.38.

Lemma 18.42 implies that Pr(M* ∈ 𝓜ₜ₋₁) ≥ 1 − δ. We have

$$\mathbb{E}\left[M_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right]\leq \delta+\mathbb{E}\sum_{h=1}^{H}\mathcal{E}^h(M_t,x_t^h,a_t^h).$$

We can now obtain

$$\mathbb{E}\sum_{t=2}^{T}\left[V_*^1(x_t^1)-V_{\pi_t}^1(x_t^1)\right]$$

$$\leq \mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\mathcal{E}^h(M_t,x_t^h,a_t^h)+\delta T$$

$$\leq \delta T+\sqrt{\operatorname{ECQ\text{-}VT}(\epsilon,\mathcal{M},T)\,\mathbb{E}\sum_{t=2}^{T}\sum_{h=1}^{H}\left(\epsilon+\sum_{s=1}^{t-1}\mathcal{E}^h(f_{M_s},x_s^h,a_s^h)^2\right)}$$

$$\leq \delta T+\sqrt{\operatorname{ECQ\text{-}VT}(\epsilon,\mathcal{M},T)\left(\epsilon HT+\delta HT^2+4\sum_{t=2}^{T}\beta_{t-1}^2\right)}.$$

The second inequality used Definition 18.39. The last inequality used the fact that when Pr(M* ∉ 𝓜ₜ₋₁) ≤ δ, and in this case 𝓔ʰ(fₜ, xₛʰ, aₛʰ)² ≤ 1; when M* ∈ 𝓜ₜ₋₁, we have