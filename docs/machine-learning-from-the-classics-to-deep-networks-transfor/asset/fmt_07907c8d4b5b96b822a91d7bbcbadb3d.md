
## 12.9 Combining learning models: a probabilistic point of view

The idea of combining different learners to boost the overall performance by exploiting their individual characteristics was introduced in Section [7.9](#Chp007_293-342_B9780443292385000135.xhtml). We now return to this task via probabilistic arguments. The section is also useful from a pedagogical point of view, to familiarize the reader further with the use of the EM algorithm.

Our starting consideration is that the data are distributed in different regions of the input space. Thus, it seems reasonable to fit different learning models, one for each region. This idea reminds us of the decision trees treated in Chapter [7](#Chp007_293-342_B9780443292385000135.xhtml). There, axis-aligned (linear) splits of the input space were performed. Here, the input space will be split via hyperplanes (generalizations to more general hypersurfaces are also possible) in a general position. Moreover, the main difference lies in the fact that in CARTS, the splits were of the hard-type decision rule. In the current setting, we adopt a more relaxed attitude and we are going to consider soft-type probabilistic splits, at the expense of some loss in interpretability.

The ME estimate is of an exponential form:

```
p̂(x) = C exp( ∑_{i ∈ I} θ_i u_i(x) )
```

The parameters `θ[i]`, `i ∈ I`, are the Lagrange multipliers used in the optimization task and their values are determined via the constraints and are given in terms of the available empirical expectations, `μ̂[i]`, `i ∈ I`. If no constraint is used other than the obvious (normalizing) one and `A[x] = [a, b] ⊂ R`, then the resulting PDF is the uniform distribution, `p(x) = C`; indeed, this is the most random one, because it shows no preference for any specific interval of values. If two constraints are used such that `u[1](x) = x` and `u[2](x) = x²` the resulting PDF is the Gaussian one, because the exponent is of a quadratic form (see chapter's appendix). In other words, the Gaussian is the most random PDF, subject to two constraints related to the mean and the variance. Note that although we focused on real-valued random variables, everything is trivially extended to vector-valued ones. An interesting discussion concerning the ME method and alternative views of the problem is provided in [42].
