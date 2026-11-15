Different implementations usually use slightly different branching heuristics.

# 9.3 Branch-and-bound with linear bound propagation

Although linear programming (LP) can provide tight bounds for each sub-domain when conducting BaB, they are usually time consuming to solve and cannot fully exploit the parallelization provided by GPUs or TPUs. Therefore many recent works applied incomplete verification solvers mentioned in the previous chapter to efficiently rule out some regions and provide guidance to BaB (Bunel et al., 2020a; Xu et al., 2021). In particular, Xu et al. (2021) combines BaB with a linear propagation-based incomplete verifier CROWN to conduct complete verification.

The main challenge of using linear propagation-based incomplete verifiers to BaB is to combine the split constraint ($z \ge 0$ or $z < 0$ for a neuron $z$) into the linear propagation procedure. One simple way to do that is to just use it as a pre-activation bound for each neuron ($l, u$ in (9.4)), but this is insufficient as the pre-activation constraint does not eliminate all the inputs outside the domain. Therefore, algorithms such as (Xu et al., 2021) incorporates the split constraints using Lagrangian multipliers. More specifically, linear propagation methods lead to the following minimization problem for verification:

```
$\min_{x \in C} f(x) \ge \min_{x \in C} w^T D z,$
```

where $z$ is the values of some layer of neural network and $D$ is the diagonal matrix derived from bounding each neurons (see Lemma 1 in Chapter 8). The split constraint can then be added into this formulation as

```
$\min_{x \in C} f(x) \ge \min_{x \in C} w^T D z, \ S z \le 0,$ (9.5)
```

where $S$ is a diagonal matrix with $+1, -1, 0$ on the diagonal, indicating the split constraints (postive, negative or no split). Optimizing (9.5) will then lead to the optimal solution within the constraint set. To deal with the constraint minimization problem, a standard approach is to transform it into an uncinstrained problem with Lagrangian multipliers:

```
$\min_{x \in C} f(x) \ge \max_{\beta \ge 0} \min_{x \in C} w^T D z + \beta S z,$ (9.6)
```

where $\beta$ are the multipliers. We can thus merge the two linear terms in the objective together, which reduced to the linear propagation method, with