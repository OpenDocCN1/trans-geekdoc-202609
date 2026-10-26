It follows that for any w ∈ [0,1], if we let w_j be the smallest j such that w_j ≥ w, then we have φ_j(z) = 0 ≤ φ(w,z) when x ∈ [w_j − ε, w_j], and φ_j(z) = φ(w,z) otherwise, where z = (x,y). Moreover,

$$\mathbb{E}_{Z\sim\mathcal{D}}[\phi_j(Z)-\phi(w,Z)] = \mathbb{E}_{X\in[w_j-\epsilon,w_j]}[0-\phi(w,Z)] \ge -\epsilon.$$

This means that {φ_j(z)} is an ε-lower bracketing cover of 𝒢, and thus

$$N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D})) \le 1+\epsilon^{-1}.$$

# Oracle inequalities

We have (by picking ε = 2/n):

$$\inf_{\epsilon>0}\left[\epsilon + \sqrt{\frac{2\ln(2N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D}))/\delta)}{n}}\right] \le \frac{2}{n} + \sqrt{\frac{2\ln((n+2)/\delta)}{n}}.$$

This implies the following additive oracle inequality from Corollary 3.15 with φ(w,z)=L(f(w,x),y). With probability at least 1−δ,

$$\mathbb{E}_{(X,Y)\sim\mathcal{D}}L(f(\hat w,X),Y) \le (1-p)+\frac{2}{n}+\sqrt{\frac{2\ln((n+2)/\delta)}{n}}.$$

In addition, we have (by picking ε = 2/n)

$$\inf_{\epsilon>0}\left[(1-\gamma)\epsilon + \frac{(\gamma+2)\ln(2N_{LB}(\epsilon,\mathcal{G},L_1(\mathcal{D}))/\delta)}{2\gamma n}\right] \le \frac{2(1-\gamma)}{n} + \frac{(\gamma+2)\ln((n+2)/\delta)}{2\gamma n}.$$

This implies the following multiplicative oracle inequality from Corollary 3.15 with φ(w,z)=L(f(w,x),y). With probability at least 1−δ, for all γ∈(0,1),

$$\mathbb{E}_{(X,Y)\sim\mathcal{D}}L(f(\hat w,X),Y) \le \frac{1+\gamma}{1-\gamma}(1-p)+\frac{2}{n}+\frac{(\gamma+2)\ln((n+2)/\delta)}{2\gamma(1-\gamma)n}.$$

The multiplicative bound is superior to the additive bound when the Bayes error is small, such as when p = 1. In this case, the multiplicative bound implies a convergence rate of ln n / n instead of √{ln n / n} from the additive form.

# 3.6 Uniform Bernstein’s Inequality

In this section, we show that better bounds can be obtained with Bernstein’s inequality under the following condition.

Definition 3.16 (Variance Condition) Given a function class 𝒢, we say it satisfies the variance condition if there exists c₀, c₁ > 0 such that for all φ(z) ∈ 𝒢,

$$\operatorname{Var}_{Z\sim\mathcal{D}}(\phi(Z)) \le c_0^2 + c_1\mathbb{E}_{Z\sim\mathcal{D}}\phi(Z), \tag{3.13}$$

where we require that $\mathbb{E}_{Z\sim\mathcal{D}}\phi(Z) \ge -c_0^2/c_1$ for all $\phi \in \mathcal{G}$.