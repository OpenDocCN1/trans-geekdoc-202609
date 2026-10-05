# 6.2.5.1 Conceptual overview

Let a quantum circuit $U(\theta)$ prepare a state,

```
$|\psi(\theta)\rangle = U(\theta)|0\rangle^{\otimes n},$ (6.22)
```

and let the output of the model be the expectation value of a Hermitian observable $M$,

```
$f(\theta) = \langle\psi(\theta)|M|\psi(\theta)\rangle.$ (6.23)
```

The goal is to compute the gradient $\nabla_theta f$. Using adjoint differentiation, this is done by propagating backgradients backwards through each gate in the circuit similar to classical neural backpropagation.

This approach leverages the chain rule for unitary gates, and computes each partial derivative with respect to a gate parameter $\theta_i$ using

```
$\frac{\partial f}{\partial\theta_i} = 2 \Re \langle\frac{\partial\psi(\theta)\rangle}{\partial\theta_i}|M|\psi(\theta)\rangle.$$ (6.24)
```

Critically, the derivative $\partial\psi(\theta)\rangle/\partial\theta_i$ is not estimated numerically but computed by catching intermediate states and applying the adjoint (reverse) of each gate, just like reverse-mode autodiff in classical machine learning.

# 6.2.5.2 Efficiency and scaling

One of the strengths of adjoint differentiation is its computational efficiency. For quantum circuits with $G$ gates and $p$ parameters, the full gradient can be computed in $O(G)$ time and memory, rather than $O(p)$ evaluations as in parameter-shift. This makes it particularly appealing for:

+   - Large variational circuits with many parameters,
- Batch-mode optimization during model prototyping, and
- Architecture searches and hyperparameter sweeps where fast gradients are needed.

# 6.2.5.3 Limitations

Despite its utility, adjoint differentiation is not usable on hardware. It requires:

+   - Access to the full quantum state, which is exponentially large in the number of qubits,
- Reversible simulation of gates, including full complex amplitudes.
- Post-selection or overlap measurements, which cannot be implemented without cloning or tomography.

Additionally, memory usage scales linearly with the number of gates (due to backpropagation through cached states), and cannot scale well beyond 30-40 qubits in practice.

# 6.2.6 Quantum natural gradient and the quantum geometric tensor

While traditional gradient descent is widely used in both classical and quantum machine learning, it is not always the most efficient path to optimization. This