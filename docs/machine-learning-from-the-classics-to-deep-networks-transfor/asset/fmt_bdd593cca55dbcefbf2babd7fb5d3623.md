
Note that although `λ[t]` guarantees optimality, in practice it can get relatively large values for some time steps `t` (recall that `σ[t]² = β[t]`). In [85], it is pointed out that setting `λ[t] = 1` results in good performance. Other, more “fancy,” choices for the weighting sequence have also been proposed, see, e.g., [37].

The cost function to be minimized results from the bound in Eq. [(19.64)](#Chp019_997-1102_B9780443292385000251.xhtml#deq138), after taking the expectation over all observations, `x[0]`. Moreover, note that the involved conditional expectation with respect to `q(x[t]|x[0])` is equivalent with taking the expectation with respect to `p(ϵ) = N(ϵ|0, I)`, from Eq. [(19.59)](#Chp019_997-1102_B9780443292385000251.xhtml#deq135). Hence, for the case of the simplified model, the contribution to the cost of the second component becomes

```
∑_{t=2}^{T} E_{x_0 ~ q(x_0)} E_{ϵ ~ N(0,I)} [ λ_t || ϵ - ϵ_θ(x_t, t) ||^2 ]
```
(19.70)

where `x[t]` is given in terms of `ϵ` in Eq. [(19.59)](#Chp019_997-1102_B9780443292385000251.xhtml#deq135). In practice, expectations are replaced by sample means. In [85], it is suggested that instead of summing up the terms over time t, one can randomly select a time index in `[1, T]` using uniform sampling and perform parameter updating based on the corresponding term. The second expectation with respect to noise is approximated by a single sample. [Algorithm 19.4](#Chp019_997-1102_B9780443292385000251.xhtml#enun0090) summarizes the training steps. The term `f_θ(·)` denotes the output of the parameterized neural network.

### Algorithm 19.4: Training the DDP model

**Repeat**

1. `x[0] ~ q(x[0])`; New input observation.
2. `t ~ U[1, T]`; Uniform discrete distribution.
3. `ϵ ~ N(0, I)`; Sample from the standard Gaussian.
