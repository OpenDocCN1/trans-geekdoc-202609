**Sensitivity model** Our sensitivity analysis should impose no constraints on how the *observed* data is modeled. However, sensitivity analysis demands some assumption on the relationship between the observed data and the *unobserved* confounder. It is convenient to formalize such assumptions by specifying a probabilistic model for how the data is generated. The strength of confounding is then formalized in terms of the parameters of the model (the sensitivity parameters). Then, the bias induced by the confounding can be derived from the assumed model. Our task is to posit a generative model that both yields a useful and easily interpretable sensitivity analysis, and that avoids imposing any assumptions about the observed data.

To begin, consider the functional form of the sensitivity model used by Imbens [Imb03].

```
logit(P(A=1|x,u)) = h(x) + \alpha u  (36.100)
\mathbb{E}[Y|a,x,u] = l(a,x) + \delta u, (36.101)
```

for some functions h and l. That is, the propensity score is logit-linear in the unobserved confounder, and the conditional expected outcome is linear.

By rearranging Equation (36.100) to solve for u and plugging in to Equation (36.101), we see that it's equivalent to assume \mathbb{E}[Y|t,x,u] = \tilde{l}(t,x) + \delta \text{logit P}(A=1|x,u). That is, the unobserved confounder u only influences the outcome through the propensity score. Accordingly, by positing a distribution on P(A=1|x,u) directly, we can circumvent the need to explicitly articulate U (and h).

**Definition 36.7.1.** Let \tilde{g}(x, u) = P(A=1|x,u) denote the propensity score given observed covariates x and the unobserved confounder u.

The insight is that we can posit a sensitivity model by defining a distribution on \tilde{g} directly. We choose:

```
\tilde{g}(X,U)|X \sim Beta(g(X)(1/\alpha - 1), (1 - g(X))(1/\alpha - 1)).
```

That is, the full propensity score \tilde{g}(X,U) for each unit is assumed to be sampled from a Beta distribution centered at the observed propensity score g(X). The sensitivity parameter \alpha plays the same role as in Imbens' model: it controls the influence of the unobserved confounder U on treatment assignment. When \alpha is close to 0 then \tilde{g}(X,U)|X is tightly concentrated around g(X), and the unobserved confounder has little influence. That is, U minimally affects our belief about who is likely to receive treatment. Conversely, when \alpha is close to 1 then \tilde{g} concentrates near 0 and 1; i.e., knowing U would let us accurately predict treatment assignment. Indeed, it can be shown that \alpha is the change in our belief about how likely a unit was to have gotten the treatment, given that they were actually observed to be treated (or not):

```
\alpha = \mathbb{E}[\tilde{g}(X,U)|A=1] - \mathbb{E}[\tilde{g}(X,U)|A=0]. (36.102)
```

With the \tilde{g} model in hand, we define the **Austen sensitivity model** as follows:

```
\tilde{g}(X,U)|X \sim Beta(g(X)(1/\alpha - 1), (1 - g(X))(1/\alpha - 1)) (36.103)
A|X, U \sim Bern(\tilde{g}(X,U)) (36.104)
\mathbb{E}[Y|A, X, U] = Q(A, X) + \delta(\text{logit}\tilde{g}(X, U) - \mathbb{E}[\text{logit}\tilde{g}(X, U)|A, X]). (36.105)
```