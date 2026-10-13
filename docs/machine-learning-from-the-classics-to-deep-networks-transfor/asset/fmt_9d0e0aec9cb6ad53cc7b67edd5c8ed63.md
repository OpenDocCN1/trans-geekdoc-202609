
where the spectral norm of a matrix has been used (Section [6.4](#Chp006_249-291_B9780443292385000123.xhtml)) and `λ_max` denotes the maximum eigenvalue of `X^T X`. Thus, if

```
μ ∈ (0, 2/λ_max),
```

the corresponding iterations in Eq. [(8.62)](#Chp008_343-416_B9780443292385000147.xhtml#deq128) converge to a solution of [(8.50)](#Chp008_343-416_B9780443292385000147.xhtml#deq110). The scheme has been used in the context of sparsity promoting learning, where (as we will see in Chapter [10](#Chp010_463-518_B9780443292385000160.xhtml)) the task of interest is

```
minimize ½‖y - Xθ‖², subject to ‖θ‖₁ ≤ ρ.
```

Then it turns out that projecting on the `ℓ₁` ball (corresponding to `C`) is equivalent to a soft thresholding operation^([^(56)](#fn56)).

#### Projected subgradient method

Starting from an arbitrary point `θ^(0)`, for the recursion [2,55]

```
(8.62)
```

*   either a solution of [(8.50)](#Chp008_343-416_B9780443292385000147.xhtml#deq110) is achieved in a finite number of steps,
*   or the iterations converge (weakly in the general case) to a point in the set of solutions of [(8.50)](#Chp008_343-416_B9780443292385000147.xhtml#deq110),

provided that

```
∑_{i=1}^{∞} μ_i = ∞, ∑_{i=1}^{∞} μ_i² < ∞.
```

Another version of the projected subgradient algorithm was presented in [70]. Let `J_* = min_θ J(θ)` be the minimum (strictly speaking, the infimum) of a cost function, whose set of minimizers is assumed to be nonempty. Then the iterative algorithm

```
(8.63)
```

converges (weakly in infinite-dimensional spaces) for `μ_i ∈ (0, 2)`, under some general conditions, and assuming that the subgradient is bounded. The proof is a bit technical and the interested reader can obtain it from, for example, [70,82].

Needless to say that, besides the previously reported major schemes discussed, there is a number of variants; for a related review see [82].

### 8.10.3 Online learning for convex optimization

Online learning in the framework of the squared error loss function has been the focus in Chapters [5](#Chp005_177-248_B9780443292385000111.xhtml) and [6](#Chp006_249-291_B9780443292385000123.xhtml). One of the reasons that online learning was introduced was to give the potential to the algorithm to track time variations in the underlying statistics. Another reason was to cope with the unknown statistics when the cost function involved expectations, in the context of the stochastic approximation theory. Moreover, online algorithms are of particular interest when the number of the available training data and the dimensionality of the input space become very large, compared to the load that today's storage, processing, and networking devices can cope with. Exchanging information has now become cheap and data sets have been populated with a massive number of data. This has rendered batch processing techniques for learning tasks with huge data sets impractical. Online algorithms that process one data point at a time have now become an indispensable algorithmic tool.

Recall from Section [3.14](#Chp003_65-117_B9780443292385000093.xhtml) that the ultimate goal of a machine learning task, given a loss function `ℒ`, is to minimize the expected loss/risk, which in the context of parametric modeling can be written as
