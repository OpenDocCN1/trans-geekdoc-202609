
where `ϕ(x; θ[k]) ∈ {−1, 1}` is the base classifier at iteration `k`, defined in terms of a set of parameters, `θ[k]`, `k = 1, 2, …, K`, to be estimated. The base classifier is selected to be a binary one. The set of unknown parameters is obtained in a *step-wise* approach and in a *greedy* way; that is, at each iteration step `i`, we only optimize with respect to a single pair, `(a[i], θ[i])`, by keeping the parameters `a[k], θ[k]`, `k = 1, 2, …, i − 1`, obtained from the previous steps, fixed. Note that ideally, one should optimize with respect to all the unknown parameters, `a[k], θ[k]`, `k = 1, 2, …, K`, simultaneously; however, this would lead to a very computationally demanding optimization task. Greedy algorithms are very popular, due to their computational simplicity, and lead to a very good performance in a wide range of learning tasks. Greedy algorithms will also be discussed in the context of sparsity-aware learning in Chapter [10](#Chp010_463-518_B9780443292385000160.xhtml).

Assume that we are currently at the `i`th iteration step; consider the partial sum of terms

```
F_i( · ) = ∑_{k = 1}^{i} a_k ϕ( · ; θ_k).
```
(7.85)

Then we can write the following recursion:

`F[i](·) = F[i − 1](·) + a[i]ϕ(·; θ[i]), i = 1, 2, …, K,`
(7.86)

starting from an initial condition. According to the greedy rationale, `F[i − 1](·)` is assumed to be known and the goal is to optimize with respect to the set of parameters `a[i], θ[i]`. For optimization, a loss function has to be adopted. No doubt different options are available, giving different names to the derived algorithms. A popular loss function used for classification is the exponential loss, defined as

![Equation](images/B9780443292385000135/fx017.jpg)
(7.87)
