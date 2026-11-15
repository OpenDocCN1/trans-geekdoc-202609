which is deduced from Lemma 5.1 pertaining to the Perron eigenvector. By adding up both sides of Eq. (5.10) over k and reorganizing the resulting equation, one obtains

\(\bar{z}_{k+1} = \bar{z}_1 + \sum_{l=1}^k \sum_{i=1}^n \pi_i \gamma_{i,l} + \sum_{l=1}^k \sum_{i=1}^n \pi_i \frac{g_{i,l}}{y_{ii,l}}.\) (5.11)

For any \(k \in \{1, \cdots, K\}\), define \(\zeta_k = \mathbb{E}[\max_{i \in \mathcal{V}} \| z_{i,k} - \bar{z}_k \|]\).

**Lemma 5.4.** Bearing in mind that \(z_{i,k}\) and \(y_{i,k}\) originate from Algorithm 1, and given Assumptions 5.1 and 5.2, it can be inferred that for every \(k = 1, \cdots, K\),

\(\zeta_k \le \frac{nC(\theta L + \sqrt{2m}b_{\max})}{1 - \varpi} + C \sum_{i=1}^n \| z_{i,1} \| + 2\theta L,\)

where \(b_{\max} = \max_{k \in \{1, \cdots, K\}} b_k\).

Proof. From Eq. (5.7), it can be deduced that

\(z_{i,k+1} = \sum_{j=1}^n [A^k]_{ij} z_{j,1} + \sum_{l=1}^{k-1} \sum_{j=1}^n [A^{k-l}]_{ij} \frac{g_{j,l}}{y_{jj,l}}\) (5.12)

\(+ \frac{g_{i,k}}{y_{ii,k}} + \sum_{l=1}^k \sum_{j=1}^n [A^{k-l+1}]_{ij} \gamma_{j,l}.\) (5.13)

From Eqs. (5.11) and (5.12), it is inferred that

\(z_{i,k+1} - \bar{z}_{k+1} = \vartheta_1 + \vartheta_2 + \vartheta_3,\) (5.14)

where

\(\vartheta_1 = \sum_{j=1}^n ([A^k]_{ij} - \pi_j) z_{j,1},\)

\(\vartheta_2 = \sum_{l=1}^{k-1} \sum_{j=1}^n ([A^{k-l}]_{ij} - \pi_j) \frac{g_{j,l}}{y_{jj,l}} + \frac{g_{i,l}}{y_{ii,l}} + \sum_{i=1}^n \pi_i \frac{g_{i,k}}{y_{ii,k}},\)

\(\vartheta_3 = \sum_{l=1}^k \sum_{j=1}^n ([A^{k-l+1}]_{ij} - \pi_j) \gamma_{j,l}.\)

Lemma 5.1 forms the basis for deriving from \(\vartheta_1\) that

\(\mathbb{E}[\|\vartheta_1\|] = \mathbb{E}[\|\sum_{j=1}^n ([A^k]_{ij} - \pi_j) z_{i,1}\|] \le C \varpi^k \sum_{i=1}^n \| z_{i,1} \|.\)