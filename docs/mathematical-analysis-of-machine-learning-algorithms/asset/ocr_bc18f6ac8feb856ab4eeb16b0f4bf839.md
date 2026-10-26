$\mathbb{E}_{X\sim\mathcal{D}_X}(f(X)-f'(X))^2 \ge 2\sigma^2 KL(\mathcal{D}_f||\mathcal{D}_{f'}),$

where $\mathcal{D}_f$ is the distribution of $(X,Y)$ when $f_{\mathcal{D}}=f$. If $\mathcal{F}$ contains $N$ functions $f_1,\dots,f_N$ such that

$\ln N \ge \ln 4 + n\sigma^{-2} \sup_{j,k} \mathbb{E}_{X\sim\mathcal{D}}(f_j(X)-f_k(X))^2,$

then

$r_n(\mathcal{P},Q_{LS}) \ge 0.125 \inf_{j\neq k} \mathbb{E}_{X\sim\mathcal{D}_X}(f_j(X)-f_k(X))^2.$

Proof Define $Q(f,f') = \mathbb{E}_{X\sim\mathcal{D}}(f(X)-f'(X))^2$. Note that for each $f \in \mathcal{F}$, we associate a $\mathcal{D}_f \in \mathcal{P}=\{\mathcal{D}_f:f\in\mathcal{F}\}$. We also let $\epsilon = 0.25\min_{j\neq k}Q(f_j,f_k)$, and it can be checked that for all $j\neq k$,

$\max(Q(f,f_j),Q(f,f_k)) \ge (Q(f,f_j)+Q(f,f_k))/2 \ge Q(f_j,f_k)/4 \ge \epsilon.$

This means that we can take $m=1$, and obtain the theorem as a direct consequence of Theorem 12.15.

The following result implies that the condition of Theorem 12.17 holds for Gaussian noise.

# **Proposition 12.18** *Consider $\mathcal{D}_f(X,Y)$ so that $X \sim \mathcal{D}_X$ is identical for all $f \in \mathcal{F}$, and $Y \sim N(f(X),\sigma^2)$ for some constant $\sigma>0$. Then*

$\mathbb{E}_{X\sim\mathcal{D}_X}(f(X)-f'(X))^2 = 2\sigma^2 KL(\mathcal{D}_f||\mathcal{D}_{f'}).$

Proof We consider a distribution $\mathcal{D}$ over $Z=(X,Y)$ associated with each $f\in\mathcal{F}$, with density defined as

$p_{\mathcal{D}}(Z)=p_{\mathcal{D}_X}(X)\,p_{N(0,1)}((Y-f(X))/\sigma),$

where $p_{\mathcal{D}_X}(X)$ is the density of $X\sim\mathcal{D}_X$ and $p_{N(0,1)}$ is the density of standard normal distribution. Using this notation, we have

$KL(\mathcal{D}_{\hat f}||\mathcal{D}_f)=\frac{\mathbb{E}_X(\hat f(X)-f(X))^2}{2\sigma^2}.$

This proves the desired result.

Similar results can also be obtained for other noise models such as Bernoulli noise, where $Y\in\{0,1\}$.

# **Proposition 12.19** *Assume that $Y\in\{0,1\}$ such that*

$\mathbb{E}[Y|X]=f(X)$

for some $f\in\mathcal{F}$, and let $\mathcal{D}_f(Z)$ be the distribution of $Z=(X,Y)$. If there exists $c\in(0,0.5)$, and for all $f\in\mathcal{F}$ and $X:f(X)\in[c,1-c]$, then there exists $\sigma>0$ such that for all $f,f'\in F$,

$\mathbb{E}_{X\sim\mathcal{D}_X}(f(X)-f'(X))^2 \ge 2\sigma^2 KL(\mathcal{D}_f||\mathcal{D}_{f'}).$