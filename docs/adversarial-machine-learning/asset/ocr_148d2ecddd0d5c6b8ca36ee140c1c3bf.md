7.11 by $Q$ and $R$, and the target event in the theorem by $\mathbb{S}$.

$$ \mathbb{P} = \left\{ \left\| k - \hat{k} \right\|_{\infty, \mathcal{M}} < \min \left\{ 1, \frac{\epsilon^2}{2^2 \left( \Lambda + 2 \sqrt{(CL + \frac{\Lambda}{2}) \Lambda} \right)^2 } \right\} \right\} $$ 

$$ \mathbb{Q} = \left\{ \left\| f^* - \tilde{f} \right\|_{\infty, \mathcal{M}} \le \frac{\epsilon}{2} \right\} $$ 

$$ \mathbb{R} = \left\{ \left\| \hat{f}^* - \tilde{f} \right\|_\infty \le \frac{\epsilon}{2} \right\} $$ 

$$ \mathbb{S} = \left\{ \left\| f^* - \hat{f}^* \right\|_{\infty, \mathcal{M}} \le \epsilon \right\} . $$

The claim is a bound on $\text{Pr}(\mathbb{S})$. By the triangle inequality, events $\mathbb{Q}$ and $\mathbb{R}$ together imply $\mathbb{S}$. Second note that event $\mathbb{R}$ is independent of $\mathbb{P}$ and $\mathbb{Q}$. Thus $\text{Pr}(\mathbb{S} | \mathbb{P}) \ge \text{Pr}(\mathbb{Q} \cap \mathbb{R} | \mathbb{P}) = \text{Pr}(\mathbb{Q} | \mathbb{P}) \text{Pr}(\mathbb{R}) \ge 1 \cdot (1 - \delta/2)$, for sufficiently small $\lambda$. Finally Lemma 7.21 bounds $\text{Pr}(\mathbb{P})$: Provided that \(\hat{D} \ge 4(D + 2) \log_e \left( 2^9 (\sigma_p \text{diam}(\mathcal{M}))^2 / (\delta \theta(\epsilon)) \right) / \theta(\epsilon)\) where \(\theta(\epsilon) = \min \left\{ 1, \epsilon^4 / \left[ 2 \left( \Lambda + 2 \sqrt{(CL + \Lambda/2) \Lambda} \right) \right]^4 \right\}\) we have $\text{Pr}(\mathbb{P}) \ge 1 - \delta/2$. Together this yields $\text{Pr}(\mathbb{S}) = \text{Pr}(\mathbb{S} | \mathbb{P}) \text{Pr}(\mathbb{P}) \ge (1 - \delta/2)^2 \ge 1 - \delta$.

# 7.7 Bounds on Optimal Differential Privacy

In this section we delve deeper into the special case of the hinge loss. We begin by plugging hinge loss $\ell(y, \hat{y}) = (1 - y\hat{y})_+$ into the main results on privacy and utility of the previous sections. Similar computations can be done for other convex losses; we select hinge loss because it is the most common among SVM classification losses. We then proceed to combine the obtained privacy and utility bounds into an upper bound on the optimal differential privacy for SVM learning with the hinge loss. This notion, while presented here specifically for the SVM, in general quantifies the highest level of privacy achievable over all $(\epsilon, \delta)$-useful mechanisms with respect to a target mechanism $M$.

**DEFINITION 7.22** For $\epsilon, C > 0, \delta \in (0, 1), N > 1$, loss function $\ell(y, \hat{y})$ convex in $\hat{y}$, and kernel $k$, the *optimal differential privacy for the SVM* is the function

$$ \beta^*(\epsilon, \delta, C, N, \ell, k) = \inf_{\hat{M} \in \mathcal{I}} \sup_{(\mathbb{D}^{(1)}, \mathbb{D}^{(2)}) \in \mathcal{D}} \sup_{t \in \mathcal{T}_{\hat{M}}} \log \left( \frac{\text{Pr}\left(\hat{M}(\mathbb{D}^{(1)}) = t\right)}{\text{Pr}\left(\hat{M}(\mathbb{D}^{(2)}) = t\right)} \right), $$

where $\mathcal{I}$ is the set of all $(\epsilon, \delta)$-useful mechanisms with respect to the SVM with parameter $C$, loss $\ell$, and kernel $k$; and $\mathcal{D}$ is the set of all pairs of neighboring databases with $N$ entries.