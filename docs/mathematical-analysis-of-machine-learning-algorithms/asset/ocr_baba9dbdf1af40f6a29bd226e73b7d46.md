Note that for any $q=[q_1,\ldots,q_d]\in B_1$, let $q^k\in Q$ so that $\|q-q^k\|\leq\epsilon$, then

$$\left[\mathbb{E}_{Z\sim\mathcal{D}}\left\|\sum_{j=1}^{d}q_j^k f_j(Z)-\sum_{j=1}^{d}q_j f_j(Z)\right\|^p\right]^{1/p}\leq\epsilon A.$$

Therefore $\left\{\sum_{j=1}^{d}q_j^k f_j:k=1,\ldots,N\right\}$ is an $\epsilon A$ $L_p$ cover of $\operatorname{CONV}(\mathcal{F})$. The result follows.

The result is linear in the dimension $d$. However, for high-dimensional problems, one would like to obtain a bound that is logarithmic in the dimensionality $d$. The following result gives such a bound for $L_2$ cover, but with a polynomial dependency on $1/\epsilon$ instead of logarithmic dependency on $1/\epsilon$.

# **Theorem 5.14**  *Consider any class $\mathcal{F}=\{f_1,\ldots,f_d\}$, and assume that for a distribution $\mathcal{D}$, $\sup_{f\in\mathcal{F}}\|f\|_{L_2(\mathcal{D})}\leq A$. Then*

$$\ln N(\epsilon,\operatorname{CONV}(\mathcal{F}),L_2(\mathcal{D}))\leq \left\lceil A^2/\epsilon^2\right\rceil\ln\left[e+ed\epsilon^2/A^2\right].$$

*Proof*  For simplicity, we assume that $A=1$. Given any $f=\sum_j\alpha_j f_j\in\operatorname{CONV}(\mathcal{F})$, with $\sum_j\alpha_j=1$ and $\alpha_j\geq 0$, we can regard $p_\alpha$ as a probability measure on $\{1,\ldots,d\}$ with $p_\alpha(j)=\alpha_j$ $(j=1,\ldots,d)$. Now, let $j_1,\ldots,j_k$ be $k$ iid samples from $p_\alpha$, then $f=\sum_j\alpha_jf_j=\mathbb{E}_{j_s}f_{j_s}$.

$$\begin{aligned}\mathbb{E}_{j_1,\ldots,j_k}\left\|\frac{1}{k}\sum_{s=1}^{k}f_{j_s}-f\right\|_{L_2(\mathcal{D})}^{2}&=\operatorname{Var}_{j_1,\ldots,j_k}\left(\left\|\frac{1}{k}\sum_{s=1}^{k}f_{j_s}\right\|_{L_2(\mathcal{D})}\right)\\&=k^{-2}\sum_{s=1}^{k}\operatorname{Var}_{j_s}(\|f_{j_s}\|_{L_2(\mathcal{D})})\\&\leq k^{-2}\sum_{s=1}^{k}\mathbb{E}_{j_s}(\|f_{j_s}\|_{L_2(\mathcal{D})}^{2})\leq 1/k.$$\end{aligned}$$

It means that there exists $j_1,\ldots,j_k$ such that

$$\left\|\frac{1}{k}\sum_{s=1}^{k}f_{j_s}-f\right\|_{L_2(\mathcal{D})}\leq 1/\sqrt{k}.$$

Now, consider

$$Q_k=\left\{\frac{1}{k}\sum_{j=1}^{d}n_jf_j:\sum_{j=1}^{d}n_j=k;\ n_j\geq 0\right\}.$$

Since $k^{-1}\sum_{s=1}^{k}f_{j_s}\in Q_k$, we know that $Q_k$ is an $1/\sqrt{k}$ cover of $\operatorname{CONV}(\mathcal{F})$. Take $k=\lceil1/\epsilon^2\rceil$, we know that $Q_k$ is an $\epsilon$ cover. Moreover, since

$$|Q_k|\leq {d+k-1\choose k}\leq e^k(1+d/k)^k,$$

we obtain the bound in the theorem.