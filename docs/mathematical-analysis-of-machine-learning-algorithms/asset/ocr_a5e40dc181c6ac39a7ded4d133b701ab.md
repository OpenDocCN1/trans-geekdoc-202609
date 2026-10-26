Now let $\bar{\phi}(z)=\inf_w \phi(w,z)+0.5M$. We know that $|\phi(w,z)-\bar{\phi}(z)|\le 0.5M$. Therefore

$$\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(\mathcal{S}'_n),z)-\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(\mathcal{S}_n),z)$$
$$=\mathbb{E}_{w\sim p(\cdot|\mathcal{S}_n)}\left(\frac{p(w|\mathcal{S}'_n)}{p(w|\mathcal{S}_n)}-1\right)[\phi(w,z)-\bar{\phi}(z)]$$
$$\le\mathbb{E}_{w\sim p(\cdot|\mathcal{S}_n)}\left|\frac{p(w|\mathcal{S}'_n)}{p(w|\mathcal{S}_n)}-1\right||\phi(w,z)-\bar{\phi}(z)|$$
$$\le(e^{2\beta M}-1)\cdot0.5M.$$

This proves the desired result.

# Example 7.18

Consider the Gibbs algorithm $\mathcal{A}$ described in (7.9) with bounded loss as in Theorem 7.17. We have the following expected oracle inequality:

$$\mathbb{E}_{\mathcal{S}_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(\mathcal{S}_n),\mathcal{D})$$
$$\le\mathbb{E}_{\mathcal{S}_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(\mathcal{S}_n),\mathcal{S}_n)+0.5(e^{2\beta M}-1)M$$
$$\le\mathbb{E}_{\mathcal{S}_n}\left[\mathbb{E}_{w\sim p(\cdot|\mathcal{S}_n)}\phi(w,\mathcal{S}_n)+\frac{1}{\beta n}\mathrm{KL}(p(\cdot|\mathcal{S}_n)||p_0)\right]+0.5(e^{2\beta M}-1)M$$
$$\le\inf_{p\in\Delta(\Omega)}\left[\mathbb{E}_{w\sim p}\phi(w,\mathcal{D})+\frac{1}{\beta n}\mathrm{KL}(p||p_0)\right]+0.5(e^{2\beta M}-1)M.$$

The first inequality followed from Theorem 7.2 and Theorem 7.17. The second inequality used non negativity of KL-divergence. The last inequality used the fact that the Gibbs distribution minimizes (7.10).

We can also prove a more refined result using leave-one-out stability as follows.

# Theorem 7.19

Consider the Gibbs algorithm $\mathcal{A}$ described in (7.9). If for all $z$: $\sup_{w\in\Omega}\phi(w,z)-\inf_{w\in\Omega}\phi(w,z)\le M$, then $\mathcal{A}$ is
$$\epsilon(Z_{n+1},\mathcal{S}_{n+1})=\beta e^{\beta M}\mathrm{Var}_{\mathcal{A}}[\phi(\mathcal{A}(\mathcal{S}_n),Z_{n+1})]$$
leave-one-out stable. If the loss function $\phi$ satisfies the variance condition (3.13), which we restate as
$$\mathrm{Var}_{Z\sim\mathcal{D}}[\phi(w,Z)]\le c_0^2+c_1[\phi(w,\mathcal{D})],$$
then for $\beta>0$ such that $c_2=1-c_1\beta e^{\beta M}>0$, we have
$$c_2\mathbb{E}_{\mathcal{S}_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(\mathcal{S}_n),\mathcal{D})\le\inf_{p\in\Delta(\Omega)}\left[\mathbb{E}_{w\sim p}\phi(w,\mathcal{D})+\frac{1}{\beta(n+1)}\mathrm{KL}(p||p_0)\right]+\beta e^{\beta M}c_0^2$$
$$\le\inf_{w\in\Omega}\phi(w,\mathcal{D})+\inf_{\epsilon>0}\left[\epsilon-\frac{\ln p_0(\Omega(\epsilon))}{\beta(n+1)}\right]+\beta e^{\beta M}c_0^2,$$
where $\Omega(\epsilon)=\{w\in\Omega:\phi(w,\mathcal{D})\le\inf_w\phi(w,\mathcal{D})+\epsilon\}.$
Proof Let $\bar{\mathcal{A}}(\mathcal{S}_{n+1},Z_{n+1})$ be the Gibbs algorithm with posterior $p(\cdot|\mathcal{S}_{n+1})$. Let $\hat{\phi}(w,Z_{n+1})=\phi(w,Z_{n+1})-\mathbb{E}_{w'\sim p(\cdot|\mathcal{S}_n)}\phi(w',Z_{n+1})$. Then $|\hat{\phi}(w,Z_{n+1})|\le M$. Note