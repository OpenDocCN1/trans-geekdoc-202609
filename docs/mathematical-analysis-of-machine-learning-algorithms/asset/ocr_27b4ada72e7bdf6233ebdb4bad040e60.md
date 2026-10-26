decomposition of (18.22). If we use $w(M_t,f_{M_t})$ instead of $w(M_t,f_{M_{S_t}})$, then the resulting method is equivalent to model-free linear MDP, as

$$\mathcal{E}^h(M_t,f_t,x^h,a^h)=\mathcal{E}^h(f_t,x^h,a^h),$$

based on (18.17). This decomposition leads to the same eluder coefficient for model-free linear MDP in Proposition 18.20. However, for model-based problems, we can also replace $L_s^h(M_t,M_*)$ on the right-hand side of Definition 18.39 by any upper bound. Therefore we can use the witness-loss upper bound,

$$\mathcal{E}^h(M_t,f_t,x^h,a^h)^2\leq \sup_{f\in\mathcal{F}}\mathcal{E}^h(M_t,f,x^h,a^h)^2,$$

to obtain the following result from Proposition 18.20. The proof is left as an exercise.

# **Proposition 18.54**  *Consider the model-based linear MDP in Definition 18.53. Assume that $\|w^h(M,f_M)-w^h(M_*,f_{M_*})\|_{\mathcal{H}^h}\leq B$, where $w^h(M,f_M)$ is defined in (18.22), then*

$$\mathrm{EC}_{Q\text{-}\mathrm{Hel}}(1,\mathcal{M},T)\leq \mathrm{EC}_{Q\text{-}\mathrm{Wit}}(1,\mathcal{M},T)\leq 2\sum_{h=1}^{H}\operatorname{entro}\left(\frac{1}{B^2T},\psi^h(\mathcal{X}\times\mathcal{A})\right).$$

Proposition 18.54 implies that we can apply Algorithm 18.5 to solve the model-based linear MDP problem. Assume that each $\mathcal{H}^h$ is $d$-dimensional, then

$$\mathrm{EC}_{Q\text{-}\mathrm{Hel}}(1,\mathcal{M},T)=\widetilde{O}(Hd),$$

and we obtain the following regret bound from Theorem 18.47 with optimal $\lambda$:

$$O\left(\sqrt{T\,H d\,\kappa(\cdot)}\right).$$

We note that $\kappa(\cdot)$ behaves like an entropy number. For a finite function class of $M$ members, $\kappa(\cdot)\leq\ln M$. For function class with infinite members, similar results can be obtained by choosing a small Hellinger-ball for the model class, with a small constant added to each conditional probability model to avoid negative infinity model log-likelihood.

# 18.8 Model-Based $V$-type Bellman Eluder Coefficient

We have shown in Section 18.4 that in the model-free setting, it is possible to learn an MDP that has an unknown Bellman factorization with a nonlinear $Q$-function class that is linearly embeddable. If we assume that the transition probability is known, then it is also possible to learn similar models using a model-based approach. To motivate this approach, we may consider the model-based approach to linear MDP. In the $Q$-type approach, we have to assume that the model can be represented linearly with the true linear map of the underlying MDP. In the $V$-type approach, this is not necessary. Similar to the model-free approach in Definition 18.27, we can introduce the following definition.