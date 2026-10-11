
In [Figure 7.9](#9783110785937_078254.xhtml#b_9783110785944-007_fig_009), the steps for extracting the temperature-dependent error model of FeFET transistors are shown. The entire FeFET device has been implemented and modeled in the Technology CAD (TCAD) framework (Synopsys Sentaurus [[656]](#backmatter-001.xhtml#b_9783110785944-010_ref_656)). The variation in the underlying transistor and the added ferroelectric layer are considered. After incorporating the temperature and variation effects in the calibrated TCAD models, Monte-Carlo simulations for the entire FeFET device are performed. Then the probability of error is extracted for a certain read voltage, i.e. the probability that logic ‘0’ is read as logic ‘1’ and a logic ‘1’ is read as logic ‘0’. Details on device physics modeling and reliability analysis for FeFET under the effects of temperature variability (runtime) and manufacturing (design-time) variability can be found in [[280]](#backmatter-001.xhtml#b_9783110785944-010_ref_280) and [[534]](#backmatter-001.xhtml#b_9783110785944-010_ref_534), respectively.

### 7.2.3 Binarized Neural Networks

Traditional neural networks use floating-point (e.g., 32 bits) or integer values (e.g., 8 bits) to represent the ANN parameters (i.e., weights, activations, inputs, etc.). In such a case, the position of the occurred bit error (i.e., the bit flip in the value) does matter. Specifically, in floating-point ANNs, a one-bit error in one weight can cause the prediction of the ANN to become useless (see e.g. [[381]](#backmatter-001.xhtml#b_9783110785944-010_ref_381)). This typically occurs when a bit flip in the exponent of the floating-point representation occurs leading to an error with an unacceptable magnitude. As mentioned before, BNNs are resource-efficient neural networks that are ideally suited for small devices. Additionally, they can be trained to be resilient against bit errors, which makes them ideal candidates for approximate memories. In BNNs each weight (and possibly each activation) is stored in a single bit `{0, 1}`. Hence, a bit error in a binary weight or binary input causes a change of the computation result by merely 1, reducing its overall impact. In addition to the reduced impact of bit errors and reduced memory footprint due to smaller weights the execution of BNNs also becomes simpler. Consider, for example, the output of the fully connected `l`-layer with activation `σ` and weights `W[l]`

(7.1) `f^(l)(X) = σ(W^(l)X)` (7.1)

In regular floating-point neural networks, the execution of this layer requires the repeated computation of matrix-vector products `W[l]X` as well as the application of `σ`. In a BNN this operation becomes

(7.2) `2 popcount (XNOR(W^(l),X)) − B > T` (7.2)

where `popcount` counts the number of 1s in the XNOR-result, `B` is the number of bits in the XNOR operands, and `T` is a learnable threshold parameter if batch normalization layers are used, whose comparison produces binary values (representing a shifted binarization function) [325, 609].

A common method of training ANNs is to apply stochastic gradient descent (SGD) with mini-batches. Let `𝒟 = {(x[1], y[1]), ..., (x[I] , y[I])}` be the training data with `x[i] ∈ 𝒳` as the inputs, `y[i] ∈ 𝒴` as the labels, and `ℓ : 𝒴×𝒴 → ℝ` as the loss function. `W = (W[1], ..., W[L])` are the weight tensors of layer 1 `... L` and `f[W](x)` is the output of the ANN. The goal is to find a solution for the optimization problem

(7.3) `argmin_W (1/I) ∑_{(x,y) ∈ 𝒟} ℓ(f_W(x), y)` (7.3)

with a mini-batch SGD strategy that computes gradients using backpropagation.

To train BNNs, Hubara et al. [[325]](#backmatter-001.xhtml#b_9783110785944-010_ref_325) proposes to deterministically binarize the weights and activations during the forward pass. For backpropagation, the floating-point numbers are used for parameter updates. This leads to training times similar regular ANNs but assumes binary values during the forward pass. More formally, let `b : ℝ → {−1, +1}` be a binarization function with

(7.4) `b(x) = 1 if x > 0 else -1` (7.4)

and let `B(W)` denote the element-wise application of `b` to a tensor `W`. Now we simply apply `B` during the forward pass to each weight tensor. During the backward pass, the authors propose using full floating point precision, whereas during the backward-pass they replace the gradient of `b` with the straight-through estimator. Consider the forward computation `Y = B(X)`. Let `∇[Y] ℓ` denote the gradient with respect to `Y`. The straight-through estimator approximates

(7.5) `∇[X]ℓ := ∇[Y]ℓ` (7.5)

essentially pretending that `B` is the identity function. Algorithm 5 summarizes this approach.

**Algorithm 5:** Binarized forward pass for a network with `L` layers, each with weight tensors `W[l]` performing a generic operation `∘[l]` (e.g. a convolution).

**1 for** `l ∈ {1, ..., L}` **do**

**2** `x ← B(B(W[l]) ∘[l] x)`

#### 7.2.3.1 Flip Regularization

To make BNNs bit error-tolerant, the state-of-the-art method is bit flip injections in the binarized values during the forward pass, as proposed by Hirtzlin et al. [[316]](#backmatter-001.xhtml#b_9783110785944-010_ref_316). The idea is simple: To make BNNs robust against bit errors, we simulate the errors already during training time. During each forward pass computation, we generate a random bit-flip mask and apply it to the binary weights.

Let `M` denote a random bit-flip mask with entries ±1 of the same size as `W` that we multiply component-wise to the binarized weights. We first consider computing the bit-flip operation as `H = (B(W) · M) ∘ X` where `∘` denotes the application of the ANN to the input `X`. Standard backpropagation on a loss `ℓ` that is a function of `H` yields the following gradient of `ℓ` with respect to `B(W)`

(7.6) `∇[B(W)]ℓ = M ⋅ ∇[B(W) ⋅ M^ℓ]` (7.6)

which for fully connected layers amounts to a gradient update

(7.7) `∇[B(W)]ℓ = M ⋅ (∇[H]ℓ X^(T))` (7.7)

We see that an update computed this way accounts for the bit-flips that were performed. We propose instead using a special flip-operator with straight-through gradient approximation. We denote by `e[p]` the bit error function that flips its input with probability `p` and let `E[p]` denote its component-wise version. During training, we change the forward pass such that it computes

`X^(l+1) := B(E[p](B(W^(l)))^∘ X^(l))` (7.8)

We replace the gradient of `E[p]` with a straight-through approximation. This way, in the example above we now have `H = E[p](B(W)) ∘ X` with gradient updates `∇[B][(W)]ℓ = ∇[E[p](B(W))]ℓ` which for fully connected layers yields the update

(7.9) `∇[B(W)]ℓ = ∇[H]ℓ X^(T)` (7.9)

which is unaware of bit flips and just uses the corrupted outputs `H`.
