
Finally, let us make a final comment concerning the Laplacian approximation. In the discussion above, our goal was to get an approximation of the integral (normalizing constant/evidence) of `p(y|M_i, θ)p(θ|M_i)`. However, if our interest were to approximate the PDF itself, we should involve the normalizing constant, which by the nature of the Gaussian function leads to

```
p(y|M_i, θ)p(θ|M_i) ≈ 1/((2π)^(K/2)|Σ|^(1/2)) exp( - 1/2 (θ - θ̂_MAP)^T Σ^(-1) (θ - θ̂_MAP) ).
```

This is also the case for the Laplacian approximation for any PDF `p(·)`.

### Remarks 12.2

*   **In the Bayesian approach**, one makes all the modeling assumptions explicit, and it is then left to the rules of probability theory to provide the answers. One does not have to “worry” about the choice of an optimizing criterion, where different criteria lead to different estimators, and there is not an objective, systematic way to decide which criterion is best. On the other hand, in the Bayesian approach one has to make sure to select the prior that explains the data in the best possible way.

*   **The choice of the prior PDF** is very critical in the performance of Bayesian methods and must be carried out in such a way to encapsulate prior knowledge as fully as possible. In practice, different alternatives can be adopted [3].

    1.  **Subjective priors**. According to this path, we choose the prior `p(θ)` to make the manipulation of the integration tractable, e.g., by employing conjugate priors (Section [3.11.1](#Chp003_65-117_B9780443292385000093.xhtml)) within the exponential family of PDFs. This family of PDFs will be presented in Section [12.8](#Chp012_583-634_B9780443292385000184.xhtml#s0075).

    2.  **Hierarchical priors**. Each one of the components of `θ[k]`, `k = 0, 2, …, K − 1`, of `θ`, is controlled by a different hyperparameter; for example, all `θ[k]`s may be assumed to be independent Gaussian variables, each one with a different variance. In turn, variances are considered to be random variables that follow a statistical distribution controlled by another set of deterministic (not random) hyperparameters; thus, a hierarchy of priors is adopted. As we will see later on, hierarchical priors are often designed using conjugate pairs of PDFs.

    3.  **Noninformative or objective priors.** The choice of the prior is done in such a way to embed as little extra information as possible and to exploit knowledge that is conveyed only by the available data. One way to construct such priors is to resort to information theoretic arguments. For example, one can estimate `p(θ)` by minimizing its Kullback–Leibler (KL) divergence from `p(θ|y)`.
