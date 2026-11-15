Combining (7.12), (7.14), (7.16), and (7.17), we can derive

\(\left\| \frac{h_i(k+1)}{q_i(k+1)} - \bar{h}(k+1) \right\| \leq \frac{\|\varphi_1\| + \|\varphi_2\| + \|\varphi_3\|}{\| \sum_{j=1}^v \Psi_{ij}(1, k+1) \|} + \|\varphi_4\| \leq \frac{2vLC + vC\delta Q}{\mu(1-\lambda)} + \frac{\delta Q + (1+v)L + \kappa \sum_{j=1}^v \|h_j(1)\|}{\mu} + \|\bar{h}(1)\|.\)

Hence, we conclude the proof.

Next, we provide the necessary definitions for the subsequent supporting lemma. For every \(k \ge 1\), an auxiliary variable is defined as follows:

\(\varsigma(k) = \Pi_\Omega^\omega(\bar{h}(k), \gamma(k-1)).\)

Moreover, for any vector \(\sigma \in \mathbb{R}^d\) and \(\gamma > 0\), a conjugate-type function related to the function \(\varphi(\cdot)\) is given by

\(\varphi^\dagger(\sigma, \gamma) = \sup_{x \in \Omega} \{ \langle \sigma, x \rangle - \frac{1}{\gamma} \varphi(x) \}.\)

Moreover, we define \(\hat{g}(s) = (1/v) \sum_{i=1}^v g_i(s)\). Using the above definitions, we now establish a crucial lemma to support the main results.

**Lemma 7.4.** Consider the functions \(\Pi_\Omega^\omega(\sigma, \gamma)\) and \(\varphi^\dagger(\sigma, \gamma)\) given by (7.2) and (7.20), respectively. For a non-increasing and positive sequence \(\{\gamma(k)\}_{k=1}^\infty\), the following statements hold:

+   (a) \(\nabla \varphi^\dagger(-\sigma, \gamma) = \Pi_\Omega^\omega(\sigma, \gamma);\)
+   
+   (b) \(\sum_{s=1}^k \langle \hat{g}(s), \varsigma(s) - x^* \rangle \leq \frac{1}{2} \sum_{s=1}^k \gamma(s-1) \|\hat{g}(s)\|^2 + \frac{1}{\gamma(k)} \varphi(x^*) + \varphi^\dagger(-\bar{h}(1), \gamma(0)) + \langle h(1), x^* \rangle, \forall x^* \in \Omega.\)

Proof. Using (7.2) and (7.20), Lemma 7.4(a) can be easily proved. Based on Lemma 7.4(a) and (7.20), we have

\(- \sum_{s=1}^k \langle \hat{g}(s), x^* \rangle \leq \sup_{x \in \Omega} \{ - \sum_{s=1}^k \langle \hat{g}(s), x \rangle - \bar{h}(1), x \rangle - \frac{1}{\gamma(k)} \varphi(x) \}\)