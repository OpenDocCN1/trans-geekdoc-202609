each of their responses on the 12 items (after reverse-scoring negatively keyed items). This represents the simplest form of weighting, often termed unit-weighting, as each item contributes equally to the composite score. As discussed above, performing factor analysis opens up a wide array of ways to weight composite scores, often manifested as some variant on weighting based on the factor loads.

Instead of weighting items to create a composite score, researchers can bypass this step and assess each item in terms of its relationship to a criterion of interest. This is often done for criterion-keyed scales and involves selecting only items that beyond some threshold in predicting the criterion (outcome) of interest. This approach points to a fundamental question: Is it better to use items or composites as predictors? Prior to answering this, we define reliability at the item level.

# 7.5 Item Reliability

We just detailed the assessment of reliability with respect to a scale

```
$R_{x_i}^2 = 1 - \frac{\Psi_i}{s_{x_i}^2}$
```

This is also referred to as (item) commonality ($h^2$) in the EFA literature as it reflects the proportion of variance in item scores attributable to the common factor. Alternatively, if we are using a one-factor model, we can easily calculate $R_i^2$ by squaring the standardized factor loadings ($\lambda_i^2$). For example, see Table 7.4 for the item reliabilities using the 12 Grit items.

An important point to note is that formulation of reliability excludes any aspect of $x$ that could be explained by a variable, latent or observed, not in the model. Given that this is always likely to be the case, the exception, we can further decompose each variable into three components,

```
$x = \Lambda\xi + s + e$,
```

where $\xi$ are the latent variables in the model. In comparing this equation back to Equation 7.1, we can conceptualize $T = \Lambda\xi + s$, with the error components remaining the same. Conceptually, $s$ refers to the specific component of each variable that is not attributable to a latent variable