with $R > R_1$ is bounded by

$\mathcal{E}_R(\theta)^2 \le C \cdot \max_{\gamma \in \{1,\tau\}} \big(\|\mathcal{R}_{\text{PDE}}[u_\theta]\|_{L^2(D)}^2 + \|\mathcal{R}_{\text{dio}}[u_\theta]\|_{L^2(D)}^2\big)^{\gamma} \big(1 + \|\mathcal{R}_d[u_\theta]\|_{L^2(D)}^{2\tau}\big), \tag{5.37}$

where $C$ depends on $u$ and $u_\theta$.

Further examples can be found in Mishra and Molinaro (2022).

# 6. Generalization

Now we turn our attention to Question 3.

**Question 3 (Q3).** Given a small training error $\mathcal{E}_T^*$ and a sufficiently large training set $\mathcal{S}$, will the corresponding generalization error $\mathcal{E}_G^*$ also be small?

We will answer this question by proving that for any model $u_\theta$, 

$\mathcal{E}_G(\theta) \le \mathcal{E}_T(\theta) + \epsilon(\theta), \tag{6.1}$

for some value $\epsilon(\theta) > 0$ that depends on the model class and the size of the training set. Using the terminology of the error decomposition (3.7), this will then imply that the generalization gap is small:

$\sup_{\theta \in \Theta} |\mathcal{E}_T(\theta,\mathcal{S}) - \mathcal{E}_G(\theta)| \le \sup_{\theta \in \Theta} \epsilon(\theta). \tag{6.2}$

As $\epsilon(\theta)$ can depend on $\theta$, we must choose the model (parameter) space $\Theta$ in a suitable way to avoid $\sup_{\theta \in \Theta} \epsilon(\theta)$ diverging.

In view of Section 2.4, one can see that the training error is nothing more than applying a suitable quadrature rule to each term in the generalization error. It is clear that the error bound for a quadrature rule immediately proves that the generalization error can be bounded in terms of the training error and the training set size, thereby answering Question 3, at least for deterministic quadrature rules. We can now combine this generalization result with the stability bounds from Section 5 to prove an upper bound on the total error of the optimized model $\mathcal{E}^*$ (3.1) (Mishra and Molinaro 2023, Theorem 2.6).

**Theorem 6.1.** Let $u \in X^*$ be the unique solution of the PDE (2.1) and assume that the stability hypothesis (5.1) holds. Let $u_\theta \in X^*$ be a model and let $\mathcal{S}$ be a training set of quadrature points corresponding to the quadrature rule (2.65) with order $\alpha$, as in (2.66). Then, for any $L^2$-based generalization error $\mathcal{E}_G$, such as (2.45) or (2.46),

$\mathcal{E}_G(\theta)^2 \le \mathcal{E}_T(\theta)^2 + C_{\text{quad}} N^{-\alpha}, \tag{6.3}$

with constant $C_{\text{quad}}$ stemming from (2.66), and which might depend on $u_\theta$.

The approach described above only makes sense for low to moderately high dimensions ($d < 20$), since the convergence rate of numerical quadrature rules with