implies that

$$r \le e_n^{h'}(\mathcal{F},\mathcal{D}) + 0.5r'.$$

Let $r' \to \max(r,\alpha b_0)$, and we obtain either $r \le \alpha b_0$, or

$$r \le e_n^{h'}(\mathcal{F},\mathcal{D}) + 0.5r.$$

Therefore

$$r \le \max\left(2e_n^{h'}(\mathcal{F},\mathcal{D}),\alpha b_0\right).$$

This implies the desired bound. □

By using the concept of rate function, we can obtain the following uniform convergence result from Corollary 6.34, where we assume that the localization function satisfies a variance condition similar to (3.13).

# **Theorem 6.41**  *Consider* $\mathcal{F}$, $\mathcal{D}$, and iid samples $S_n=\{Z_1,\ldots,Z_n\}\sim\mathcal{D}$. Let $f(\mathcal{D})=\mathbb{E}_{Z\sim\mathcal{D}}[f(Z)]$, and $f(S_n)=n^{-1}\sum_{i=1}^n f(Z_i)$. Assume that for all $f\in\mathcal{F}$,

$$\operatorname{Var}_{\mathcal{D}}[f(Z)]\le c_0^2+c_1h(f)$$

for some $c_0,c_1,h(\cdot)>0$. Assume also that $\mathcal{F}$ is bounded: $\sup_{z,z'}|f(\mathcal{D})-f(z')|<M$ for all $f\in\mathcal{F}$. Then with probability at least $1-\delta$ over $S_n$, $\forall f\in\mathcal{F}$ and $\forall\alpha>0$,

$$f(\mathcal{D})\le f(S_n)+5\alpha h(f)+5r_0+\sqrt{\frac{2c_0^2\ln(1/\delta)}{n}}+\frac{(3c_1+4\alpha M)\ln(1/\delta)}{3\alpha n},$$

where

$$r_0=\bar r_n^h(\alpha,\mathcal{F},\mathcal{D})+\alpha\inf_{f\in\mathcal{F}}h(f)+\sqrt{\frac{2c_0^2}{n}+\frac{(3c_1+4\alpha M)}{3\alpha n}}$$

$$\le 2e_n^{h'}(\alpha,\mathcal{F},\mathcal{D})+2\alpha\inf_{f\in\mathcal{F}}h(f)+\sqrt{\frac{2c_0^2}{n}+\frac{(3c_1+4\alpha M)}{3\alpha n}},$$

with $h'(f,S_n)=0.5\alpha h(f)$.

*Proof*  The inequality for $r_0$ is a direct consequence of Proposition 6.40. We will now use a peeling argument. For $\ell=1,2,\ldots$, let $r_\ell=\alpha^{-1}(1.5)^{\ell-1}r_0$. Define $\mathcal{F}_\ell=\{f\in\mathcal{F}:h(f)\le r_\ell\}$. It follows that

$$\sup_{f\in\mathcal{F}_\ell}\operatorname{Var}_{\mathcal{D}}[f(Z)]\le c_0^2+c_1h(f)\le c_0^2+c_1r_\ell.$$

For each $\ell\ge1$, let $\delta_\ell=4\delta/((\ell+3)(\ell+4))$. We have with probability $1-\delta_\ell$,