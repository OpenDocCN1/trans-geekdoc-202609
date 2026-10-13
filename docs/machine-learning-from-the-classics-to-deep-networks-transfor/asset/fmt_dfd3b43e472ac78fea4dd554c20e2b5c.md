
which is known as the `loss` matrix. Note that if we set `λ[k_i] = 1, k = 1, 2, …, M`, `i = 1, 2, …, M`, `k ≠ i`, then we obtain the Bayes rule (verify it).

## Remarks 7.1

*   **The reject option**: Bayesian classification relies on the maximum value of the posterior probabilities, `P(ω_i|x), i = 1, 2, …, M`. However, often in practice, it may happen that for some vector `x`, the maximum value is comparable to the values the posterior obtains for other classes. For example, in a two-class task, it may turn out that `P(ω_1|x) = 0.51` and `P(ω_2|x) = 0.49`. If this happens, it may be more sensible not to make a decision for this particular pattern, `x`. This is known as the reject option. If such a decision scenario is adopted, a user-defined threshold value `θ` is chosen and classification is carried out only if the maximum posterior is larger than this threshold value, so that `P(ω_i|x) > θ`. Otherwise, no decision is taken. Similar arguments can be adopted for the average risk classification.

## Example 7.1

In a two-class, one-dimensional classification task, the data in the two classes are distributed according to the following two Gaussians:

```
p(x|ω_1) = \frac{1}{\sqrt{2\pi}}\exp\left( - \frac{x^{2}}{2} \right),
```

and

```
p(x|ω_2) = \frac{1}{\sqrt{2\pi}}\exp\left( - \frac{{(x - 1)}^{2}}{2} \right).
```

The problem is more sensitive with respect to errors committed on patterns from class `ω_1`, which is expressed via the following loss matrix:

```
L = \begin{bmatrix} {0\ } & 1 \\ {0.8\ } & 0 \\ \end{bmatrix}.
```
