
A rigorous study has been made of applicability of adiabatic approximation on the basis of these three conditions in case of Grover’s Quantum Search under AQC framework in \[[46](#bodymatter-003.xhtml#b_9783110670707-003_ref_046)\]. It has been found that the results obtained originally by Folk theorem is still valid. As this chapter, primarily uses Grover’s search, so for rest of the chapter, the results of Folk theorem will be applied.

Grover’s Quantum Search algorithm \[[47](#bodymatter-003.xhtml#b_9783110670707-003_ref_047)\] and its variants can be used as a subroutine in designing algorithms for solving optimization problems. The variants of Grover’s search algorithm, which do not require prior knowledge of the number of target entities like Boyer’s proposal \[[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)\] and fixed point schemes \[[49](#bodymatter-003.xhtml#b_9783110670707-003_ref_049)\], are especially suited for such problems. Durr and Høyer proposed an algorithm in \[[50](#bodymatter-003.xhtml#b_9783110670707-003_ref_050)\] for finding minimum value in a database by employing the algorithm proposed in \[[48](#bodymatter-003.xhtml#b_9783110670707-003_ref_048)\] as a subroutine.

The quantum algorithm for locating minima searches for the minimum entry in an un-arranged table ‘`D`’ of `K` items, where every item has a value belonging to an ordered set. The pseudo code for quantum minimum searching algorithm is as follows:

1. Randomly select a threshold index `J[in]` ∈ [0,`K`−1].
2. Repeat till the total running time is more than 22.5√`K` + 1.4 lg² `K`.
    1. Apply the Boyer et al. quantum searching algorithm \[48\].
    2. Observe the first register: let `D`[`J[in′]`] be the outcome.
    3. If `D[J[in′]]` < `D[J[in]]`, then set threshold index `J[in]` to `J[in′]`.
3. Return `J[in]`.

The quantum minimum searching algorithm finds the index of the minimum value and it forms the inspiration for further developing optimization algorithms and heuristics, so in a way, was a path breaking research.

### 3.3.1 Oracle

A classical oracle of a function `f(x)` can be implemented reversibly as shown in the [Figure 3.1](#bodymatter-003.xhtml#b_9783110670707-003_fig_001). Similarly regular quantum oracle can be implemented as shown in [Figure 3.2](#bodymatter-003.xhtml#b_9783110670707-003_fig_002) \[[51](#bodymatter-003.xhtml#b_9783110670707-003_ref_051)\]. However, it differs from the reversible oracle as it may be given input in some superposition of basis states and produces output that may be entangled and in some superposition of basis states.

![Figure 3.1: Reversible implementation of Classical Oracle.](graphic/converted/b_9783110670707-003_fig_001.png)

Figure 3.1: Reversible implementation of Classical Oracle.

![Figure 3.2: Quantum Oracle.](graphic/converted/b_9783110670707-003_fig_002.png)

Figure 3.2: Quantum Oracle.

## 3.4 Grover’s adaptive search

Baritompa et al. generalized the quantum minimum search algorithm for solving finite global optimization problems, which have been formulated as follows \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]:

(3.12) *O**p**t**i**m**i**z**e* `f`(`α`), `α` ∈ `A`

where `f` is a real valued function on a finite set `A`.

Let the cardinality of set `A` be `N`. Let `a[1]` < `a[2]` < `a[3]` … < `a[L]` be ‘`L`’ distinct values of the objective function `f`(`α`) for all `α` in `A`. Therefore, `L` should be less than or equal to `N` i.e. if `L` would be equal to `N` then for every value of `α` in set `A`, there would be a distinct objective function value of `f`. Let there be a uniform probability measure `λ` on `A`, such that `ϒ` be the range measure given by a stochastic vector (`ϒ[1]`, `ϒ[2]`, …, `ϒ[L]`) induced by `f`, so that `ϒ[j]` = |`f^(−1)`(`a[j]`)|/`N` for `j` = 1, 2, …, `L`. Let `P[j]` = $\\sum\_{i = 0}^{j}\\Upsilon\_{j}$, the probability that a random point has value of ‘`a[j]`’ or less, i.e. `P[L]` = 1. Therefore, there is an improving region corresponding to all values of objective function `f`(`α`), which belongs to a sub-set of `A`, where `f`(`α`) has strictly better value \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]. The measure of improving region under `λ` is denoted as improving fraction `P`. So if we choose a particular value for objective function, say ‘`θ`’, then the improving region would comprise of set of all the point whose objective function values are better than ‘`θ`’.

The algorithm proposed by Baritompa et al. is known as Grover Adaptive search (GAS), which takes a sequence of rotation counts and an objective function value threshold as the input. Its pseudo code is as follows \[[52](#bodymatter-003.xhtml#b_9783110670707-003_ref_052)\]:

1. Select `α[1]` in `A`, and set `θ[1]` = `f`(`α[1]`).
2. Set count `nc` = 1.
3. While (termination condition is not met)
* {
* a. Perform a Grover search of `r[nc]` rotations on `f` with threshold `V[nc]`, and denote the outputs by `α` and `θ`.
* b. If `v` < `V[nc]`, set `θ[nc+1 ]` = `α` and `V[nc +1 ]` = `v`; otherwise, set `θ[nc+1 ]` = `θ[nc]` and `V[nc +1 ]` = `V[nc]`.
* c. `nc` = `nc` + 1.
* }

GAS has been studied using an adaptive search framework developed in \[[53](#bodymatter-003.xhtml#b_9783110670707-003_ref_053), [54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054), [55](#bodymatter-003.xhtml#b_9783110670707-003_ref_055)\] which has been applied for theoretically analyses of convergence properties of optimization methods that use stochastic global search. One of the underlying assumptions of the adaptive algorithms is that search can find better (“improving”) solutions (at some cost). GAS is based on an oracular function that can find better solutions than the current one with a finite probability in every iteration, if one exists. This oracle takes an input string `α` ∈ `A`, computes `f`(`α`), compares `f`(`α`) with current threshold and outputs zero or one depending on the result of comparison and the type of optimization problem being solved i.e. whether it is a minimization or maximization problem. Such oracles can be implemented using reversible / quantum circuits as shown in [Section 3.3.1](#bodymatter-003.xhtml#b_9783110670707-003_s_003_s_003_s_001).

Thus, GAS generates a series of domain solutions, which are uniformly distributed in the improving region of the previous solution. Further, according Theorem 1 and Corollary 6 given in \[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\], such a series converges to a global optimal solution rapidly; e.g., a unique optimal solution in a domain of size `K` can be located after 1 + ln(`K`) such improvements, in expectation \[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\].

Theorem 1 \[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\]. *The expected number of iterations, I, required for solving the finite optimization problem described by* [eq. (3.12)](#bodymatter-003.xhtml#b_9783110670707-003_eq_012) *is:*

1. $I = 1 + \\sum\\limits\_{i = 2}^{N}\\frac{\\Upsilon\_{i}}{P\_{i}}$ *for strong Pure Adaptive Search.*
2. $I = 1 + \\sum\\limits\_{i = 2}^{N}\\frac{\\Upsilon\_{i}}{P\_{i - 1}}$ *for weak Pure Adaptive Search.*

where Strong Pure Adaptive Search implies that each iteration of the search algorithm should sample objective function value from a strictly improving region. The weak Adaptive search implies that each iteration of the search algorithm should sample objective function value that is either equal or better.

### Corollary 6

\[[54](#bodymatter-003.xhtml#b_9783110670707-003_ref_054)\]. *The expected number of iterations, I, for solving finite global optimization described by* [eq. (3.12)](#bodymatter-003.xhtml#b_9783110670707-003_eq_012)*, and given a uniform distribution on the objective function values, is:*

1. *bounded above by 1 + log`N` for strong Pure Adaptive Search.*
2. *bounded above by 2 + log(`N`−*1) for weak Pure Adaptive Search.*
