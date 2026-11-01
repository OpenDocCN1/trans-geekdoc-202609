
In sensory cortical areas there are many topographic maps that represent two or more dimensions of a stimulus (e.g., retinal position and edge orientation); localized activity in these maps represent conjunctions of values on these dimensions. Similarly, quantum computational maps can represent conjunctions of values as inputs or outputs of functions.

Suppose we want to compute a function `f` : `Ω` × `Ω` → `Ω′`, where `Ω` = {`x[1]`,…, `x[n]`} and `Ω′` = {`y[1]`,…, `y[n]`}. We will represent the input to the function by a two-dimensional array of qubits for each (`x[j]`, `x[k]`) pair. (They do not have to be physically arranged as a two-dimensional array so long as there is a qubit for each pair of values.) This will require `n²` qubits, but we are assuming that `n` is small because low precision is adequate for neural networks. Therefore we expect the 2D map to comprise typically several thousand qubits. The qubits representing the (`x[j]`, `x[k]`) pairs are then mapped to the qubits representing the outputs `f(x[j], x[k])` by the method described in `Prop. 5`.

The `n²` conjunctions are computed by `n²` `CCNOT` gates, each of which requires a `|0⟩` ancilla and generates two extra qubits (containing the inputs) in addition to the conjunction. However, these extra qubits are passed along the rows and columns to be used in other conjunctions, and so there are only `2n` total garbage qubits. In summary, there are `2n` + `n²` input qubits (including `n²` ancillae) and `n²` + `2n` output qubits (including `2n` garbage). That is, if `|ϕ[j]⟩` is the state of element `j` of one input map, and `|ψ[k]⟩` is the state of element `k` of the other input map, then the state `|χ[jk]⟩` of element (`j, k`) of the two-dimensional map is computed by

```
(2.36) |ϕ[j]⟩|ψ[k]⟩|χ[jk]⟩ = CCNOT |ϕ[j]⟩|ψ[k]⟩|0⟩.
```

`If` `|ϕ[j]⟩` = `p′|0⟩` + `p|1⟩` and `|ψ[k]⟩` = `q′|0⟩` + `q|1⟩`, then the result of `CCNOT` is

```
|ϕ[j]⟩|ψ[k]⟩|χ[jk]⟩ = p′q′|000⟩ + p′q|100⟩ + p q′|010⟩ + p q|111⟩.
```

The qubits are entangled, but the conjunction computes probability-like amplitudes if we interpret the squares of the amplitudes as probabilities.

Based on the foregoing, we define a unitary operator `U[OP]` on a `n² + 2n` dimensional Hilbert space that does what amounts to an outer product on two one-dimensional maps to compute a two-dimensional map:

```
(2.37) |φ⟩|ψ⟩|χ⟩ = U[OP] |φ⟩|ψ⟩|0⟩^(⊗ n²),
```

where inputs `|φ⟩` and `|ψ⟩` are `n`-dimensional, and output `|χ⟩` is `n²`-dimensional and computed by [eq. (2.36)](#bodymatter-002.xhtml#b_9783110670707-002_eq_054).

To illustrate the use of computational maps to implement binary operations, we will use a simple, useful function, addition. We want to define `sum` : `Ω` × `Ω` → `Ω′` so that `sum(x, y)` = `x + y`, but we have a problem, since the maximum value of `x + y` is greater than the maximums of `x` and `y`. Since the range of numbers represented by our maps is quite limited, this is a more serious problem than overflow in binary addition. One solution is to make the codomain map large enough; for example, if `Ω` = {0, `Δx`, 2`Δx`,…, (`n`−1)`Δx`}, then let `Ω′` = {0, `Δx`, 2`Δx`,…, 2(`n`−1)`Δx`}. Generally, however, it is more convenient to have the codomain map be the same as the domain maps, since this facilitates composing functions. Therefore, another solution is to scale either the inputs or the output so that we compute, for example, `h sum(x, y)` = (`x`+`y`)/2; this is often useful if we know that we are going to scale the quantities anyway. A third option is to compose addition with a squashing function, so that we compute, for example, the truncated `tsum(x, y)` = min(`x`+`y`, `x[n]`), where `x[n]` = max `Ω`. This is the solution that we will use for illustration.

If `Ω` = {0, `Δx`,…, (`n`−1)`Δx`}, then the (`j, k`) element of the two-dimensional qubit map will represent the pair of inputs ((`j`−1)`Δx`, (`k`−1)`Δx`). This will be mapped to the sum (`j`+`k`−2)`Δx` if `j` + `k` − 2 < `n` − 1, and to the maximum value (`n`−1)`Δx` otherwise. Therefore the constant `j` + `k` anti-diagonals above the `j` + `k` = `n` + 1 anti-diagonal each map to one value, (`j`+`k`−2)`Δx`, which is the sum of (`j`−1)`Δx` and (`k`−1)`Δx`. The elements below the `j` + `k` = `n` + 1 anti-diagonal all map to the same (`n`−1)`Δx` value, since the sum is above the maximum representable value in the topographic map.

`Proposition 5` shows how to implement the truncated addition, but it treats it as a unary function on an `n²`-dimensional space, which is wasteful since the intended output (the sum) is `n`-dimensional and the remaining `n²` − `n` elements are garbage. Therefore, we implement a unitary operator that directly maps the input pairs to the corresponding outputs.

To compute the outer product we require `n²` constant `|0⟩` ancillae, and this computation also passes the two `n`-dimensional inputs through as garbage output. The qubit representing (0, 0) maps bijectively to the output qubit `y[1]` representing 0. Each of the other `n` − 1 output qubits `y[i]` (`i` = 2,…, `n`) has two or more domain pairs mapping to it. As before, let `n[i]` be the preimage multiplicity of output `i` and note that `∑_{i = 1}^{n} n_i = n²`. Each of these non-injective outputs receives its value from an `OR[n[i]]` operation, which requires `n[i]` − 1 input `|1⟩` ancillae and generates `2n[i]` − 2 qubits of output garbage (`n[i]` for the negated inputs and `n[i]` − 1 for the intermediate disjunctions). Therefore, the total number of `|1⟩` ancillae is

```
∑_{i = 2}^{n} (n_i - 1) = ∑_{i = 2}^{n} n_i - (n - 1) = (n² - 1) - n + 1 = n² - n.
```

Moreover, the complete input dimension is `2n` + `n²` + `n²` − `n` = `2n²` + `n`.

This is also the complete output dimension, for we have `n` qubits for the function value, `2n` qubits for the passed-through input arguments (garbage), and the garbage output from the `OR` gates, which is:

```
∑_{i = 2}^{n} (2n_i - 2) = 2(n² - n).
```

That is, the complete output dimension is `3n` + `2(n² - n)` = `2n²` + `n`.

In summary, there is a unitary operator `U[tsum]` ∈ `ℒ(ℋ^{2n² + n}, ℋ^{2n² + n})` so that

```
(2.38) U[tsum] |{x}⟩ |{y}⟩ |0⟩^(⊗ n²) |1⟩^(⊗ n(n - 1)) = |{tsum(x, y)}⟩ |{x}⟩ |{y}⟩ |γ⟩,
```

where the garbage `|γ⟩` has dimension `2n(n - 1)` (the passed-through inputs may also be considered garbage).

Based on this example, we state a more general result.

### Proposition 6

Suppose `f` : `Ω` × `Ω` → `Ω`, and let `n` = |`Ω`|. Let `m_nr` ≜ `n - |Im f|` be the number of codomain elements that are not in the range of `f`. Then there is a unitary operator `U[f]` ∈ `ℒ(ℋ, ℋ)`, where `ℋ` is `2n² + n + 2m[nr]` dimensional Hilbert space, such that:

```
(2.39) U[f] |{x}⟩ |{y}⟩ |0⟩^(⊗ (n² + m[nr])) |1⟩^(⊗ (n² - n + m[nr])) = |{f(x, y)}⟩ |{x}⟩ |{y}⟩ |γ⟩,
```

where the garbage `|γ⟩` has dimension `2(n² - n + m[nr])` (the `2n` passed-through inputs may also be considered garbage).

### Proof:
