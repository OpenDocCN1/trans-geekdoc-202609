
# Neuron NeuroResearch

events, $e_i^k$, is applied at every event. The iterative updates estimate the strength of the k-th kernel contribution to neural activity at the specified event-onset times,

```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

# Dictionary learning step

We use gradient-based methods to update the dictionary. In its implicit form, this takes like stochastic gradient descent:

where $p(z) = \|z\|$ performs a norm, and $\eta$ is the learning rate. This method completes the formulation and optimization of SSSL. We note that, particularly for non-Gaussian data, this is not a published framework, and no available toolboxes can solve SSSL directly. The challenges of current toolboxes, we discuss how the optimization of SSSL can be mapped into the training of a deep network, as to Deconvolutional Unrolled Learning (DUNL). The transition from SSSL to DUNL is crucial for the practical applicability of the proposed framework to scale neural data, and by the flexibility of the framework to ensure a variety of constraints on parameters and representations (e.g., input event onsets, structured representations, k-sparse codes).

# Iterative convolutional unrolled neural learning (DUNL)

# Inference method

The alternating minimization procedure described above can be mapped into an encoder/decoder neural network. We use algorithm $^{60}$ to map the sparse coding step (3) into an encoder. This approach is similar to the architectures proposed in $^{14,49}$ for dictionary learning. In this architecture, each sparse coding (14) is interpreted as a layer of neural network with a recurrent convolutional structure and a ReLU nonlinearity. We refer to this encoder as an inference network, which maps sparse-onsets, single-type time series $y^k$ to the estimates of the time-series sparse codes $x_i^k$. These co-onsets and their contributions to explain the data (see Figure S1).

Given the codes from the inference network, we construct a generative decoder based on the generative model (1) (see Figure S1B). This decodes the estimated time sets of sparse codes for a given neuron into a time series estimation (e.g., a time series representing the firing rate) for spiking data.

We combine the inference network and the generative decoder to construct an interpretable neural network that can be trained via backpropagation. Propagation allows us to learn the kernels $\{h_i^k\}$, which characterize the neural response to events coded by $\{x_i^k\}$. As detailed in, the framework of this network is twofold: the neural parameters are directly linked to the kernels $\{h_i^k\}$, and the encoder's latent representations correspond to the weights and their strengths. The model involves two sets of trainable parameters used to learn the dictionary, both of which are highly parallelizable across neurons and trials. The sparse-coding and dictionary-update step works as follows in SSSL: we alternate between sparse coding and dictionary updates. This has been demonstrated in previous works such as spike learning $^{70}$, and theoretical analysis exists for the binomial case with one hidden layer $^{44}$. Additionally, DUNL benefits from the rich literature on sparse coding, which provides insights into under model mismatch, $^{111, 76–78}$ and while mismatch increases error, the learned parameters still exhibit a positive correlation with the ground truth.

# Structured representation

Motivated by biological factors and prior knowledge, we wish to introduce additional constraints to the codes beyond sparsity. For example, calcium fluorescence does not encode electrical activity; the signals differ different when a neuron's firing rate increases versus decreases. If the underlying firing rate varies, the same measured calcium signal will differ. These differences can be captured by introducing structured representations in our framework. We consider a case of model fluorescence with one kernel per neuron. This model would fail to capture nonlinear relationships between both positive (increased activity above baseline) and negative (decreased activity) codes on the filter or kernel. To address this, we can introduce an additional filter and a prior of filters to prevent the occurrence of event onsets, ensuring that both filters do not contribute to neural activity at the same onset. As demonstrated in our analysis of fluorescence from dopamine neurons, these priors enable the model to capture the nonlinearity relationship between activity and levels.

Neuron J17, 1151–1168–et.e13, April 2025 e5

# CellProcess

# Neuron

# NeuroResource

Algorithm 1. Iterative method to approximate unknown step size.

```
Input: size $T$, initial estimate or randomly initialized $\{h_k\}_{k=1}^T$, the inverse link function $g(\cdot)$; Initialize:
x^{(0)}=[x_1^{(B)},x_2^{(B)},\dots,x_T^{(B)}]^T using Normal distribution
Repeat: $m=0, \dots, M-1
x^{(m+1)}=|x^{(m)}\|_2^{-2}g'(h^{(m)})
Output: $x^{(M)}$
```

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $p(z) = \|z\|$ performs a norm, and $\eta$ is the learning rate. This method completes the formulation and optimization of SSSL. We note that, particularly for non-Gaussian data, this is not a published framework, and no available toolboxes can solve SSSL directly. The challenges of current toolboxes, we discuss how the optimization of SSSL can be mapped into the training of a deep network, as to Deconvolutional Unrolled Learning (DUNL). The transition from SSSL to DUNL is crucial for the practical applicability of the proposed framework to scale neural data, and by the flexibility of the framework to ensure a variety of constraints on parameters and representations (e.g., input event onsets, structured representations, k-sparse codes).

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x^{(0)}=[x_1^{(B)},x_2^{(B)},\dots,x_T^{(B)}]^T$ using Normal distribution
Repeat: $m=0, \dots, M-1$
$x^{(m+1)}=|x^{(m)}\|_2^{-2}g'(h^{(m)})$
Output: $x^{(M)}$

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x^{(0)}=[x_1^{(B)},x_2^{(B)},\dots,x_T^{(B)}]^T$ using Normal distribution
Repeat: $m=0, \dots, M-1$
$x^{(m+1)}=|x^{(m)}\|_2^{-2}g'(h^{(m)})$
Output: $x^{(M)}$

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x^{(0)}=[x_1^{(B)},x_2^{(B)},\dots,x_T^{(B)}]^T$ using Normal distribution
Repeat: $m=0, \dots, M-1$
$x^{(m+1)}=|x^{(m)}\|_2^{-2}g'(h^{(m)})$
Output: $x^{(M)}$

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x^{(0)}=[x_1^{(B)},x_2^{(B)},\dots,x_T^{(B)}]^T$ using Normal distribution
Repeat: $m=0, \dots, M-1$
$x^{(m+1)}=|x^{(m)}\|_2^{-2}g'(h^{(m)})$
Output: $x^{(M)}$

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

where $x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

where $x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

where $x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be be either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

where $x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

where $x_k^j$ is the sparse code. This is the
-
```
$x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```

where $x_k^j$ is the sparse code. This is the
-
```
$x_k^j - x_{k-1}^j\|_2^2$ is the term.

This latent structure can be enforced either on the codes or by incorporating an additional penalty term into the original methodology, this modified optimization solves:

```
$$\min_{\{h_k^j\}_{k=1}^T} \sum_{k=1}^T -log p(x_k|h_k^j,x_{k-1}^j) + \sum_{k=1}^{T-1} \|x_k^j - x_{k-1}^j\|_2^2 + \sum_{k=1}^T \lambda \|x_k^j\|_1$$
```

where $x_k^j$ is the sparse code. This is the
-
```
$x_i^k = e_i^k - S_{\sigma_i^k}(x_i^{k-1} + a^k h_i^k \star y^k - g\left(\sum_{j=1}^k h_i^j \star x_i^{j-1} + a^j\right)\right)$
```
