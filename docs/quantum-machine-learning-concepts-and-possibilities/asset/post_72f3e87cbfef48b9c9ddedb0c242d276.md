
## Quantum Machine Learning

Several quantum machine learning frameworks provide infrastructure for hybrid auto-differentiation:

- **PennyLane [18]** enables full differentiable quantum-classical graphs, supporting PyTorch, TensorFlow, JAX backends. It exposes *quantum nodes* with built-in gradients and supports end-to-end optimization with standard optimizers.
- **Qiskit Machine Learning [19]** integrates with PyTorch via custom TORCHCONNECTOR modules and supports parameter-shift gradients or finite-difference estimators on IBM backends or simulators.
- **TensorFlow Quantum [20]** supports differentiable quantum layers integrated with classical TensorFlow/Keras pipelines. It uses adjoint differentiation in simulation and sampling-based gradient rules on.

These frameworks automatically keep track of which parts of the graph are quantum versus classical, and invoke the correct gradient rules accordingly.

**Hybrid training loop**
Consider a model where a quantum circuit produces a real-valued output $f(x; 0)$ used in a logistic regression task. The loss might be

$L(f, y) = -y\log(f) - (1 - y)\log(1 - f).$ (6.6)

- During training:
  - The **forward pass** evaluates the quantum circuit on input $x$, measures the observable, and computes it which is stored in the graph.
  - The loss $L$ uses the scalar output $f$.
  - The **backward pass** starts from $\nabla_f L$, uses quantum gradient rules to evaluate $\nabla(f)$, and applies the chain rule to compute $\nabla_x L$.
  - A classical optimizer (e.g. Adam) updates the parameters $\theta$.

The entire process is transparent to the user, who simply defines the model and loss in a declarative way, like building a classical neural network.

## Differentiability in-prctice

Differentiability across the quantum-classical boundary is possible only because quantum circuits can be expressed as expectation-value functions, given suitable gates and observables. However, differentiability **does not mean analyability** due to sampling noise, barren plateaus, and hardware limitations; must be taken to ensure gradients are informative and reliable.

Nevertheless, hybrid autodiff has made variational quantum models practical. It enables the integration of quantum modules into large-scale machine learning systems, facilitating experimentation with architectures where quantum computation plays a meaningful, trainable role.

## 6.2.2 Parameter-shift rule

One of the main break-throughs enabling the training of variational quantum circuits on quantum hardware is the parameter-shift rule (PSR) [21]. This rule allows us to compute the gradient of an expectation value with respect to a circuit parameter, using only evaluations of the quantum circuit at shifted values of the parameter, meaning no access to the internal quantum state or wavefunction is required. This makes the PSR a hardware-friendly and analytically exact method for computing gradients on NISQ devices.

### Mathematical derivation

Suppose we have a parameterized quantum circuit $U(\theta)$ composed of gates where a specific gate $R(\theta)$ has the form

$R(\theta) = e^{-i\theta G},$

where $G$ is a Hermitian generator with two distinct eigenvalues $\pm r$ (common case: $r=\frac{1}{2}$, as in Pauli rotations).

Let the circuit prepare the quantum state,

$|\psi(\theta)\rangle = U(\theta)|\psi_0\rangle$,

and let the output be the expectation value of some observable $M$:

$f(\theta) = \langle\psi(\theta)|M|\psi(\theta)\rangle$,

Then the parameter-shift rule states

$\frac{\partial f}{\partial\theta} = \frac{1}{2}[f(\theta+\frac{\pi}{4r}) - f(\theta-\frac{\pi}{4r})],$

where $s=\frac{\pi}{4r}$,

For the common case $G=\frac{1}{2}Z$ (i.e. single-qubit rotation gates such as $R_X, R_Y, R_Z$), this simplifies to

$\frac{\partial f}{\partial\theta} = \frac{1}{2}[f(\theta+\frac{\pi}{2}) - f(\theta-\frac{\pi}{2})],$

This result is exact and does not involve finite-difference approximations or knowledge of the wavefunction, only evaluations of the same circuit with different parameter values.

### Intuition

In variational circuits, parameterized gates are often single qubit rotations about the (X, Y, and Z) axes:

- $R_X(\theta) = e^{-i\theta X/2}$,
- $R_Y(\theta) = e^{-i\theta Y/2}$,
- $R_Z(\theta) = e^{-i\theta Z/2}$.

## Quantum Machine Learning

The parameter-shift rule tells us that the effect of changing $\theta$ on the measurement outcome can be captured by evaluating the circuit at two symmetrically shifted points. This is particularly advantageous because it works even when the circuit runs on a noisy quantum device.

### Practical implementation

To compute the gradient of a loss function with respect to a parameter $\theta$, one must:

1. Shift $\theta$ forward by $\frac{\pi}{2}$, evaluate the circuit, and record the outcome.
2. Shift $\theta$ backward by $\frac{\pi}{2}$, evaluate the circuit again.
3. Take the difference, divide by 2, and chain with the loss function.

This results in two **forward passes per trainable parameter.**

Example: Parameter-shift rule
Suppose we are measuring a qubit in the $Z$ basis after applying a rotation $R_y(\theta)$. The expectation value is

$\frac{\partial f}{\partial\theta} = \frac{1}{2}[f(\theta+\frac{\pi}{2}) - f(\theta-\frac{\pi}{2})],$ (13)

### Limitations

The parameter-shift rule applies only to gates with **two eigenvalues**. When the generator has more than two eigenvalues (e.g. non-Pauli rotations), it becomes computationally expensive. For a circuit with $p$ parameters, one needs $2p$ evaluations.

## 6.2.3 Generalized parameter-shift rules

While the standard PSR applies to generators with two eigenvalues, many quantum operations involve generators with more than two. The generalized PSR [22] offers a framework for computing expectation values for arbitrary gates of the form

$U(\theta) = e^{-i\theta G},$ (15)

### General form of the gradient

Given a quantum circuit that prepares the state $|\psi\rangle = U(\theta)|\psi_0\rangle$, and an observable $M$, the expectation value is

$f(\theta) = \langle\psi(\theta)|M|\psi(\theta)\rangle,$ (16)

Then, under suitable regularity conditions (e.g. that $G$ has a discrete spectrum), the derivative $f(\theta)$ can be expressed as a finite sum of circuit evaluations at multiple parameter values:

$\frac{\partial f}{\partial\theta} = \sum_{s} c_s f(\theta + s).$ (17)

where:

- $s \in \mathbb{R}$ is a set of shifted values
- $c_s \in \mathbb{R}$ are coefficients depending on the spectrum of $G$.

### Key observations

- The number of shifts depends on the **number of distinct eigenvalues** of $G$. For Pauli generators (two eigenvalues), two shifts; for more complex gates, the number of required shifts increase accordingly.
- **Multi-qubit gates** such as controlled-phase or controlled-rotation gates, the generator often has four or more eigenvalues. In this case, one may need four, six, or even more circuit evaluations to estimate the gradient of a single parameter.
- **Diagonal generators** (e.g. projectors or Hamiltonian terms in block-diagonal form) can often be decomposed analytically, facilitating an efficient generalized-PSR formulation.

Example: Three eigenvalue generator
Suppose $G$ has eigenvalues $(-1, 0, +1)$. Then the generalized PSR yields:

$\frac{\partial f}{\partial\theta} = \sum_{k} c_k f(\theta + s_k),$ (18)

with shift values $s_k \in \{\pm\pi/2, \pm\pi/4\}$, and coefficients $c_k$ computed to match the derivative of $f$.
