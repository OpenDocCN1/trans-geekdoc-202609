minimise \(\sum_{i=1}^n \ell(\tilde{\theta}_i, y_i) + \sum_{j=1}^p J(\tilde{\beta}_j) \quad \text{over } (\tilde{\beta}, \tilde{\theta}) \in \mathbb{R}^p \times \mathbb{R}^n \text{ with } \tilde{\theta} = X \tilde{\beta},\) (4.22)

where \(\ell: \mathbb{R}^2 \rightarrow \mathbb{R}\) is a loss function and \(J: \mathbb{R} \rightarrow \mathbb{R}\) is a penalty function. In particular, consider a GLM of the form (4.2) in which \(y_i | (x_i, \beta) \sim q(\cdot | x_i^\top \beta)\) for \(1 \le i \le n\), where \(q(\cdot | z)\) is a Lebesgue density on \(\mathbb{R}\) for each \(z \in \mathbb{R}\). Then the maximum likelihood estimators (MLEs) of \(\beta\) and \(\theta = X\beta\) are given by

\((\hat{\beta}^{MLE}, \hat{\theta}^{MLE}) := \underset{(\tilde{\beta}, \tilde{\theta}) \in \mathbb{R}^p \times \mathbb{R}^n}{\text{argmin}} . \sum_{i=1}^n - \log q(y_i | \tilde{\theta}_i). \quad \tilde{\theta} = X\tilde{\beta}\)

If in addition \(\beta_1, \dots, \beta_p \sim^{iid} p_{\bar{\beta}}\) for some prior density \(p_{\bar{\beta}}\), then the maximum a posteriori (MAP) estimates of \(\beta\) and \(\theta\) are

\((\hat{\beta}^{MAP}, \hat{\theta}^{MAP}) := \underset{(\tilde{\beta}, \tilde{\theta}) \in \mathbb{R}^p \times \mathbb{R}^n}{\text{argmin}} \left( \sum_{i=1}^n - \log q(y_i | \tilde{\theta}_i) + \sum_{j=1}^p - \log p_{\bar{\beta}}(\tilde{\beta}_j) \right). \quad \tilde{\theta} = X\tilde{\beta}\)

Assuming henceforth that \(\ell\) and \(J\) are convex in their first arguments, we will now design a GAMP iteration (4.29) whose fixed points are solutions to the associated optimisation problem (4.22); see Proposition 4.4 below. By exploiting this connection and applying the GAMP theory from Section 4.1, we will explain later how to obtain a statistical payoff in the form of exact high-dimensional asymptotics for estimators defined by (4.22).

To begin the construction, fix two sequences of deterministic scalars \(\bar{b}_k > 0\) and \(\bar{c}_k < 0\) for \(k \in \mathbb{N}_0\). These will later be assigned appropriate values in (4.29) below, but for the time being, we will treat them as generic constants. For \(k \in \mathbb{N}_0\), define \(\bar{g}_k

\(\bar{g}_k(u, v) := \underset{z \in \mathbb{R}}{\text{argmin}} \left\{ \ell(z, v) + \frac{1}{2\bar{b}_k}(z-u)^2 \right\}, \quad g_k(u, v) := \frac{\bar{g}_k(u, v) - u}{\bar{b}_k},\)
(4.23)

\(f_{k+1}(w) := \underset{z \in \mathbb{R}}{\text{argmin}} \left\{ J(z) - \frac{\bar{c}_k}{2} \left( z + \frac{w}{\bar{c}_k} \right)^2 \right\}.\) (4.24)