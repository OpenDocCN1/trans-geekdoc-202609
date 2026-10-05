Quantum Machine Learning

+   - **Mode collapse**: Especially relevant in adversarial training, where the generator fails to capture the diversity of the data distribution. This can also be encountered due to the prevalence of spurious minima in the optimization landscape.
- **Hardware constraints**: Real quantum devices have limited qubit counts, gate fidelity, and coherence times, which restrict circuit complexity and batch sizes.

#  7.5 Case studies and applications

QGMs offer a flexible and powerful framework for learning and synthesizing distributions that are difficult or inefficient to represent classically. This has opened the door to a wide range of applications quantum physics, machine learning, optimization, and sensing. In this section, we highlight some cases where QGMs have shown promise or achieved early success, and discuss the potential for scaling these techniques in quantum computing workflows.

#  7.5.1 Learning classical data distributions

A major line of research focuses on using QBCMs, QGANs, and hybrid VAEs to learn structured classical datasets. These include:

+   - **Binary images** with bars-and-stripes or small MNIST digits,
- **Correlated patterns** from spin models or statistical physics, and
- **Synthetic tabular data** with controllable complexity.

In these cases, quantum models are trained to reproduce a classical probability distribution $P_{data}(x)$ by minimizing a divergence (e.g. KL or MMD). Because QBCMs encode the distribution directly into quantum amplitudes, they offer a natural advantage in representing highly entangled or non-factorizable correlations that may be difficult for shallow classical models.

For example, in a recent study [34], QBCMs were used to learn event distributions from simulated high-energy physics experimental data, demonstrating that quantum circuits with modest depth and hardware-efficient layout can successfully model nontrivial correlations present in collider observables.

#  7.5.2 Quantum state learning and tomography

QGMs can be used to learn and reconstruct unknown quantum states, an application that leverages their quantum-native architecture. The goal is to train a parameterized quantum circuit $U(	heta)$ such that its output state matches a target quantum state $ho_{target}$, in terms of measurement or through a fidelity-based loss:

```
$L_{fidelity} = 1 - F(\rho_{	heta}, \rho_{target}), \quad \text{where} \quad F(\rho, \sigma) = (\text{Tr}\sqrt{\sqrt{\rho}\sigma\sqrt{\rho}})^2. \quad (7.17)$
```

This approach by-passes full state tomography and has been shown to scale better for higher-dimensional systems [35]. It is particularly well-suited for applications

7-12