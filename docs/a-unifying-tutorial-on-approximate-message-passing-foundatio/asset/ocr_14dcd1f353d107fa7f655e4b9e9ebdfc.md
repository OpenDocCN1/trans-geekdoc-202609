As for (3.23), we can apply (3.9), the definition of \( R_{\pi, \psi}(\rho) \), the fact that \( \rho_k \le \rho_k^* \) and Lemma 3.7 (in that order) to conclude that \( n^{-1} \sum_{i=1}^n \psi(\hat{v}_i^k, v_i) \xrightarrow{c} \mathbb{E}\{\psi(g_k(\mu_k V + \sigma_k G_k), V)\} \ge R_{\psi, \pi}(\rho_k) \ge R_{\psi, \pi}(\rho_k^*) \), as required.

Proof of Theorem 3.10. Under the conditions of Lemma 3.8, each \( g_k^*: \mathbb{R} \to \mathbb{R} \) is Lipschitz and satisfies (M2), and by Corollary A.19, \( \rho \mapsto \lambda^2(1 - \text{mmse}(\rho)) =: m_\lambda(\rho) \) is non-decreasing on \( [0, \infty) \) and continuous on \( (0, \infty) \).

+   (a) We will show that if either (i) or (ii) holds, then
+   \(\rho_{\text{AMP}}^* \equiv \rho_{\text{AMP}}^*(\lambda) := \inf\{\rho > 0 : \rho = m_\lambda(\rho)\} > 0,\rho_0^* \in [0, \rho_{\text{AMP}}^*], \rho_1^* > 0,\m_\lambda(\rho) \ge \rho \text{ for all } \rho \in [0, \rho_{\text{AMP}}^*], \rho_{k+1}^* = m_\lambda(\rho_k^*) \text{ for all } k \in \mathbb{N}_0.\) (A.64)

Note that since \( m_\lambda(\rho) \le \lambda^2 \) for all \( \rho \in [0, \infty) \), we always have \( \rho_{\text{AMP}}^*(\lambda) \le \lambda^2 \).

+   (i) Non-spectral initialisation: In this case, (M1) holds with \( \mu_0 = 0, \sigma_0 = 1, \rho_0^* = 0 \) and \( U = 1 \). Since \( \mathbb{E}(V) \neq 0 \) and \( \mathbb{E}(V^2) = 1 \) by (M1), \( \rho_1^* = \lambda^2(1 - \text{mmse}_k(0)) = \lambda^2(1 - \text{Var}(V)) = \lambda^2 \mathbb{E}(V)^2 = m_\lambda(0) > 0 \), and therefore \( \rho_{k+1}^* = m_\lambda(\rho_k^*) \) for all \( k \in \mathbb{N}_0 \). In addition, \( m_\lambda(\rho) \ge m_\lambda(0) = \rho_1^* > \rho \) for all \( \rho \in [0, \rho_1^*) \), so \( \rho_{\text{AMP}}^* \ge \rho_1^* > 0 \) and \( m_\lambda(\rho) > \rho \) for all \( \rho \in [0, \rho_{\text{AMP}}^*) \).

+   (ii) Spectral initialisation: By Proposition 3.4, (M1) holds with \( U \equiv G_0 \sim N(0, 1) \), so \( \rho_{k+1}^* = m_\lambda(\rho_k^*) \) for all \( k \in \mathbb{N}_0 \). Since \( \text{mmse}(\rho) \) is the minimum value of \( \mathbb{E}\{(V - g(\sqrt{\rho} V + G))^2\} \) as \( g \) ranges over all measurable functions,
+   \( m_\lambda(\rho) \ge \lambda^2(1 - \inf_{a,b \in \mathbb{R}} \mathbb{E}\{(V - a(\sqrt{\rho} V + G) - b)^2\} )\)
+   \( = \lambda^2 \left( 1 - \frac{1 - \mathbb{E}(V)^2}{1 + \rho \{1 - \mathbb{E}(V)^2\}} \right) \ge \frac{\lambda^2 \rho}{1 + \rho}\)

for all \( \rho \in [0, \infty) \), where the equality above can be verified by a routine calculation. Recalling that \( \lambda > 1 \), we have