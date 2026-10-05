# Quantum Kernels

![](bbox=[0.151, 0.141, 0.848, 0.31])

**Figure 8.1.** Conceptual map of classical and quantum hypothesis classes. Quantum kernel methods and variational quantum circuits (PQC/QNN) can represent functions outside classical. Quantum generative models such as Born machines may further push the boundary of expressivity.

quantum models, where the curve of dimensionality and vanishing gradients can hinder optimization.

One manifestation of this issue is the **barren plateau phenomenon**, where the variance of the gradient of a loss function decays exponentially with the number of qubits. This makes it extremely difficult to train deep or highly expressive variational circuits, as small gradients are quickly overwhelmed by noise or finite sampling error.

# Barren plateau theorem (sketch)

Let $U(	heta)$ be a variational circuit initialized from a distribution approximating a unitary 2-design. Then, for a randomly initialized circuit of depth $d$ acting on $n$ qubits, the variance of the gradient of a loss function $L(	heta)$ with respect to $	heta$ satisfies

```
Var(\nabla_{\theta} L) = \mathcal{O}(\frac{1}{poly(2^n)})
```

This result implies that the gradients vanish exponentially in the system size, making gradient-based optimization impractical without additional structure.

Several mitigation strategies have been proposed, including layerwise training, cost loss functions, and restricted ansatz families that avoid expressivity levels leading to such plateaus. Nevertheless, designing quantum models that strike the right balance between expressivity and trainability remains a central challenge in the field.

In the following section, we build on this framework to examine how expressivity relates to the learnability of quantum models, quantifying the sample complexity and generalization properties associated with each class.