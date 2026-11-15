where \(a_1 = \frac{m}{\beta^2 \epsilon_3}(\beta^2 + \frac{\sigma_2^2}{\omega^2})\epsilon_1\), \(a_2 = \frac{1}{n_{\max}}\), and \(a_3 = \frac{\lambda(1-\sigma_2^2)^2 \epsilon_1}{\lambda(1-\sigma_2^2)+8\beta\epsilon_4}\). It is evident that the result of \(\max\{\frac{1}{\log \frac{1}{1-a_1}}, \frac{1}{\log \frac{1}{1-a_2}}, \frac{1}{\log \frac{1}{1-a_3}}\}\) and \(c\) remain unchanged, hence the intricacy can be condensed to \(\mathcal{O}(\log \frac{1}{\epsilon})\).

Proof. To simplify our analysis, we define \(a_1 = \frac{m}{\beta^2 \epsilon_3}(\beta^2 + \frac{\sigma_2^2}{\omega^2})\epsilon_1\), \(a_2 = \frac{1}{n_{\max}}\), and \(a_3 = \frac{\lambda(1-\sigma_2^2)^2 \epsilon_1}{\lambda(1-\sigma_2^2)+8\beta\epsilon_4}\). Given a convergence error denoted as \(\epsilon\), we formulate the subsequent inequality based on Theorem 3.1:

\(\mathbb{E}[\|x_k^i - x^*\|^2] \le c(1 - \min\{a_1, a_2, a_3\})^k \le \epsilon.\)

By applying logarithmic operations to the middle and right sides of the aforementioned inequality, we derive the subsequent equation:

\(k \ge \frac{-\log \frac{\epsilon}{c}}{-\log(1 - \min\{a_1, a_2, a_3\})}.\)

Further simplifying the expression leads to a more comprehensible equation as follows:

\(k \ge \max\{\frac{1}{\log \frac{1}{1-a_1}}, \frac{1}{\log \frac{1}{1-a_2}}, \frac{1}{\log \frac{1}{1-a_3}}\} \log \frac{c}{\epsilon}.\)

The proof is completed.

**Remark 3.2.** The algorithm incorporating gradient tracking has already facilitated a linear convergence speed, as referenced in [34,35,37,40]. Nevertheless, in comparison, the P-DVR algorithm possesses distinct benefits: (i) Due to the inclusion of a projection operator, it is apt for addressing constrained optimization problems; (ii) Thanks to the variance-reduction strategy, it exhibits computational efficiency.

# 3.5 Numerical simulations

To validate the efficacy of the P-DVR algorithm, we conducted numerical simulation experiments involving logistic regression models and acoustic source localization problems.

# 3.5.1 Decentralized logistic regression experiments

In this subsection, the P-DVR algorithm is employed to address a binary classification problem using logistic regression. Assume that a communication network consisting of \(m\) nodes is established, with each node housing \(n\) data points. The logistic regression binary classification problem can be formulated as follows:

\(\min \ f(x), \ \text{s.t.} \ x \in \Omega_0,\)