
where `K+` is the number of nonzero rows in the class and `H_N = \sum_{j = 1}^{N}\frac{1}{j}` is a constant. The exact form of the involved constants in the above proportionality relation is of no importance to us (see, e.g., [23] for details).

Having derived the above prior probability over the class of binary matrices, the issue now is how one can sample from or implement such a distribution in practice. In the same vein as with the DPs in Section [13.11.2](#Chp013_635-716_B9780443292385000196.xhtml#s0110), there are two alternatives.

#### Restaurant construction

In analogy to the CRP, it turns out that the following metaphor is a way to sample from the prior in Eq. [(13.132)](#Chp013_635-716_B9780443292385000196.xhtml#deq204). Imagine that the columns of `Z` correspond to customers and that the rows correspond to dishes in an infinitely long buffet, which is inspired by the large variety of dishes in a typical Indian restaurant! This is the reason that the method is known as the *Indian buffet process* (IBP).

1.  **1.** The first customer, `n = 1`, takes `K^(1)` dishes, according to a Poisson distribution with parameter `α`, i.e.,

```
P(K^(1); α) = (α^K(1) exp(-α)) / K^(1)!.
```

2.  **2.** The `n`th customer takes dishes that have been previously sampled with probability `m_k / n`, where `m_k` is the number of customers who have sampled the `k`th dish (feature). He/she also takes `K^(n)` new dishes, according to the Poisson distribution with parameter `α/n`, i.e.,

```
P(K^(n); α/n) = ((α/n)^K(n) exp(-α/n)) / K^(n)!.
```

Thus, after `N` customers have been served, a matrix `Z ∈ ℝ^(K+ × N)` is formed, with `K+` being the total number of dishes that have been sampled. It can be shown that following such a sampling procedure, as `K → ∞`, the probability of any equivalence class `P([Z])` is equal to that in Eq. [(13.132)](#Chp013_635-716_B9780443292385000196.xhtml#deq204) (e.g., [23]). It turns out that:
