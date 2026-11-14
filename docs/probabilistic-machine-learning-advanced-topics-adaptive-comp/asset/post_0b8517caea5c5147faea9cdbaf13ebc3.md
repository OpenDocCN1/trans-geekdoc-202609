
This remark allows, nonetheless, to narrow down the set of candidate functions to those that have already undergone such transformations. This reasoning yields the so-called set of c-concave functions, \(\mathcal{F}_c \triangleq \{f \mid \exists g : \mathcal{X} \to \mathbb{R}, f = \overline{g}\}\), which can be shown, equivalently, to be the set of functions \(f\) such that \(f = \overline{\tilde{f}}\). One can therefore focus our attention to c-concave functions to solve (6.199) using a so-called semi-dual formulation,

\(\sup_{f \in \mathcal{F}_c} \int_{\mathcal{X}} f \, d\mu + \int_{\mathcal{X}} \overline{f} \, d\nu.\)

Going from (6.199) to (6.203), we have removed a dual variable \(g\) and narrowed down the feasible set to \(\mathcal{F}_c\), at the cost of introducing the highly non-linear transform \(\overline{f}\). This reformulation is, however, very useful, in the sense that it allows us to restrict our attention to c-concave functions, notably for two important classes of cost functions \(c\): distances and squared-Euclidean norms.

## 6.8.3.2 Kantorovich-Rubinstein duality and Lipschitz potentials

A striking result illustrating the interest of c-concavity is provided when \(c\) is a metric \(d\), namely when \(p=1\) in (6.197). In that case, one can prove (exploiting notably the triangle inequality of the \(d\)) that a \(d\)-concave function \(f\) is 1-Lipschitz (one has \(|f(\mathbf{x}) - f(\mathbf{y})| \le d(\mathbf{x}, \mathbf{y})\) for any \(\mathbf{x}, \mathbf{y}\)) and such that \(\overline{f} = -f\). This result translates therefore in the following identity:

\(W_1(\mu, \nu) = \sup_{f \in 1\text{-Lipschitz}} \int_{\mathcal{X}} f \, (d\mu - d\nu).\)

This result has numerous practical applications. This supremum over 1-Lipschitz functions can be efficiently approximated using wavelet coefficients of densities in low dimensions [SJ08], or heuristically in more general cases by training neural networks parameterized to be 1-Lipschitz [ACB17] using ReLU activation functions, and bounds on the entries of the weight matrices.

## 6.8.3.3 Monge maps as gradients of convex functions: the Brenier theorem

Another application of c-concavity lies in the case \(c(\mathbf{x}, \mathbf{y}) = \frac{1}{2} \|\mathbf{x} - \mathbf{y}\|^2\), which corresponds, up to the factor \(\frac{1}{2}\), to the squared \(W_2\) distance used between densities in an Euclidean space. The remarkable result, shown first by [Bre91], is that the Monge map solving (6.194) between two measures for that cost (taken for granted \(\mu\) is regular enough, here assumed to have a density wrt the Lebesgue measure) exists and is necessarily the gradient of a convex function. In loose terms, one can show that

\(T^\star = \arg \min_{T: T_\sharp \mu = \nu} \int_{\mathcal{X}} \frac{1}{2} \|\mathbf{x} - T(\mathbf{x})\|_2^2 \, \mu(d\mathbf{x}).\)

exists, and is the gradient of a convex function \(u : \mathbb{R}^d \to \mathbb{R}\), namely \(T^\star = \nabla u\). Conversely, for any convex function \(u\), the optimal transport map between \(\mu\) and the displacement \(\nabla u_\sharp \mu\) is necessarily equal to \(\nabla u\).

We provide a sketch of the proof: one can always exploit, for any reasonable cost function \(c\) (e.g., lower bounded and lower semi continuous), primal-dual relationships: Consider an optimal coupling \(P^\star\) for (6.196), as well as an optimal c-concave dual function \(f^\star\) for (6.203). This implies in particular that \((f^*, g^* = \overline{f^*})\) is optimal for (6.199). Complementary slackness conditions for this pair of linear programs imply that if \(\mathbf{x}_0, \mathbf{y}_0\) is in the support of \(P^*\), then necessarily (and sufficiently) \(f^*(\mathbf{x}_0) + \overline{f^*}(\mathbf{y}_0) = c(\mathbf{x}_0, \mathbf{y}_0)\). Suppose therefore that \(\mathbf{x}_0, \mathbf{y}_0\) is indeed in the support of \(P^*\). From the equality \(f^*(\mathbf{x}_0) + \overline{f^*}(\mathbf{y}_0) = c(\mathbf{x}_0, \mathbf{y}_0)\) one can trivially obtain that \(\overline{f^*}(\mathbf{y}_0) = c(\mathbf{x}_0, \mathbf{y}_0) - f^*(\mathbf{x}_0)\). Yet, recall also that, by definition, \(\overline{f^*}(\mathbf{y}_0) = \inf_c c(\mathbf{x}, \mathbf{y}_0) - f^*(\mathbf{x})\). Therefore, \(\mathbf{x}_0\) has the special property that it minimizes \(\mathbf{x} \rightarrow c(\mathbf{x}, \mathbf{y}_0) - f^*(\mathbf{x})\). If at that point, one recalls that \(c\) is assumed in this section to be \(c(\mathbf{x}, \mathbf{y}) = \frac{1}{2}\|\mathbf{x} - \mathbf{y}\|^2\), one has therefore that \(\mathbf{x}_0\) verifies

\(\mathbf{x}_0 \in \operatorname{argmin}_{\mathbf{x}} \frac{1}{2}\|\mathbf{x} - \mathbf{y}_0\|^2 - f^*(\mathbf{x}).\)

Assuming \(f^*\) is differentiable, which one can prove by \(c\)-concavity, this yields the identity

\(\mathbf{y}_0 - \mathbf{x}_0 - \nabla f^*(\mathbf{x}_0) = 0 \Rightarrow \mathbf{y}_0 = \mathbf{x}_0 - \nabla f^*(\mathbf{x}_0) = \nabla \left( \frac{1}{2}\|\cdot\|^2 - f^* \right)(\mathbf{x}_0).\)

Therefore, if \((\mathbf{x}_0, \mathbf{y}_0)\) is in the support of \(P^*\), \(\mathbf{y}_0\) is uniquely determined, which proves \(P^*\) is in fact a Monge map “disguised” as a coupling, namely

\(P^* = (\text{Id}, \nabla(\frac{1}{2}\|\cdot\|^2 - f^*))_\sharp \mu.\)

The end of the proof can be worked out as follows: For any function \(h : \mathcal{X} \rightarrow \mathbf{R}\), one can show, using the definitions of \(c\)-transforms and the Legendre transform, that \(\frac{1}{2}\|\cdot\|^2 - h\) is convex if and only if \(h\) is \(c\)-concave. An intermediate step in that proof relies on showing that \(\frac{1}{2}\|\cdot\|^2 - \overline{h}\) is equal to the Legendre transform of \(\frac{1}{2}\|\cdot\|^2 - h\). The function \(\frac{1}{2}\|\cdot\|^2 - f^*\) above is therefore convex, by \(c\)-concavity of \(f^*\), and the optimal transport map is itself the gradient of a convex function.

Knowing that an optimal transport map for the squared-Euclidean cost is necessarily the gradient of a convex function can prove very useful to solve (6.203). Indeed, this knowledge can be leveraged to restrict estimation to relevant families of functions, namely gradients of input-convex neural networks [AXK17], as proposed in [Mak+20] or [Kor+20], as well as arbitrary convex functions with desirable smoothness and strong-convexity constants [PdC20].

## 6.8.3.4 Closed forms for univariate and Gaussian distributions

Many metrics between probability distributions have closed form expressions for simple cases. The Wasserstein distance is no exception, and can be computed in closed form in two important scenarios. When distributions are univariate and the cost \(c(\mathbf{x}, \mathbf{y})\) is either a convex function of the difference \(\mathbf{x} - \mathbf{y}\), or when \(\partial c/\partial \mathbf{x} \partial \mathbf{y} < 0\) a.e., then the Wasserstein distance is essentially a comparison between the quantile functions of \(\mu\) and \(\nu\). Recall that for a measure \(\rho\), its quantile function \(Q_\rho\) is a function that takes values in \([0, 1]\) and is valued in the support of \(\rho\), and corresponds to the (generalized) inverse map of \(F_\rho\), the cumulative distribution function (cdf) of \(\rho\). With these notations, one has that

\(\text{OT}_c(\mu, \nu) = \int_{[0,1]} c(Q_\mu(u), Q_\nu(u)) \, \mathrm{d}u\)

In particular, when \(c\) is \(\mathbf{x}, \mathbf{y} \mapsto |\mathbf{x} - \mathbf{y}|\) then \(\text{OT}_c(\mu, \nu)\) corresponds to the Kolmogorov-Smirnov statistic, namely the area between the cdf of \(\mu\) and that of \(\nu\). If \(c\) is \(\mathbf{x}, \mathbf{y} \mapsto (\mathbf{x} - \mathbf{y})^2\), we recover simply the squared-Euclidean norm between the quantile functions of \(\mu\) and \(\nu\). Note finally that the Monge map is also available in closed form, and is equal to \(Q_\nu \circ F_\mu\).

The second closed form applies to so-called elliptically contoured distributions, chiefly among them Gaussian multivariate distributions [Gel90]. For two Gaussians \(\mathcal{N}(\mathbf{m}_1, \Sigma_1)\) and \(\mathcal{N}(\mathbf{m}_2, \Sigma_2)\) their 2-Wasserstein distance decomposes as

$$
W_2^2(\mathcal{N}(\mathbf{m}_1, \Sigma_1), \mathcal{N}(\mathbf{m}_2, \Sigma_2)) = \|\mathbf{m}_1 - \mathbf{m}_2\|^2 + \mathcal{B}^2(\Sigma_1, \Sigma_2)
$$

where the Bures metric \(\mathcal{B}\) reads:

$$
\mathcal{B}^2(\Sigma_1, \Sigma_2) = \text{tr} \left( \Sigma_1 + \Sigma_2 - 2 \left( \Sigma_1^{\frac{1}{2}} \Sigma_2 \Sigma_1^{\frac{1}{2}} \right)^{\frac{1}{2}} \right).
$$

Notice in particular that these quantities are well-defined even when the covariance matrices are not invertible, and that they collapse to the distance between means as both covariances become 0.

When the first covariance matrix is invertible, one has that the optimal Monge map is given by

\(T \triangleq \mathbf{x} \mapsto A(\mathbf{x} - \mathbf{m}_1) + \mathbf{m}_2, \text{ where } A \triangleq \Sigma_1^{-\frac{1}{2}} \left( \Sigma_1^{\frac{1}{2}} \Sigma_2 \Sigma_1^{\frac{1}{2}} \right)^{\frac{1}{2}} \Sigma_1^{-\frac{1}{2}}\)

It is easy to show that \(T^*\) is indeed optimal: The fact that \(T_\sharp \mathcal{N}(\mathbf{m}_1, \Sigma_1) = \mathcal{N}(\mathbf{m}_2, \Sigma_2)\) follows from the knowledge that the affine push-forward of a Gaussian is another Gaussian. Here \(T\) is designed to push precisely the first Gaussian onto the second (and \(A\) designed to recover random variables with variance \(\Sigma_2\) when starting from random variables with variance \(\Sigma_1\)). The optimality of \(T\) can be recovered by simply noticing that it is the gradient of a convex quadratic form, since \(A\) is positive definite, and closing this proof using the Brenier theorem above.

## 6.8.3.5 Exact evaluation using linear program solvers

We have hinted, using duality and \(c\)-concavity, that methods based on stochastic optimization over 1-Lipschitz or convex neural networks can be employed to estimate Wasserstein distances when \(c\) is the Euclidean distance or its square. These approaches are, however, non-convex and can only reach local optima. Apart from these two cases, and the closed forms provided above, the only reliable approach to compute Wasserstein distances appears when both \(\mu\) and \(\nu\) are discrete measures: in that case, one can instantiate and solve the discrete (6.192) problem, or its dual (6.198) formulation. The primal problem is a canonical example of network flow problems, and can be solved with the network-simplex method in \(O(nm(n+m)\log(n+m))\) complexity [AMO88], or, alternatively, with the comparable auction algorithm [BC89]. These approaches suffer from computational limitations: their cubic cost is intractable for large scale scenarios; their combinatorial flavor makes it harder to solve to parallelize simultaneously the computation of multiple optimal transport problems with a common cost matrix \(C\).

An altogether different issue, arising from statistics, should further discourage users from using these LP formulations, notably in high-dimensional settings. Indeed, the bottleneck practitioners will most likely encounter when using (6.192) is that, in most scenarios, their goal will be to approximate the distance between two continuous measures \(\mu, \nu\) using only i.i.d samples contained in empirical
