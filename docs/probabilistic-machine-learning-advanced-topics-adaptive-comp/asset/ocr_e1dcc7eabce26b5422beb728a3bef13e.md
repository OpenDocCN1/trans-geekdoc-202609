in particular that \((f^*, g^* = \overline{f^*})\) is optimal for (6.199). Complementary slackness conditions for this pair of linear programs imply that if \(\mathbf{x}_0, \mathbf{y}_0\) is in the support of \(P^*\), then necessarily (and sufficiently) \(f^*(\mathbf{x}_0) + \overline{f^*}(\mathbf{y}_0) = c(\mathbf{x}_0, \mathbf{y}_0)\). Suppose therefore that \(\mathbf{x}_0, \mathbf{y}_0\) is indeed in the support of \(P^*\). From the equality \(f^*(\mathbf{x}_0) + \overline{f^*}(\mathbf{y}_0) = c(\mathbf{x}_0, \mathbf{y}_0)\) one can trivially obtain that \(\overline{f^*}(\mathbf{y}_0) = c(\mathbf{x}_0, \mathbf{y}_0) - f^*(\mathbf{x}_0)\). Yet, recall also that, by definition, \(\overline{f^*}(\mathbf{y}_0) = \inf_c c(\mathbf{x}, \mathbf{y}_0) - f^*(\mathbf{x})\). Therefore, \(\mathbf{x}_0\) has the special property that it minimizes \(\mathbf{x} \rightarrow c(\mathbf{x}, \mathbf{y}_0) - f^*(\mathbf{x})\). If at that point, one recalls that \(c\) is assumed in this section to be \(c(\mathbf{x}, \mathbf{y}) = \frac{1}{2}\|\mathbf{x} - \mathbf{y}\|^2\), one has therefore that \(\mathbf{x}_0\) verifies

\(\mathbf{x}_0 \in \operatorname{argmin}_{\mathbf{x}} \frac{1}{2}\|\mathbf{x} - \mathbf{y}_0\|^2 - f^*(\mathbf{x}).\)

Assuming \(f^*\) is differentiable, which one can prove by \(c\)-concavity, this yields the identity

\(\mathbf{y}_0 - \mathbf{x}_0 - \nabla f^*(\mathbf{x}_0) = 0 \Rightarrow \mathbf{y}_0 = \mathbf{x}_0 - \nabla f^*(\mathbf{x}_0) = \nabla \left( \frac{1}{2}\|\cdot\|^2 - f^* \right)(\mathbf{x}_0).\)

Therefore, if \((\mathbf{x}_0, \mathbf{y}_0)\) is in the support of \(P^*\), \(\mathbf{y}_0\) is uniquely determined, which proves \(P^*\) is in fact a Monge map “disguised” as a coupling, namely

\(P^* = (\text{Id}, \nabla(\frac{1}{2}\|\cdot\|^2 - f^*))_\sharp \mu.\)

The end of the proof can be worked out as follows: For any function \(h : \mathcal{X} \rightarrow \mathbf{R}\), one can show, using the definitions of \(c\)-transforms and the Legendre transform, that \(\frac{1}{2}\|\cdot\|^2 - h\) is convex if and only if \(h\) is \(c\)-concave. An intermediate step in that proof relies on showing that \(\frac{2}{}\|\cdot\|^2 - \overline{h}\) is equal to the Legendre transform of \(\frac{1}{2}\|\cdot\|^2 - h\). The function \(\frac{1}{2}\|\cdot\|^2 - f^*\) above is therefore convex, by \(c\)-concavity of \(f^*\), and the optimal transport map is itself the gradient of a convex function.

Knowing that an optimal transport map for the squared-Euclidean cost is necessarily the gradient of a convex function can prove very useful to solve (6.203). Indeed, this knowledge can be leveraged to restrict estimation to relevant families of functions, namely gradients of input-convex neural networks [AXK17], as proposed in [Mak+20] or [Kor+20], as well as arbitrary convex functions with desirable smoothness and strong-convexity constants [PdC20].

# 6.8.3.4 Closed forms for univariate and Gaussian distributions

Many metrics between probability distributions have closed form expressions for simple cases. The Wasserstein distance is no exception, and can be computed in close form in two important scenarios. When distributions are univariate and the cost \(c(\mathbf{x}, \mathbf{y})\) is either a convex function of the difference \(\mathbf{x} - \mathbf{y}\), or when \(\partial c/\partial \mathbf{x} \partial \mathbf{y} < 0\) a.e., then the Wasserstein distance is essentially a comparison between the quantile functions of \(\mu\) and \(\nu\). Recall that for a measure \(\rho\), its quantile function \(Q_\rho\) is a function that takes values in \([0, 1]\) and is valued in the support of \(\rho\), and corresponds to the (generalized) inverse map of \(F_\rho\), the cumulative distribution function (cdf) of \(\rho\). With these notations, one has that

\(\text{OT}_c(\mu, \nu) = \int_{[0,1]} c(Q_\mu(u), Q_\nu(u)) \, \mathrm{d}u\)

In particular, when \(c\) is \(\mathbf{x}, \mathbf{y} \mapsto |\mathbf{x} - \mathbf{y}|\) then \(\text{OT}_c(\mu, \nu)\) corresponds to the Kolmogorov-Smirnov statistic, namely the area between the cdf of \(\mu\) and that of \(\nu\). If \(c\) is \(\mathbf{x}, \mathbf{y} \mapsto (\mathbf{x} - \mathbf{y})^2\), we recover