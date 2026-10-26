$$\hat{w}' = \sum_{t=1}^{T} \frac{2(t+1)}{T^2+3T} w_{t-1},$$

*then*

$$\mathbb{E}_{S_T}\mathbb{E}_{D}\phi(\hat{w}',Z)+\frac{\lambda}{2}\|\hat{w}'\|_2^2 \leq \inf_{w\in\Omega}\left[\mathbb{E}_{D}\phi(w,Z)+\frac{\lambda}{2}\|w\|^2\right]+\frac{2[G+\lambda d(\Omega)]^2}{\lambda(T+3)}.$$

*Proof* Note that $\ell_t(w)$ is $\lambda$-strongly convex in $w$. Moreover, it is $G+\lambda d(\Omega)$ Lipschitz. We simply take expectation and apply Jensen’s inequality to obtain the desired bounds.

In the stochastic setting, the online gradient algorithm is often referred to as the *stochastic gradient descent* algorithm (SGD). The results in Corollary 14.13 directly imply both a generalization bound and a convergence bound for SGD. In order to obtain concentration bounds, or obtain an oracle inequality without the assumption of $d(\Omega)$, one can apply the technique of sample dependent bounds similar to the analysis of kernel methods as in Corollary 9.26 and Corollary 9.27. If we restrict $\mathcal{D}$ to the uniform distribution of training data, then Corollary 14.13 implies a convergence of SGD to a minimizer of the training loss. However, once we go through the data more than once, Corollary 14.13 cannot be used to obtain a generalization bound for SGD. In this case, we have to combine the convergence analysis of Corollary 14.13 and the stability analysis of Theorem 7.14 to obtain a generalization bound if we run SGD multiple times over the data. We leave the resulting bound as an exercise. Moreover, some recent work studied the generalization of SGD (and the related SGLD method) using the mutual information-based generalization bound of Corollary 10.22.

# 14.5 Online Nonconvex Optimization

Consider the online optimization problem with a nonconvex but bounded loss function $\ell_t(w)$. In this case, in order to obtain a meaningful online regret bound, it is necessary to consider randomized algorithms. We have the following negative result for any deterministic algorithm.

**Proposition 14.14** *Consider $\Omega=\{w_0,w_1,\ldots,w_T\}$ that contains $T$ members. Given any deterministic online learning algorithm $\mathcal{A}$ that returns a model parameter $w_{t-1}$ based on $\{\ell_s:s=1,\ldots,t-1\}$, there exists a loss sequence $\ell_t(w)\in\{0,1\}$ so that*

$$\inf_w \sum_{t=1}^{T}\ell_t(w)=0, \qquad \sum_{t=1}^{T}\ell_t(w_{t-1})=T.$$

*Proof* We simply pick the loss at each time $t$ so that

$$\ell_t(w)=\mathbf{1}(w=w_{t-1}).$$