Quantum Machine Learning

Effective dimension
Let $K \in \mathbb{R}^{n 	imes n}$ be the kernel matrix associated with a hypothesis class, and $\lambda > 0$ a regularization parameter. The effective dimension is defined as
$$d_{\eff}(\lambda) = \text{Tr}(K+\lambda I)^{-1}$$
This quantity serves as a capacity measure that often replaces the VC dimension in kernelized learning bounds. It depends on the spectral decay of $K$ and characterizes the sample complexity of the model.

For quantum kernels, $K$ may be constructed using a quantum feature map $\phi(x) = U(x)|0\rangle$, leading to entries $K_{ij} = |\langle\phi(i)|\phi(j)\rangle|^2$. When the eigenvalues of $K$ decay rapidly, the effective dimension remains small, enabling generalization despite the high-dimensional Hilbert space.

# 8.1.2.3 Quantum-specific expressivity measures

+   Quantum models add additional metrics that are absent in classical settings:
* Entangling Highly entangled states typically expand the expressivity of the model but may be harder to optimize and generalize from.
* Proximity to a unitary-design, Circuits that approach a 2-design, for instance, exhibit concentration of measure phenomena.
* Quantum Fisher information matrix (QFIM), which governs the local sensitivity of quantum states to parameter changes. Its rank and conditioning can be used to estimate the dimensionality of the effective model manifold.
* Circuit depth and locality, which constrain the types of correlations that a model can express. Circuits with low connectivity have limited expressivity.

Figure 8.1 illustrates the conceptual landscape of classical and quantum hypothesis classes. The ellipses represent different families of models used in machine learning, including classical kernel methods, quantum kernels, variational circuits (QCs) or quantum neural networks (QNNs), and quantum generative models such as Born machines. The overlapping regions reflect representational capabilities, while the distinct regions indicate expressivity that may be inaccessible to other model types.

The labeled intersections (e.g. ‘Born Machines’) highlight areas where the expressive power of quantum models is conjectured—although not always rigorously proven—to exceed that of classical models under reasonable complexity-theoretic assumptions.

# 8.1.3 Expressivity versus trainability

While high expressivity is generally desirable for representing complex functions, it can negatively impact trainability. This tension is particularly pronounced in