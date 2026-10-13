
However, since `q(x)` is not known, one has to resort to approximations. In the context of diffusion models, `q(x)` refers to the pdf associated with the observed input samples. Following the rationale that underlies such models, the required approximation is achieved by gradually disturbing a given observation point, `x[0]`, via a number of steps that add noise, according to a sequence of variances, `σ[1]² < σ[2]² < … < σ[T]²`. A typical model follows conditionals, `q(x[t]|x[0])`, of the Gaussian form, `N(x[t]|x[0], σ[t]²I)`, `t = 1, 2, …, T`. For sampling purposes, the previous Gaussian assumption is expressed as

```
x[t] = x[0] + σ[t]ϵ,  ϵ ∼ N(0, I).
```

(19.73)

A noise conditional score network is a deep neural network, which is trained to *estimate* the score function `∇[x[t]] ln q(x[t]|x[0])`. Ideally, one would like to obtain estimates of `∇[x[t]] ln q(x[t])`, but this is not, in general, computationally tractable. So we rest on the corresponding conditionals, as we did with the DDP models. Due to the Gaussian assumption, i.e., `N(x[t]|x[0], σ[t]²I)`, it is trivial to show that
