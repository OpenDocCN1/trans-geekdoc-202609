
## Quantum hypothesis class

Let $\mathcal{Q}_0$ be a class of quantum hypotheses defined as

$$\mathcal{Q}_0 = \{h_\theta(x) = \mathbb{E}[M \mid U_\theta U_{enc}(x)] : \theta \in \Theta\}$$

Where $U_{enc}(x)$ is a unitary operator of the classical input $x$, $U_{\theta}$ is a variational quantum circuit parametrized by $\theta$, and $M$ is a Hermitian operator corresponding to a projective or positive operator-valued measure POVM measurement. The output $h_{\theta}(x)$ is the expected value of the observable $M$ with respect to the quantum state $U_{\theta} U_{enc}(x)$.

This formulation captures a variety of quantum machine learning models, including variational classifiers (chapter 6), quantum generative models (chapter 7), and quantum kernel methods (chapter 4). The precise structure of $U_{\theta}$ and the choice of measurement kernel $M$ determines the expressivity and learnability of the hypothesis class.

## 8.1.2 Quantifying expressivity

To compare classical and quantum models in a principled manner, we require quantitative measures of expressivity. These measures often reflect the richness or capacity of the hypothesis class $\mathscr{H}$ to approximate a wide variety of functions. Several frameworks exist to capture this notion, including complexity-theoretic, geometric, and spectral metrics.

### 8.1.2.1 Classical complexity measures

In classical learning theory, the following notions are widely used:

- The **Vapnik–Chervonenkis (VC) dimension** [1], which measures the largest number of points that can be shattered (correctly labeled in all possible ways) by the hypothesis class.
- The **pseudo-dimension** [2], an extension of the VC dimension to real-valued functions.
- The **Rademacher complexity**, which quantifies the ability of a hypothesis class to fit random noise.
- **Covering numbers** and **fat-shattering dimension**, which describe the metric entropy and granularity of function classes.
- **Compression schemes** and **algorithmic stability**, which are relevant for bounding generalization error.

### 8.1.2.2 Kernel-based metrics

For kernel machines, including quantum kernel methods, a widely used metric is the **effective dimension.**

#### Effective dimension
Let $K \in \mathbb{R}^{n \times n}$ be the kernel matrix associated with a hypothesis class, and $\lambda > 0$ a regularization parameter. The effective dimension is defined as
$$d_{\text{eff}}(\lambda) = \text{Tr}(K+\lambda I)^{-1}$$
This quantity serves as a capacity measure that often replaces the VC dimension in kernelized learning bounds. It depends on the spectral decay of $K$ and characterizes the sample complexity of the model.

For quantum kernels, $K$ may be constructed using a quantum feature map $\phi(x) = U(x)|0\rangle$, leading to entries $K_{ij} = |\langle\phi(i)|\phi(j)\rangle|^2$. When the eigenvalues of $K$ decay rapidly, the effective dimension remains small, enabling generalization despite the high-dimensional Hilbert space.

### 8.1.2.3 Quantum-specific expressivity measures

Quantum models add additional metrics that are absent in classical settings:
- Entangling: Highly entangled states typically expand the expressivity of the model but may be harder to optimize and generalize from.
- Proximity to a unitary-design: Circuits that approach a 2-design, for instance, exhibit concentration of measure phenomena.
- Quantum Fisher information matrix (QFIM), which governs the local sensitivity of quantum states to parameter changes. Its rank and conditioning can be used to estimate the dimensionality of the effective model manifold.
- Circuit depth and locality, which constrain the types of correlations that a model can express. Circuits with low connectivity have limited expressivity.

Figure 8.1 illustrates the conceptual landscape of classical and quantum hypothesis classes. The ellipses represent different families of models used in machine learning, including classical kernel methods, quantum kernels, variational circuits (QCs) or quantum neural networks (QNNs), and quantum generative models such as Born machines. The overlapping regions reflect representational capabilities, while the distinct regions indicate expressivity that may be inaccessible to other model types.

The labeled intersections (e.g. ‘Born Machines’) highlight areas where the expressive power of quantum models is conjectured—although not always rigorously proven—to exceed that of classical models under reasonable complexity-theoretic assumptions.

## 8.1.3 Expressivity versus trainability

While high expressivity is generally desirable for representing complex functions, it can negatively impact trainability. This tension is particularly pronounced in quantum models, where the curve of dimensionality and vanishing gradients can hinder optimization.

One manifestation of this issue is the **barren plateau phenomenon**, where the variance of the gradient of a loss function decays exponentially with the number of qubits. This makes it extremely difficult to train deep or highly expressive variational circuits, as small gradients are quickly overwhelmed by noise or finite sampling error.

### Barren plateau theorem (sketch)

Let $U(\theta)$ be a variational circuit initialized from a distribution approximating a unitary 2-design. Then, for a randomly initialized circuit of depth $d$ acting on $n$ qubits, the variance of the gradient of a loss function $L$ with respect to $\theta$ satisfies
$$\text{Var}(\nabla_\theta L) = \mathcal{O}(2^{-n})$$
This result implies that the gradients vanish in the system size, making gradient-based optimization impractical. Several mitigation strategies have been proposed, designing designing models that strike the right balance between expressivity and trainability remains a central challenge.

## Quantum Kernels

![](img/7dbe239d4cc1f635a551b6e06f3d3df9_123_0.png)

**Figure 8.1.** Conceptual map of classical and quantum hypothesis classes. Quantum kernel methods and variational quantum circuits (PQC/QNN) can represent functions outside classical. Quantum generative models such as Born machines may further push the boundary of expressivity.

## 8.2 performance measure: sample complexity and generalization

This investigates how expressive quantum hypothesis translate into learnable models. We develop bounds on sample complexity and generalization, adapting classical learning-theoretic concepts to quantum settings, and summarize known results.

### 8.2.1 PAC and agnostic learning

In the probably correct (PAC) learning model [3, 4], the learner aims to find a hypothesis with lower error using only a limited number of training samples. Let $\mathcal{H}$ be a hypothesis class mapping inputs $x \in \mathcal{X}$ to labels $y \in \{0, 1\}$ or real values in regression. The learner has access to a dataset $\mathcal{S} = \{(x_i, y_i)\}_{i=1}^n \sim \mathcal{D}$, and the goal is to find $h \in \mathcal{H}$ such that the population risk $R(h)$ is close to the minimum possible risk with $\mathcal{H}$:
$$R(h) = \mathbb{E}_{x,y \sim \mathcal{D}} [l(h(x), y)]$$

In the agnostic learning model, we do not assume the data labels are consistent with any hypothesis in $\mathcal{H}$. The learner competes with the best possible hypothesis in the class. Quantum models can be analysed in this framework with minor adjustments. The hypothesis $h_0$ now results from a measurement on a quantum circuit:
$$h_0(x) = \mathbb{E}[M|U_0 U_{enc}(x)|0]$$
where the expectation is taken with respect to the Born rule over repeated shots. The training dataset may be classical (a list of $(x_i, y_i)$) or quantum, consisting of access to pure or mixed quantum states encoding the data-label pairs. Two quantum-data models are often considered:

- Classical access: The learner receives $(x_i, y_i)$ drawn i.i.d. from $\mathcal{D}$.
- Quantum examples: The learner has access to the quantum superposition state:
$$|\psi_y\rangle = \sum_{x} \sqrt{p(x, y)}|x, y\rangle$$
possibly along with oracle related operations.

The PAC learning guarantees under both access models often follow similar forms, with dependence on a complexity measure such as VC dimension or effective dimension.
