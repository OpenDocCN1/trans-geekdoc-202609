
![c7-fig-5024.jpg](images/c7-fig-5024.jpg)

(7.22)

Again, the progression from line two to line three is not obvious and is explored in problem 7.9. However, the result makes sense. The final line is a matrix of the same size as `Ω[k]`. It depends linearly on `h[k]`, which was multiplied by `Ω[k]` in the original expression. This is also consistent with the initial intuition that the derivative of the weights in `Ω[k]` will be proportional to the values of the hidden units `h[k]` that they multiply. Recall that we already computed these during the forward pass.

### 7.4.1 Backpropagation algorithm summary

We now briefly summarize the final backpropagation algorithm. Consider a deep neural network `f[x[i], ϕ]` that takes input `x[i]`, has `K` hidden layers with ReLU activations, and individual loss term `ℓ[i] = l[f[x[i], ϕ], y[i]]`. The goal of backpropagation is to compute the derivatives `∂ℓ[i]/∂β[k]` and `∂ℓ[i]/∂Ω[k]` with respect to the biases `β[k]` and weights `Ω[k]`.

**Forward pass:** We compute and store the following quantities:

![c7-fig-5025.jpg](images/c7-fig-5025.jpg)

(7.23)

**Backward pass:** We start with the derivative `∂ℓ[i]/∂f[K]` of the loss function `ℓ[i]` with respect to the network output `f[K]` and work backward through the network:

![c7-fig-5026.jpg](images/c7-fig-5026.jpg)

(7.24)

where ⊙ denotes pointwise multiplication, and `𝕀[f[k][−1] > 0]` is a vector containing ones where `f[k][−1]` is greater than zero and zeros elsewhere. Finally, we compute the derivatives with respect to the first set of biases and weights:

![c7-fig-5027.jpg](images/c7-fig-5027.jpg)

(7.25)

We calculate these derivatives for every training example in the batch and sum them together to retrieve the gradient for the SGD update.

---

Problem 7.10

---

Note that the backpropagation algorithm is extremely efficient; the most demanding computational step in both the forward and backward pass is matrix multiplication (by `Ω` and `Ω^T`, respectively) which only requires additions and multiplications. However, it is not memory efficient; the intermediate values in the forward pass must all be stored, and this can limit the size of the model we can train.

---

Notebook 7.2

Backpropagation

---

### 7.4.2 Algorithmic differentiation

Although it's important to understand the backpropagation algorithm, it's unlikely that you will need to code it in practice. Modern deep learning frameworks such as PyTorch and TensorFlow calculate the derivatives automatically, given the model specification. This is known as *algorithmic differentiation*.

Each functional component (linear transform, ReLU activation, loss function) in the framework knows how to compute its own derivative. For example, the PyTorch ReLU function `z[out] = relu[z[in]]` knows how to compute the derivative of its output `z[out]` with respect to its input `z[in]`. Similarly, a linear function `z[out] = β + Ωz[in]` knows how to compute the derivatives of the output `z[out]` with respect to the input `z[in]` and with respect to the parameters `β` and `Ω`. The algorithmic differentiation framework also knows the sequence of operations in the network and thus has all the information required to perform the forward and backward passes.

These frameworks exploit the massive parallelism of modern graphics processing units (GPUs). Computations such as matrix multiplication (which features in both the forward and backward pass) are naturally amenable to parallelization. Moreover, it's possible to perform the forward and backward passes for the entire batch in parallel if the model and intermediate results in the forward pass do not exceed the available memory.

---

Problem 7.11

---

Since the training algorithm now processes the entire batch in parallel, the input becomes a multi-dimensional *tensor*. In this context, a tensor can be considered the generalization of a matrix to arbitrary dimensions. Hence, a vector is a 1D tensor, a matrix is a 2D tensor, and a 3D tensor is a 3D grid of numbers. Until now, the training data have been 1D, so the input for backpropagation would be a 2D tensor where the first dimension indexes the batch element and the second indexes the data dimension. In subsequent chapters, we will encounter more complex structured input data. For example, in models where the input is an RGB image, the original data examples are 3D (height × width × channel). Here, the input to the learning framework would be a 4D tensor, where the extra dimension indexes the batch element.

### 7.4.3 Extension to arbitrary computational graphs

We have described backpropagation in a deep neural network that is naturally sequential; we calculate the intermediate quantities `f[0]`, `h[1]`, `f[1]`, `h[2]` …, `f[k]` in turn. However, models need not be restricted to sequential computation. Later in this book, we will meet models with branching structures. For example, we might take the values in a hidden layer and process them through two different sub-networks before recombining.

---

Problems 7.12–7.13

---

Fortunately, the ideas of backpropagation still hold if the computational graph is acyclic. Modern algorithmic differentiation frameworks such as PyTorch and TensorFlow can handle arbitrary acyclic computational graphs.

## 7.5 Parameter initialization

The backpropagation algorithm computes the derivatives that are used by stochastic gradient descent and Adam to train the model. We now address how to initialize the parameters before we start training. To see why this is crucial, consider that during the forward pass, each set of pre-activations `f[k]` is computed as:

![c7-fig-5028.jpg](images/c7-fig-5028.jpg)

(7.26)

where `a[•]` applies the ReLU functions and `Ω[k]` and `β[k]` are the weights and biases, respectively. Imagine that we initialize all the biases to zero and the elements of `Ω[k]` according to a normal distribution with mean zero and variance `σ²`. Consider two scenarios:

*   If the variance `σ²` is very small (e.g., 10⁻⁵), then each element of `β[k] + Ω[k]h[k]` will be a weighted sum of `h[k]` where the weights are very small; the result will likely have a smaller magnitude than the input. In addition, the ReLU function clips values less than zero, so the range of `h[k]` will be half that of `f[k][−1]`. Consequently, the magnitudes of the pre-activations at the hidden layers will get smaller and smaller as we progress through the network.

*   If the variance `σ²` is very large (e.g., 10⁵), then each element of `β[k] + Ω[k]h[k]` will be a weighted sum of `h[k]` where the weights are very large; the result is likely to have a much larger magnitude than the input. The ReLU function halves the range of the inputs, but if `σ²` is large enough, the magnitudes of the pre-activations will still get larger as we progress through the network.

In these two situations, the values at the pre-activations can become so small or so large that they cannot be represented with finite precision floating point arithmetic.

Even if the forward pass is tractable, the same logic applies to the backward pass. Each gradient update (equation 7.24) consists of multiplying by `Ω^T`. If the values of `Ω` are not initialized sensibly, then the gradient magnitudes may decrease or increase un-controllably during the backward pass. These cases are known as the *vanishing gradient problem* and the *exploding gradient problem*, respectively. In the former case, updates to the model become vanishingly small. In the latter case, they become unstable.

### 7.5.1 Initialization for forward pass
