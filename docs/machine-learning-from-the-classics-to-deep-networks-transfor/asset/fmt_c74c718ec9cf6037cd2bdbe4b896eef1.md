
## 8.11 Regret analysis

A major effort when dealing with iterative learning algorithms is dedicated to the issue of convergence; where the algorithm converges, under which conditions it converges, and how fast it converges to its steady state. A large part of Chapter [5](#Chp005_177-248_B9780443292385000111.xhtml) was focused on the convergence properties of the LMS. Furthermore, in the current chapter, when we discussed the various subgradient-based algorithms, convergence properties were also reported.

In general, analyzing the convergence properties of online algorithms tends to be quite a formidable task and classical approaches have to adopt a number of assumptions, sometimes rather strong. Typical assumptions refer to the statistical nature of the data (e.g., being i.i.d. or the noise being white). In addition, it may be assumed that the true model, which generates the data, to be known, and/or that the algorithm has reached a region in the parameter's space that is close to a minimizer.

More recently, an alternative methodology has been developed which bypasses the need for such assumptions. The methodology evolves around the concept of `cumulative loss`, which has already been introduced in Chapter [5](#Chp005_177-248_B9780443292385000111.xhtml), Section [5.5.2](#Chp005_177-248_B9780443292385000111.xhtml). The method is known as `regret analysis`, and its birth is due to developments in the interplay between game and learning theories (see, for example, [21]).

Let us assume that the training samples (`y[n]`, `x[n]`), `n = 1, 2, ...`, arrive sequentially and that an adopted online algorithm makes the corresponding predictions, `ŷ[n]`. The quality of the prediction for each time instant is tested via a loss function, `L(y[n], ŷ[n])`. The cumulative loss up to time `N` is given by

### Algorithm Steps

3.  **θₙ = (1 - μₙλ)θₙ₋₁ + (μₙ/m) Σₖ∈Aₙ yₖ xₖ**

```
θₙ = (1 - μₙλ)θₙ₋₁ + (μₙ/m) Σₖ∈Aₙ yₖ xₖ
```

4.  **θₙ = min(1, 1/(√λ ||θₙ||)) θₙ** (Optional)

```
θₙ = min(1, 1/(√λ ||θₙ||)) θₙ
```

*   **End For**

Application of regret analysis arguments points out the required number of iterations for obtaining a solution of accuracy `ϵ` is `O(1/ϵ)`, when each iteration operates on a single training sample. The algorithm is very similar with the algorithms proposed in [45, 112]. The difference lies in the choice of the step size. We will come back to these algorithms in Chapter [11](#Chp011_519-582_B9780443292385000172.xhtml). There, we are going to see that the online learning in infinite-dimensional spaces is more tricky. In [73], a number of comparative tests against well-established support vector machine algorithms have been performed using standard data sets. The main advantage of the algorithm is its computational simplicity, and it achieves comparable performance rates at lower computational costs.
