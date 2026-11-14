# # B.2 Proof of Theorem 4.14

Proof We show that any optimal sequence with \( M \in \mathfrak{N}_0 \) attack points (in the sense of Definition 4.10) must have a monotonically increasing sequence of non-zero elements. For \( M = 0 \), the trivial sequence \( \alpha^* = \mathbf{0} \) is the only sequence in \( \mathcal{A}^{(M, \infty)} \) and thus is optimal (and trivially satisfies the theorem).

For \( M > 0 \), the proof proceeds by contradiction by assuming that there exists an such that there is an optimal sequence, \( \alpha^* \in \mathcal{A}^{(M, \infty)} \) with a sub-sequence of non-zero elements that is not monotonically non-decreasing. To simplify the proof, we instead consider an equivalent sequence (with respect to the distance function) with all interleaving zero elements removed from \( \alpha^* \). As shown in Theorem 4.12, the placement of zero elements in the sequence *does not affect* the distance function \( D(\cdot) \). Thus, the sequence \( \alpha^* \) achieves the same distance as the sequence \( \alpha^{opt} \) created by removing the zero elements of \( \alpha^* \). Moreover, for \( \alpha^* \) to not be non-decreasing in some non-zero sub-sequence, the sequence \( \alpha^{opt} \) *must* have at least one pair of adjacent decreasing elements. That is, there exists an index \( \tau \) such that the \( \tau^\text{th} \) and \( (\tau + 1)^\text{th} \) elements decrease: \( \alpha_\tau^{opt} > \alpha_{\tau+1}^{opt} \). We show that, by switching these elements, the distance achieved by the resulting sequence exceeds that of \( \alpha^{opt} \), i.e., \( \alpha^{opt} \) is not optimal. Formally, we assume that

\(\exists \alpha^{opt} \in \mathcal{A}^{(M, \infty)} \text{ s.t. } \forall \alpha \in \mathcal{A}^{(M, \infty)} \quad D(\alpha^{opt}) \ge D(\alpha) \qquad \text{(B.3)}\)
\(\text{and } \exists \tau \in \mathfrak{N} \text{ s.t. } \alpha_\tau^{opt} > \alpha_{\tau+1}^{opt} > 0. \qquad \text{(B.4)}\)

Now we consider an alternative sequence \( \alpha' \in \mathcal{A}^{(M, \infty)} \) that switches the \( \tau^\text{th} \) and \( (\tau + 1)^\text{th} \) element of \( \alpha^{opt} \) :

\(\alpha'_\tau = \left\{ \begin{array}{ll} \alpha_t^{opt}, & \text{if } t < \tau \\ \alpha_{t+1}^{opt}, & \text{if } t = \tau \\ \alpha_{t-1}^{opt}, & \text{if } t = \tau + 1 \\ \alpha_t^{opt}, & \text{if } t > \tau + 1 \end{array} \right.\)

By design, \( \alpha^{opt} \) and \( \alpha' \) are \( (\tau, 1) \)-differing sequences and thus we can compute the difference in their distances by applying Lemma B.1 to yield\(^1\)

\(\Delta_{\alpha^{opt}, \alpha'} = \frac{ \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha'_\tau \right) \cdot \alpha_\tau^{opt} \cdot \alpha_{\tau+1}^{opt} - \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha_\tau^{opt} \right) \cdot \alpha'_\tau \cdot \alpha'_{\tau+1} }{ \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha_\tau^{opt} \right) \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha'_\tau \right) \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha_\tau^{opt} + \alpha_{\tau+1}^{opt} \right) }\)
\(= \frac{ \left( \alpha_{\tau+1}^{opt} - \alpha_\tau^{opt} \right) \cdot \alpha_\tau^{opt} \cdot \alpha_\tau^{opt} }{ \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha_\tau^{opt} \right) \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha_{\tau+1}^{opt} \right) \left( \mu_{\tau-1}^{(\alpha^{opt})} + \alpha_\tau^{opt} + \alpha_{\tau+1}^{opt} \right) },\)

in which \( \mu_t^{(\alpha^{opt})} = N + \sum_{\ell=1}^t \alpha_\ell^{opt} \) from Lemma B.1.

\(^1\) Although \( \mu_{\tau-1}^{(\alpha^{opt})} \) may be zero (e.g., if \( \tau = 0 \)), the lemma is applicable since we assumed \( \alpha_\tau^{opt} > \alpha_{\tau+1}^{opt} > 0 \).