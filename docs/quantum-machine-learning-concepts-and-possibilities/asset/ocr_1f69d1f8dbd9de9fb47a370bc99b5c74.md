# Quantum Machine Learning

+   * Entanglement structure: Models that generate highly entangled states tend to have more expressive power.
* Parameterization: Redundant or untrainable parameters can reduce effective expressivity.
* Measurement scheme: The choice of measurement basis can influence what features are observable in the output.

A useful metric is the frame potential [28, 29], which measures how well a set of circuits covers the unitary group. A circuit family with low frame potential is closer to forming a unitary 2-design, which is often used as a proxy for high expressivity.

# 7.3.3 Trade-off with trainability

+   High expressivity can be a double-edged sword. While expressive models are capable of learning complex distributions, they may also be prone to:
* Overfitting in small datasets
* Barren plateaus, where gradients vanish exponentially with system size [30, 31]; and
* Optimization instability when too many parameters interact nonlinearly

Thus, balancing expressivity with inductive bias and training feasibility is critical when designing quantum generative circuits.

# 7.4 Training quantum generative models

Training quantum generative models involves optimizing the parameters of a quantum circuit such as the distribution induced by measurement outcomes approximates a target distribution. While conceptually analogous to training classical generative models, the quantum setting introduces distinctive challenges and opportunities, particularly due to measurement stochasticity, non-differentiability, and hardware constraints.

This section outlines the typical training loop, common losses, gradient estimation techniques, and specific difficulties encountered during optimization.

# 7.4.1 The optimization loop

+   Most quantum generative models follow a hybrid quantum-classical training loop:
* Initialize parameters $	heta$ for the quantum circuit $U(	heta)$.
* Generate samples from the circuit by measuring in the computational basis, yielding outcomes $x \sim p_	heta(x)$.
* Estimate a loss function comparing $p_	heta$ to the target distribution $p_{data}$.
* Update parameters using a classical optimizer (e.g. gradient descent, Adam, or SPSA).
* Repeat until convergence.

This loop is model-agnostic and applies to QCBMs, QGANs, QVAEs, and other quantum generative frameworks.