we emphasise the following points of difference. First, the asymptotic variance in the high-dimensional setting depends on $\bar{S}_{\breve{b}_*} = M'_{\breve{b}_*}$, the score function of a regularised version of M (rather than M itself). In addition, the “effective noise” in the high-dimensional regime is $\bar{\varepsilon} + \tau_* G$, rather than $\bar{\varepsilon}$. In fact, Donoho and Montanari (2016, Corollary 4.3) showed that

$V(S_{\breve{b}_*};\bar{\varepsilon}+\tau_*G) \ge \frac{1}{1-\delta^{-1}} \cdot \frac{1}{I(P_{\breve{\varepsilon}})}$, (4.62)

where $I(P_{\breve{\varepsilon}})^{-1}$ is the classical lower bound. This shows that the M-estimator is inefficient in high dimensions, particularly so when $\delta$ is close to 1.

We also mention that Donoho and Montanari (2015, Theorem 2.2) extended the conclusion (4.60) to M-estimators defined with respect to the Huber loss function, which is not strongly convex on $\mathbb{R}$ and hence is not covered by Theorem 4.7. Donoho and Montanari (2016, Section 6) noted an interesting connection between the Lasso and Huber M-estimators, as a special case ($J: w \mapsto \lambda|w|$) of a duality relationship between the following optimisation problems:

+   (i) The regularised least squares problem

minimise $\frac{1}{2}\|\breve{y} - \breve{X}\breve{\beta}\|^2 + \sum_{j=1}^p J(\breve{\beta}_j)$ over $\breve{\beta} \in \mathbb{R}^n$

based on $\breve{X} \in \mathbb{R}^{(n-p) \times n}$ and $\breve{y} \in \mathbb{R}^{n-p}$, with convex penalty $J: \mathbb{R} \mapsto \mathbb{R}$;

+   (ii) The unpenalised M-estimation problem (4.50) based on $X \in \mathbb{R}^{n \times p}$, $y \in \mathbb{R}^n$ satisfying $\breve{X}X = 0$ and $\breve{y} = \breve{X}y$, with convex loss function M: $w \mapsto \min_{z \in \mathbb{R}} \{J(z) + (z-w)^2/2\}$.

# 4.7 GAMP for Logistic Regression

To further illustrate the generality and utility of the GAMP framework, we will now demonstrate how it can be applied to a popular non-linear GLM, namely the logistic regression model with canonical logit link.