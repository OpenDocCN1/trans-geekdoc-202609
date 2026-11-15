# **Lemma 7.3.** Given that Assumptions 7.1 and 7.2 are satisfied, define the auxiliary vector \(\bar{h}(k+1) = \frac{1}{v}\sum_{i=1}^v h_i(k+1)\). There exists a constant \(\Theta > 0\) such that for all \(k \ge 1\) and \(i \in \mathcal{V}\), the following inequality holds:

\(\left\| \frac{h_i(k)}{q_i(k)} - \bar{h}(k) \right\| \le \Theta,\)

where

\(\Theta = \frac{1}{\mu}(\delta Q + (1 + v)L + \kappa \sum_{j=1}^v ||h_j(1)||) + \frac{Cv(2L + \delta Q)}{\mu(1 - \lambda)} + ||\bar{h}(1)||.\)

_Proof._ It follows from (7.4) and (7.5a) that

\(h_i(k+1) = \sum_{s=1}^{k-1} \sum_{j=1}^v \psi_{ij}(s+1, k+1) \sum_{l=1}^v P_{jl}(s)\tau_{jl}(s) + g_i(k) + \sum_{s=1}^{k-1} \sum_{j=1}^v \psi_{ij}(s+1, k+1) g_j(s) + \sum_{j=1}^v P_{ij}(k)\tau_{ij}(k) + \sum_{j=1}^v \psi_{ij}(1, k+1)h_j(1).\) (7.8)

Similarly, according to (7.5b), we can obtain that

\(q_i(k+1) = \sum_{j=1}^v P_{ij}(k)q_j(k) = \sum_{j=1}^v \psi_{ij}(1, k+1),\) (7.9)

derived from the condition \(q_j(1) = 1\) for all \(j \in \mathcal{V}\). Utilizing (7.7) and the definition of \(\bar{h}(k+1)\), we obtain

\(\bar{h}(k+1) = \frac{1}{v} \sum_{i=1}^v (\sum_{j=1}^v P_{ij}(k)h_j(k) + \sum_{j=1}^v P_{ij}(k)\tau_{ij}(k) + g_i(k)) = \frac{1}{v} \sum_{j=1}^v h_j(k) + \frac{1}{v} \sum_{i=1}^v \sum_{j=1}^v P_{ij}(k)\tau_{ij}(k) + \frac{1}{v} \sum_{i=1}^v g_i(k) = \bar{h}(k) + \frac{1}{v} \sum_{i=1}^v g_i(k),\) (7.10)