\(\le \mathcal{H}_{\Omega}^h(-\bar{z}_k, \alpha_{k-1}) - \mathcal{H}_{\Omega}^h(-\bar{z}_{k+1}, \alpha_k) + \frac{\alpha_{k-1}}{2} || \sum_{i=1}^n (\frac{g_{i,k}}{y_{ii,k}} + \gamma_{i,k}) \pi_i ||^2, \tag{5.23}\)

which, by summing (5.23) over k, further yields that

\(\sum_{k=1}^K \sum_{i=1}^n \langle (\frac{g_{i,k}}{y_{ii,k}} + \gamma_{i,k}) \pi_i, \bar{z}_k \rangle \le \mathcal{H}_{\Omega}^h(-\bar{z}_1, \alpha_0) - \mathcal{H}_{\Omega}^h(-\bar{z}_{K+1}, \alpha_K) + \sum_{k=1}^K \frac{\alpha_{k-1}}{2} || \sum_{i=1}^n (\frac{g_{i,k}}{y_{ii,k}} + \gamma_{i,k}) \pi_i ||^2, \tag{5.24}\)

where the first term on the right side of the inequality is derived from \(\mathcal{H}_{\Omega}^h(-\bar{z}_1, \alpha_0) - \mathcal{H}_{\Omega}^h(-\bar{z}_{K+1}, \alpha_K) = (\mathcal{H}_{\Omega}^h(-\bar{z}_k, \alpha_{K-1}) - \mathcal{H}_{\Omega}^h(-\bar{z}_{K+1}, \alpha_K)) + \cdots (\mathcal{H}_{\Omega}^h(-\bar{z}_1, \alpha_0) - \mathcal{H}_{\Omega}^h(-\bar{z}_2, \alpha_1))\). Additionally, based on the definitions of \(\bar{x}_k\) and \(\mathcal{H}_{\Omega}^h(\cdot)\), it follows that \(\mathcal{H}_{\Omega}^h(-\bar{z}_{K+1}, \alpha_K)\) equals \(-\langle \bar{z}_{K+1}, \bar{x}_{K+1} \rangle\) minus (1/\alpha_K) times h(\bar{x}_{K+1}). Therefore combining Eqs. (5.21) and (5.24) leads to the conclusion that

\(\sum_{k=1}^K \sum_{i=1}^n \langle (\frac{g_{i,k}}{y_{ii,k}} + \gamma_{i,k}) \pi_i, \bar{z}_k - x^* \rangle \le \mathcal{H}_{\Omega}^h(-\bar{z}_1, \alpha_0) + \langle \bar{z}_1, x^* \rangle + \langle \bar{z}_{K+1}, \bar{x}_{K+1} - x^* \rangle + \frac{h(\bar{x}_{K+1})}{\alpha_K} + \sum_{k=1}^K \frac{\alpha_{k-1}}{2} || \sum_{i=1}^n (\frac{g_{i,k}}{y_{ii,k}} + \gamma_{i,k}) \pi_i ||^2. \tag{5.25}\)

Define a function \(\psi(x)\) as the sum of the inner product \(\langle \bar{z}_{K+1}, x \rangle\) and the ratio h(x)/\alpha_K. It is important to observe that \(\bar{x}_{K+1}\) equals \(\Pi_{\Omega}^h(\bar{z}_{K+1}, \alpha_K)\). Given that h(x) exhibits 1-strong convexity, it follows that \(\psi(x)\) demonstrates 1/\alpha_K-strong convexity. Referring to Lemma 5.4 in reference [45], we can deduce that

\(\langle \bar{z}_{K+1}, \bar{x}_{K+1} - x^* \rangle + \frac{h(\bar{x}_{K+1})}{\alpha_K} \le \frac{h(x^*)}{\alpha_K}. \tag{5.26}\)

Furthermore, by applying the Cauchy inequality, we infer that

\(\mathbb{E}[|| \sum_{i=1}^n (\gamma_{i,k} + \frac{g_{i,k}}{y_{ii,k}}) \pi_i ||^2] \le \mathbb{E}[|| \sum_{i=1}^n (\gamma_{i,k} + \frac{g_{i,k}}{y_{ii,k}})^2 ||] \sum_{i=1}^n || \pi_i ||^2]\)