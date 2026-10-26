$$\mathbb{E}_{M_*}[r^h|x^h,a^h]=R^h_{M_*}(x^h,a^h).$$

We assume that $r^h+f_M^h(x^h,a^h)\in[0,1]$ and $f_M^1(x^1)\in[0,1]$. We also assume that there is a planning oracle that solves the optimal policy $\pi_M$ and $Q$-function $f_M^h(x^h,a^h)$ for any given model $M\in\mathcal{M}$.

One advantage of model-based RL is that the completeness assumption is not required if the model Bellman operator $(\mathcal{T}_M^h f)(x^h,a^h)$ can be evaluated efficiently. In this case, we may simply compare the model value to $r^h+f^{h+1}(x^{h+1})$, which is an unbiased estimate of the true Bellman operator $(\mathcal{T}_{M*}^h f)(x^h,a^h)$. Using this observation, one may define the following loss function

$$L^h(M,M',x^h,a^h,r^h,x^{h+1})=\big((\mathcal{T}_M^h f_{M'})(x^h,a^h)-r^h-f_{M'}(x^{h+1})\big)^2,\qquad(18.16)$$

which we call value-targeted loss to be consistent with Ayoub et al. (2020). It is natural to require that a good model has a value-targeted loss that fits well on historic data. This allows us to define a version space for the models in $\mathcal{M}$. We can then apply the general principle of optimism as in Algorithm 17.4 and Algorithm 18.1. The resulting algorithm is presented in Algorithm 18.4. Since we do not need completeness, the analysis of the algorithm is a direct extension of Algorithm 17.4.

# Algorithm 18.4 Value-Targeted Loss UCB Algorithm

```
Input: $\lambda, T, \mathcal{M}$
1 Let $\mathcal{F}_0=\{f_0\}$
2 Let $\beta_0=0$
3 for $t=1,2,\dots,T$ do
4   Observe $x_t^1$
5   Let
    $M_t\in\arg\max_{M\in\mathcal{M}_{t-1}}f_M(x_t^1)$.
    Let $\pi_t=\pi_{M_t}$
6   Play policy $\pi_t$ and observe trajectory $(x_t,a_t,r_t)$
7   Let
    $\hat{M}_t=\arg\min_{M\in\mathcal{M}}\sum_{h=1}^H\sum_{s=1}^t L^h(M,M_s,x_s^h,a_s^h,r_s^h,x_s^{h+1})$, where $L^h(\cdot)$ is defined according to (18.16).
8   Define
    $\mathcal{M}_t=\{M\in\mathcal{M}:\sum_{h=1}^H\sum_{s=1}^t\big((\mathcal{T}_M^h f_{M_s})(x_s^h,a_s^h)-(\mathcal{T}_{M_t}^h f_{M_s})(x_s^h,a_s^h)\big)^2\le\beta_t^2\}$ with appropriately chosen $\beta_t$.
9 return randomly chosen $\pi_t$ from $t=1$ to $t=T$
```