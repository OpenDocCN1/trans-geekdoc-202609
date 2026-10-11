
Furthermore, any unitary quantum parametric gates can be rewritten as `V[l](θ[l]) = exp(iθ[l]H[l])`, where `H[l]` refers to the Hermitian generator of the gate `V[L]`. The approximation to the Fubini–Study metric tensor admits that for each parametric layer `l` in the variational quantum circuit, the `n[l] × n[l]` block-diagonal submatrix of the Fubini–Study metric tensor `g[l, i, j]^+` is calculated by

```
g[l, i, j]^+ = ⟨ψ[l]|H[l](i)H[l](j)|ψ[l]⟩ − ⟨ψ[l]|H[l](i)|ψ[l]⟩⟨ψ[l]|H[l](j)|ψ[l]⟩,
```
(18.8)

where

```
|ψ[l]⟩ = V[l](θ[l])W[l] ··· V[1](θ[1])W[1]|ψ[0]⟩.
```
(18.9)

Note that `|ψ[l]⟩` in Eq. (18.9) denotes the quantum state before the application of the parameterized layer `l`. Fig. 18.4 illustrates a simplified version of a VQC, where `W[1]` and `W[2]` are related to non-parametric gates, and `V[1](θ[0], θ[1])` and `V[2](θ[2], θ[3])` correspond to the parametric gates with adjustable parameters, respectively. Since there are two layers, each of which owns two free parameters, the block-diagonal approximation is composed of two `2 × 2` matrices, `g[1]^+` and `g[2]^+`, which can be respectively expressed as

```
g_1^+ = [[⟨z_0^2⟩ − ⟨z_0⟩^2, ⟨z_0 z_1⟩ − ⟨z_0⟩⟨z_1⟩],
         [⟨z_0 z_1⟩ − ⟨z_0⟩⟨z_1⟩, ⟨z_1^2⟩ − ⟨z_1⟩^2]]
```
(18.10)

and

```
g_2^+ = [[⟨y_1^2⟩ − ⟨y_1⟩^2, ⟨y_1 x_2⟩ − ⟨y_1⟩⟨x_2⟩],
         [⟨y_1 x_2⟩ − ⟨y_1⟩⟨x_2⟩, ⟨x_2^2⟩ − ⟨x_2⟩^2]].
```
(18.11)

**Figure 18.4** A demonstration of the VQC approximation method based on the Fubini–Study metric tensor: (a) A block-diagonal approximation to VQC based on the Fubini–Study metric tensor; (b) a measurement of `z[0]`, `z[1]` for `|ψ[0]〉`; (c) measurement of `y[1]`, `x[2]` for `|ψ[1]〉`.

The elements of `g[1]^+` and `g[2]^+` compose `g^+(θ)` as

```
g^+(θ) = [[g_1^+, 0],
          [0, g_2^+]].
```
(18.12)

Then, we employ Eq. (18.4) to update the VQC parameter `θ`.

## 18.5 Federated quantum natural gradient descent

**Algorithm 1** Iterative approximation.

A QFL system can be built by setting up VQC models in an FL manner, given the dataset `S` composed of subsets `S[1], S[2], …, S[K]`, the objective of QFL can be formulated as

```
min_θ Σ_{k=1}^K w_k g_k^+(θ) L(θ; S_k),
```
(18.13)

where `w[k]` refers to the coefficient assigned to the `k`th gradient participant, and each `w[k]` can be estimated as

```
w_k = |S_k| / |S| = |S_k| / Σ_{k=1}^K |S_k|.
```
(18.14)

The QNGD algorithm is applied for each VQC and the uploaded gradients of all VQCs are aggregated to update the model parameters of the global VQC. The FQNGD can be mathematically summarized as

```
θ̄_{t+1} = θ̄_t − η Σ_{k=1}^K (|S_k| / |S|) g_k^+(θ_t^(k)) ∇L(θ_t^(k); S_k),
```
(18.15)

where `θ̄_t` and `θ_t^(k)` respectively correspond to the model parameters of the global VQC and the `k`th VQC model at epoch `t`, and `N[k]` represents the amount of training data stored in the participant `k`, and the sum of `K` participants' data is equivalent to `N`.

Compared with the SGD counterparts used for QFL, the FQNGD algorithm admits adaptive learning rates for the gradients such that the convergence rate could be accelerated according to the VQC model status.

## 18.6 Experimental results

To demonstrate the FQNGD algorithm for QFL, we perform the binary and ternary classification tasks on the standard MNIST dataset [9], with digits `{2, 5}` for the binary task and `{1, 3, 7}` for the ternary one. There are 11379 training data and 1924 test data for the binary classification, and 19138 training data and 3173 test data are assigned for the ternary classification. As for the setup of QFL in our experiments, the QFL system consists of 6 identically local VQC participants, each of which owns the same amount of training data. The test data are stored in the global part and are used to evaluate the classification performance.

We compare our proposed FQNGD algorithm with other three optimizers: the naive SGD optimizer, the AdaGrad optimizer [20], and the Adam optimizer [18]. The AdaGrad optimizer is a gradient descent optimizer with a past-gradient-dependent learning rate in each dimension. The Adam optimizer refers to the gradient descent method with an adaptive learning rate as well as adaptive first and second moments. (See Tables 18.1 and 18.2.)

**Table 18.1** The simulation results of a binary classification in terms of accuracy.
