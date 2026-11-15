indicates a sufficient level of confidence in the ensemble's predictions, allowing ABC to avoid deferring to a higher-cost model when the ensemble's agreement is high, thereby reducing inference costs without sacrificing accuracy. Recall from Definition Definition 3.1 that the failure rate of a deferral rule, as a function of the agreement threshold is given by,

```
Pr(s(x) \ge \theta, h_k(x) \neq y).
```

In particular, safe deferral rules are those with a failure rate bounded by a small \(\epsilon \ge 0\) of our choice. This means that, given a distribution P over \(\mathcal{X} \times \mathcal{Y}\) we can define a function \(p(\theta)\) as,

```
\(p(\theta) = \mathbb{P}(s(x) \ge \theta, H_k(x) \neq y).\)
```

We can now define feasible thresholds, \(\theta\) as those for which the error rate \(p(\theta) \le \epsilon\), since any such \(\theta\) leads to safe deferral. In practice, we rarely have access to P and therefore \(p(\theta)\). We instead use its plugin-estimator, given by

```
\(\hat{p}(\theta) = \frac{1}{n} \sum_{i=1}^n \mathbb{I}[s(x) \ge \theta, H_k(x) \neq y].\)
```

We estimate \(\hat{p}(\theta)\) by using a small subset of samples from the validation set. Typically, we draw around 100 samples and set them aside to determine a stable threshold. Figure B.1 shows how the estimated threshold varies with the number of samples used in the estimation process, across models with different accuracy levels. Each plot represents a model of a specific accuracy, with accuracy percentages indicated in the legend. As shown, the estimate generally stabilizes even with 100 samples, suggesting that only a few validation samples are needed to reliably estimate \(\theta\), making the parameter estimation process efficient and practical for real-world applications.

# B.3 Existence of Safe Deferral Rules and Selection Rates

This section examines the existence of safe deferral rules — rules that have a very low probability of being incorrect, where data is not deferred to a larger model — by evaluating selection rates. For any threshold \(\theta\), the selection rate \(P(r(x) \ge \theta)\) represents the fraction of data that deemed ‘easy’ enough to be processed at a lower tier of the cascade. Experimentally, we observe that \(\theta_\epsilon\) computed in the manner described in Section Appendix B.2 does indeed adhere to the error tolerance of choice \(\epsilon\). This means that whenever a data point is selected at a lower tier, the inference