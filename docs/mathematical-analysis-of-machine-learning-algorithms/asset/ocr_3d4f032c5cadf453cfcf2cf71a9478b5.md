Another method that is closely related to the Gibbs algorithm is model aggregation, studied in Section 15.3. The generalization bound there implies that using model aggregation on a sieve $\mathcal{F}_n = \{f_1,\dots,f_N\}$, with $N = M(\epsilon,\mathcal{F},L_2(\mathcal{D}_X))$, we have

$\mathbb{E}_{S_n} Q_{\mathrm{LS}}(\hat f,\mathcal{D}) = O\Big(\inf_j Q_{\mathrm{LS}}(f_j,\mathcal{D}) + n^{-1}\ln M(\epsilon,\mathcal{F},L_2(\mathcal{D}_X))\Big)$.

This achieves the same rate as that of Proposition 12.21. It follows that the exponential aggregation algorithm is also an optimal algorithm for least squares regression.

# 12.5 Minimax Analysis for Density Estimation

Assume that we are given a family of conditional distributions

$\mathcal{F} = \{p(Y|X) : p \in \mathcal{F}\}$

and the true conditional distribution $p_{\mathcal{D}} \in \mathcal{F}$. Similar to Section 12.4, we assume that all conditional densities share a marginal distribution $\mathcal{D}_X$ on $X$ (which the learning algorithm does not need to know). The joint distribution is $\mathcal{P} = \{p(X,Y)=p_{\mathcal{D}_X}(X)p(Y|X) : p \in \mathcal{F}\}$.

Given any $p \in \mathcal{F}$, we are interested in minimizing its squared Hellinger distance to the true distribution

$Q_H(p,\mathcal{D}) = H_{\mathcal{D}_X}(p||p_{\mathcal{D}})^2 = \mathbb{E}_{X\sim\mathcal{D}_X} H(p(\cdot|X)||p_{\mathcal{D}}(\cdot|X))^2.$

Here $H_{\mathcal{D}_X}$ is the Hellinger distance between the joint probability $p_{\mathcal{D}_X}(X)p(Y|X) \in \mathcal{P}$. We focus on the case that there exists $c_{\mathcal{F}} > 0$ so that for all $p,p' \in \mathcal{F}$

$\mathbb{E}_{X\sim\mathcal{D}_X} \mathrm{KL}(p(\cdot|X)||p'(\cdot|X)) \le c_{\mathcal{F}} H_{\mathcal{D}_X}(p||p')^2. \tag{12.2}$

For example, this condition holds if $\ln p(Y|X)$ is bounded.

The following result is a direct consequence of Theorem 12.15. The proof is similar to that of Theorem 12.17, and we leave it as an exercise.

**Theorem 12.24** *Consider the conditional density estimation problem with $X \sim \mathcal{D}_X$, and assume that the true conditional probability is given by*

$$p_{\mathcal{D}}(Y|X) \in \mathcal{F}.$$

*Assume that (12.2) holds. If $\mathcal{F}$ contains $N$ conditional densities $p_1,\dots,p_N$ such that*

$$\ln N \ge \ln 4 + 2c_{\mathcal{F}} \sup_{j,k} H_{\mathcal{D}_X}(p_j||p_k)^2,$$

*then*

$$r_n(\mathcal{P},Q_H) \ge 0.125 \inf_{j\neq k} H_{\mathcal{D}_X}(p_j||p_k)^2.$$