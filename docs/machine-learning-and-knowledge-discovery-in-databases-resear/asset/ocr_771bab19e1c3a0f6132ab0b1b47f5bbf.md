where $\mathcal{B}$ denotes training batches, $\tau = 0.5$ controls negative sample discrimination, and $(z_m, z'_m)$ are paired embeddings from the molecular and bond-interaction views. The contrastive loss operates directly on graph encoder outputs $z_G$ to maximize mutual information between complementary representations.

# ## 3.3 Evidential Uncertainty Quantification

Existing metabolic stability (MS) prediction methods typically employ two distinct learning paradigms: (1) **Classification framework** mapping instances x to binary stability labels $y \in \{0, 1\}$ with class probabilities $\pi = [\pi_0, \pi_1] \in \mathbb{R}^2$, and (2) **(2) Regression framework**: predicting continuous half-life values $y \in \mathbb{R}^+$. However, these approaches only output predicted probability distributions or continuous values, critically lacking epistemic uncertainty quantification (knowledge uncertainty), compromising their reliability in decision-critical applications.

To address this limitation, we propose a unified Beta-Binomial uncertainty quantification framework that harmonizes discrete and continuous predictions through evidential reasoning (Fig. 1c). Our approach establishes a formal correspondence between neural network outputs and subjective logic [7] parameters, enabling principled uncertainty estimation.

**For binary classification**, we formalize the relationship between evidence and belief masses via Beta-Binomial conjugacy. Given evidence vector $\mathbf{e} = (e^+, e^-) \in \mathbb{R}^2_+$ (_e.g._, two neurons in a linear layer) representing supporting/non-supporting observations, we parameterize the Beta distribution as:

```
Beta\((\alpha, \beta)\), \(\alpha = e^+ + 1\), \(\beta = e^- + 1\)
```

This formulation induces a Dirichlet evidence distribution with probability density:

```
\(\text{Beta}(p|\alpha, \beta) = \frac{p^{\alpha-1}(1-p)^{\beta-1}}{\text{B}(\alpha, \beta)}\), \(\text{B}(\alpha, \beta) = \frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha + \beta)}\)
```

where \(\Gamma(\cdot)\) is the gamma function. Through subjective logic transformation, we derive three fundamental mass components: belief mass ($b$) supporting positive classification, disbelief mass ($d$) endorsing negative classification, and uncertainty mass ($u$) quantifying the indeterminacy level, formally expressed as:

```
\(b = \frac{e^+}{S} = \frac{\alpha - 1}{S}, d = \frac{e^-}{S} = \frac{\beta - 1}{S}, u = \frac{K}{S}\)
```

with \(S = \alpha + \beta\) as total evidence strength and \(K = 2\) as the Dirichlet prior constant. This maintains the conservation property \(b + d + u = 1\). Concurrently, the projected class probabilities correspond to the Beta distribution's expectation:

```
\(\hat{\mathbf{p}} = (\mathbb{E}[p^+], \mathbb{E}[p^-]) = \left( \frac{\alpha}{S}, \frac{\beta}{S} \right)\)
```