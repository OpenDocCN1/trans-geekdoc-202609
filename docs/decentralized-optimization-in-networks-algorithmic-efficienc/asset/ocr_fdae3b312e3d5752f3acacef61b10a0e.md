Given that \(\gamma_{i,k}\) follows a Laplace distribution \(\mathcal{L}(0, b_k)\), it can be deduced that the expected value of \(\gamma_{i,k}\) is zero, for all \(i\) belonging to the set \(\mathcal{V}\) and for all \(k\) greater than or equal to 1. Furthermore, Eq. (5.18) suggests additionally that

\(\phi_1 \le \mathbb{E}[\sum_{k=1}^K \sum_{i=1}^n \langle \frac{g_{i,k}}{\gamma_{i,k}}(y_{i,k} - \pi_i), \bar{x}_k - x^* \rangle] + \mathbb{E}[\sum_{k=1}^K \sum_{i=1}^n (\langle \frac{g_{i,k}}{\gamma_{i,k}} + \gamma_{i,k}) \pi_i, \bar{x}_k - x^* \rangle].\) (5.19)

Based on Assumption 5.2, it is inferred that the norm of the difference between \(\bar{x}_k\) and \(x^*\) is bounded by a positive constant \(M\) [28]. Subsequently, Lemma 5.1 is applied to deduce the first term on the right-hand side of Eq. (5.19), which states that

\(\mathbb{E}[\sum_{k=1}^K \sum_{i=1}^n \langle \frac{g_{i,k}}{\gamma_{i,k}}(y_{i,k} - \pi_i), \bar{x}_k - x^* \rangle] \le \mathbb{E}[\sum_{k=1}^K \sum_{i=1}^n || \frac{g_{i,k}}{\gamma_{i,k}} || || (y_{i,k} - \pi_i) || || \bar{x}_k - x^* ||] \le \frac{n C \theta L M}{1 - \varpi} = M_1.\) (5.20)

Next, we examine the second component located on the right-hand side of Eq. (5.19). From Eq. (5.11), it is deduced that

\(\sum_{k=1}^K \sum_{i=1}^n \langle (\frac{g_{i,k}}{\gamma_{i,k}} + \gamma_{i,k}) \pi_i, x^* \rangle = \langle \bar{z}_{K+1}, x^* \rangle - \langle \bar{z}_1, x^* \rangle.\) (5.21)

Observing that \(\alpha_k\) is less than or equal to \(\alpha_{k-1}\), it follows that \(\mathcal{H}_\Omega^h(-\bar{z}_{k+1}, \alpha_k)\) is less than or equal to \(\mathcal{H}_\Omega^h(-\bar{z}_{k+1}, \alpha_{k-1})\). Lemma 5.4 then allows us to deduce that

\(\mathcal{H}_\Omega^h(-\bar{z}_{k+1}, \alpha_k) \le \mathcal{H}_\Omega^h(-\bar{z}_k, \alpha_{k-1}) - \langle \bar{x}_k, \sum_{i=1}^n (\frac{g_{i,k}}{\gamma_{i,k}} + \gamma_{i,k}) \pi_i \rangle + \frac{1}{2} \alpha_{k-1} || \sum_{i=1}^n (\frac{g_{i,k}}{\gamma_{i,k}} + \gamma_{i,k}) \pi_i ||^2.\) (5.22)

Reorganizing the terms leads to

\(\sum_{i=1}^n \langle (\frac{g_{i,k}}{\gamma_{i,k}} + \gamma_{i,k}) \pi_i, \bar{x}_k \rangle\)