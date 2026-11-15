where **c** corresponds to the specification as defined in (7.8). Unfortunately, solving (O) is intractable due to the nonconvex constraints; it is thus natural to conduct convex relaxation on the feasible set. Specifically, we relax each \(x^{(l+1)} = \sigma^{(l)}(z^{(l)})\) by convex inequality constraints, leading to the following convex relaxation:

```
min
\(c^T x^{(L)}\) s.t. \(z^{(l)} = W^{(l)}x^{(l)} + b^{(l)}\),

\(\underline{\sigma}^{(l)}(z^{(l)}) \le x^{(l+1)} \le \bar{\sigma}^{(l)}(z^{(l)})\),

\(\underline{z}^{(l)} \le x^{(l)} \le \bar{z}_i\),

\(l \in [L]\),
(C)
```

where \(\underline{\sigma}^{(l)}(z)\) (\(\bar{\sigma}^{(l)}(z)\)) is convex (concave) and satisfies \(\underline{\sigma}^{(l)}(z) \le \sigma^{(l)}(z) \le \bar{\sigma}^{(l)}(z)\) for \(\underline{z}^{(l)} \le z \le \bar{z}^{(l)}\). The preactivation upper and lower bounds \(\bar{z}^{(l)}\) and \(\underline{z}^{(l)}\) correspond to some precomputed upper and lower bounds for each **z**. In general, we can set \(\underline{z}^{(l)} = -\infty\) and \(\bar{z}^{(l)} = \infty\) for all *l*, but tighter ranges of \(\underline{z}^{(l)}\) and \(\bar{z}^{(l)}\) can achieve tighter solutions. A typical approach is to solve (C) recursively to obtain the tightest \(\underline{z}^{(l)}\) and \(\bar{z}^{(l)}\).

In the following, we will introduce a family of linear relaxation-based methods, which can be viewed as particular cases of (C) when the nonlinear activation functions are bounded by linear upper and lower bounds.

# 8.2 Linear bound propagation methods

Linear bound propagation is a simple yet effective method for sound but incomplete verification. Note that there were several papers proposing different versions of linear bound propagation methods, such as (Wong and Kolter, 2017; Weng et al., 2018a; Zhang et al., 2018; Singh et al., 2018a, 2019b) (see Fig. 8.1). However, since they lead to similar algorithms with slightly different choices of upper/lower bounds, we will mainly focus on introducing the CROWN algorithm (Zhang et al., 2018) in this section and then talk about the relationship between CROWN and other algorithms.

The key idea is to use linear functions to bound the values of each particular neuron in any intermediate and final layer. The main difficulty for obtaining a linear bound is the nonlinear activations. If there are no nonlinear activations, then clearly any \(z^{(l)}\) can be written as a linear function to the input. Then for any output neuron \(f(\mathbf{x})\), we can write it as \(f(x) = a^T x\), where \(a\) is the slope, and in this case, verification is equivalent to