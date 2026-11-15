average score of the majority prediction on \(x\) and let \(\text{vote}(x; H^k) = \frac{1}{k} \sum_{h \in H^k} \mathbb{I}[H^k(x) = h(x)]\) denote the fraction of votes received by the prediction, where,

\(r_v(x; \theta_v) = \begin{cases} 1 & \text{vote}(x; H_1^k) \le \theta_v \\ 0 & \text{otherwise.} \end{cases} \quad (3.3)\)

\(r_s(x; \theta_s) = \begin{cases} 1 & s(x; H_1^k) \le \theta_s \\ 0 & \text{otherwise.} \end{cases} \quad (3.4)\)

# ### 3.3.4 Inference Cost Savings and Competitiveness

Since we do not impose an inference cost budget on the cascade, it is possible for the cascade to incur a higher cost than simply using the larger model \(h_2\). Intuitively, if majority of the samples seen during test time are ‘hard’, the cascade pays the cost of evaluating both \(H_1^k(x)\) and \(h_2(x)\).

**Proposition 3.1.** Let \(\mathcal{M} = \{H_1^k, h_2\}\) be two classifiers and \(r\) a deferral rule such that \(r\) is a safe deferral rule for \(H_1^k\) according to Definition 3.1, for a distribution \(\mathbb{P}\) over \(\mathcal{X} \times \mathcal{Y}\). Then for every \(\xi \ge \epsilon > 0\), the agreement based cascading (ABC) classifier \(\mathcal{M}_r(x)\) is such that,

+   1. The ABC classifier is competitive with the large classifier \(h_2\) in terms of accuracy,

\(\mathcal{R}(\mathcal{M}_r) \le \mathcal{R}(h_2) + \epsilon,\)

+   2. The ABC classifier enjoys an average inference cost of,

\(\mathbb{E}[C(\mathcal{M}_r)] = (k^\rho \gamma + \mathbb{P}(r(x) = 1))C(h_2).\)

Thus the cost savings we can expect with a drop-in cascade depends on three key factors; the relative cost \(\gamma\), the degree of parallelization \(\rho\) and the deferral rate \(\mathbb{P}(r(x) = 1)\), or equivalently, the *selection rate* \(\mathbb{P}(r(x) = 0)\). In particular, for *every* feasible deferral rule \(r\), in the best case scenario where the cost of the smaller model is negligible, \((\gamma = 0)\), the cost of inference reduces by the selection rate, \(P(r(x) = 0)\). Conversely, in the worst-case scenarios, the cost can be \((k + 1)\) times the cost of the larger model. In the next section, we demonstrate real world scenarios where the favorable interplay of these three quantities lead to significant improvements in inference cost. See Appendix B.3 and Figure B.2 for information on selection rates for various models and datasets considered here.