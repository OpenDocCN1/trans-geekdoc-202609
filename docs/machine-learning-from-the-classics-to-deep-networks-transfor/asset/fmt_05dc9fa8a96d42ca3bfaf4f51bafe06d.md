
### Stick breaking construction

As was the case with the CRP, the restaurant construction of an IBP fits nicely when inference is done via Monte Carlo sampling, e.g., Gibbs sampling (Chapter [14](#Chp014_717-754_B9780443292385000202.xhtml)). However, when variational approximation methods are to be used, a stick breaking construction is more appropriate.

Choose a beta distribution, `Beta(β|α, 1)`. Sample `β₁ ∼ Beta(β|α, 1)` and set `P₁ = β₁`. Then the `k`th step of the algorithm is given by:

```
[Equation image: images/B9780443292385000196/fx021.jpg]
```

#### Properties of the IBP

*   The number `K₊` of nonzero rows of `Z` is also distributed according to a Poisson with parameter `αH_N`, i.e.,

    ```
    P(K₊; αH_N) = (αH_N)^K₊ exp(-αH_N) / K₊!
    ```

*   As `K → ∞`, matrix `Z` remains *sparse*. As a matter of fact, the number of nonzero elements follows a Poisson distribution with parameter `αN` and its mean value is `αN`. Furthermore, the probability of nonzero values higher than the mean decreases *exponentially*. Also, taking into account that the mean value of a Poisson is equal to its parameter, the average number of dishes selected (features used) is equal to `αH_N` (e.g., [23]). That is, for a fixed `N`, the larger the concentration parameter is, the more dishes are selected.

In analogy to [Fig. 13.14](#Chp013_635-716_B9780443292385000196.xhtml#f0080), [Fig. 13.18](#Chp013_635-716_B9780443292385000196.xhtml#f0115) shows the distribution of dishes per customer for a specific choice of the `α` parameter. In CRP, each customer is associated with a *single* table. In CRP, the crucial point is how many customers sit at the same table. In IBP, each customer is associated with *multiple* dishes and the crucial point is how many customers select the same dishes. Note that the number of new dishes keeps decreasing fast. Dishes associated with the first (top) rows are shared by many customers. The dishes associated with rows to the bottom of the figure are shared by fewer and fewer customers.

![Figure 13.18 The distribution of dishes per customer. Each new customer selects some of the previously selected dishes and some new ones. Observe that the probability of selecting a new one decreases fast.](images/B9780443292385000196/gr018.jpg)

[Fig. 13.19](#Chp013_635-716_B9780443292385000196.xhtml#f0120) shows the evolution of the number of dishes per customer, for two different concentration parameters. To avoid confusion, note that, for practical reasons for saving space in presenting the figure, customers correspond to rows and dishes to columns (in contrast to [Fig. 13.18](#Chp013_635-716_B9780443292385000196.xhtml#f0115)). The larger the concentration parameter is, the more dishes (features) are selected, which is in line with what has been said before in relation to Eq. [(13.133)](#Chp013_635-716_B9780443292385000196.xhtml#deq207).

![Figure 13.19 In this figure, customers are shown in rows and dishes in columns, for graphical convenience. Gray squares correspond to selected dishes. Note that as the concentration parameter increases, more dishes are selected.](images/B9780443292385000196/gr019.jpg)
