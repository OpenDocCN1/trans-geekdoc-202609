# 6.8.2.2 Monge formulation and optimal push forward maps

By introducing mass-splitting, the Kantorovich formulation of optimal transport allows for a far more general comparison between discrete measures of different sizes and weights (middle plot of Fig. 6.18). Naturally, this flexibility comes with a downside: one can no longer associate to each point \(\mathbf{x}_i\) another point \(\mathbf{y}_j\) to which it is uniquely associated, as was the case with the classical matching problem. Interestingly, this property can be recovered in the limit where the measures become densities. Indeed, the Monge [Mon81] formulation of optimal transport allows us to recover precisely that property, on the condition (loosely speaking) that measure \(\mu\) admits a density. In that setting, the analogous mathematical object guaranteeing that \(\mu\) is mapped onto \(\nu\) is that of **push forward** maps morphing \(\mu\) to \(\nu\), namely maps \(T\) such that for any measurable set \(A \subset \mathcal{X}\), \(\mu(T^{-1}(A)) = \nu(A)\). When \(T\) is differentiable, and \(\mu, \nu\) have densities \(p\) and \(q\) wrt the Lebesgue measure in \(\mathbb{R}^d\), this statement is equivalent, thanks to the change of variables formula, to ensuring almost everywhere that:

\(q(T(x)) = p(x)|J_T(x)|,\) (6.193)

where \(|J_T(x)|\) stands for the determinant of the Jacobian matrix of \(T\) evaluated at \(x\). Writing \(T_\sharp \mu = \nu\) when \(T\) does satisfy these conditions, the Monge [Mon81] problem consists in finding the best map \(T\) that minimizes the average cost between \(\mathbf{x}\) and its displacement \(T(\mathbf{x})\),

\(\inf_{T: T_\sharp \mu = \nu} \int_{\mathcal{X}} c(x, T(x)) \mu(dx).\) (6.194)

\(T\) is therefore a map that pushes \(\mu\) forwards to \(\nu\) globally, but which results, on average, in the smallest average cost. While very intuitive, the Monge problem turns out to be extremely difficult to solve in practice, since it is non-convex. Indeed, one can easily check that the constraint \(\{T_\sharp \mu = \nu\}\) is not convex, since one can easily find counter-examples for which \(T_\sharp \mu = \nu\) and \(T'_\sharp \nu\) yet \((\frac{1}{2}T + \frac{1}{2}T')_\sharp \mu \neq \nu\). Luckily, Kantorovich's approach also works for continuous measures, and yields a comparatively much simpler linear program.

# 6.8.2.3 Kantorovich formulation

The Kantorovich problem (6.192) can also be extended to a continuous setting: Instead of optimizing over a subset of matrices in \(\mathbb{R}^{n \times m}\), consider \(\Pi(\mu, \nu)\), the subset of joint probability distributions \(\mathcal{P}(\mathcal{X} \times \mathcal{X})\) with marginals \(\mu\) and \(\nu\), namely

\(\Pi(\mu, \nu) \triangleq \{ \pi \in \mathcal{P}(\mathcal{X}^2) : \forall A \subset \mathcal{X}, \pi(A \times \mathcal{X}) = \mu(A) \text{ and } \pi(\mathcal{X} \times A) = \nu(A) \}.\) (6.195)

Note that \(\Pi(\mu, \nu)\) is not empty since it always contains the product measure \(\mu \otimes \nu\). With this definition, the continuous formulation of (6.192) can be obtained as

\(OT_c(\mu, \nu) \triangleq \inf_{\pi \in \Pi(\mu, \nu)} \int_{\mathcal{X}^2} c \, d\pi.\) (6.196)

Notice that (6.196) subsumes directly (6.192), since one can check that they coincide when \(\mu, \nu\) are discrete measures, with respective probability weights \(\mathbf{a}, \mathbf{b}\) and locations \((\mathbf{x}_1, \dots, \mathbf{x}_n)\) and \((\mathbf{y}_1, \dots, \mathbf{y}_m)\).