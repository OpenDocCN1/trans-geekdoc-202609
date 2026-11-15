The iteration (4.29) has two important features that make it a useful theoretical tool. First, Remark 4.3 ensures that its iterates are characterised by the state evolution parameters \((\mu_k, \sigma_k, \Sigma_k: k \in \mathbb{N})\) under the hypotheses of Theorem 4.2. In addition, the following result highlights the significance of (4.29) as an optimisation procedure for the original constrained problem (4.22).

**Proposition 4.4** (Rangan et al., 2016, Theorem 1). In (4.22), suppose that \(\ell\) and \(J\) are convex in their first arguments, and define the associated Lagrangian by

```
L(\tilde{\beta}, \tilde{\theta}, s) := \sum_{i=1}^n \ell(\tilde{\theta}_i, y_i) + \sum_{j=1}^p J(\tilde{\beta}_j) + s^\top (\tilde{\theta} - X \tilde{\beta})
```

for \(\tilde{\beta} \in \mathbb{R}^p\) and \(\tilde{\theta}, s \in \mathbb{R}^n\). Then the iterates in (4.29) satisfy

```
\hat{\beta}^{k+1} = \underset{\tilde{\beta} \in \mathbb{R}^p}{\text{argmin}} \{ L(\tilde{\beta}, \tilde{\theta}^k, \hat{s}^k) - \frac{\bar{c}_k}{2} \| \tilde{\beta} - \hat{\beta}^k \|^2 \},
\hat{\theta}^{k+1} = \underset{\tilde{\theta} \in \mathbb{R}^n}{\text{argmin}} \{ L(\hat{\beta}^{k+1}, \tilde{\theta}, \hat{s}^k) + \frac{1}{2\bar{b}_{k+1}} \| \tilde{\theta} - X \hat{\beta}^{k+1} \|^2 \},
\hat{s}^{k+1} = \hat{s}^k + \frac{(\hat{\theta}^{k+1} - X \hat{\beta}^{k+1})}{\bar{b}_{k+1}}.
```

for \(k \in \mathbb{N}_0\). Moreover, if \((\beta^*, \theta^*, \tilde{\beta}^*, \tilde{\theta}^*, \hat{s}^*)\) is a fixed point of (4.29), then \((\tilde{\beta}^*, \tilde{\theta}^*)\) is a solution to the optimisation problem (4.22), i.e., \(\hat{\beta}^* \in \underset{\tilde{\beta} \in \mathbb{R}^p}{\text{argmin}} C(\tilde{\beta}; X, y)\).

In fact, the proof we give in Section A.9 reveals that Proposition 4.4 holds for any choice of deterministic scalars \(\bar{b}_k > 0\) and \(\bar{c}_k < 0\) in the first column of (4.29), provided that these are also used to define \(\tilde{g}_k, f_{k+1}\). The characterisation in (4.31)–(4.33) shows that the GAMP algorithm (4.29) is closely related to (but not completely identical to) a “linearised” Alternating Direction Method of Multipliers (ADMM) procedure (Parikh and Boyd, 2013, Section 4.4.2) for optimising (4.22). Alternating algorithms of this type are particularly well-suited to handling objective functions of the form (4.30) since each minimisation step involves only one of \(J\) and \(\ell\) (while (4.33) is a dual update step). The forms of the quadratic penalties in (4.31)–(4.32)