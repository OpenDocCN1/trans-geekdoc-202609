# Quantum Perceptron

The classical perceptron describes an algorithm for supervised learning that considers only linearly separable problems in which groups can be separated by a line or hyperplane. The quantum perceptron does usually not include learning, instead it computes the output of a binary unit (neuron) efficiently. It is based on the Kitaev's phase estimation algorithm. A quantum perceptron can be used as building block of larger systems, it can process an arbitrary number of input vectors in parallel. We present a simple example of the quantum perceptron for two-dimensional input.

# 21.1 COUNTING ONES WITH KITAEV'S PHASE ESTIMATION ALGORITHM

The phase gate

```
$P(\lambda) = \begin{pmatrix} 1 & 0 \ 0 & e^{i\lambda} \end{pmatrix}$
```

Has tow eigenvectors [1] and [0] with the eigenvalues $e^{i\lambda}$ and 1. Setting $\lambda$ to

```
$$\lambda = \pi \cdot \frac{net}{2^{m-1}}$
```

results in the eigenvalue

```
$e^{i\pi \cdot \frac{net}{2^{m-1}}}$$
```

Kitaev's Phase Estimation Algorithm determines the eigenvalue using the controlled phase gate with

```
$P|1\rangle = e^{2\pi i\cdot\theta} |1\rangle = e^{2\pi i\cdot\frac{\theta}{2^{m-1}}} |1\rangle = e^{2\pi i\cdot\frac{\theta}{2^m}} |1\rangle. \quad (21.1)$
```

The phase estimation algorithm will write the phase of $P$ to the $m$ qubits in the control register

```
$net = x_m \cdot \dots \cdot x_2x_1$
```

```
$$\theta = 0.cdot x_m \cdot \dots \cdot x_2x_1 = \frac{x}{2^m} = \frac{net}{2^m}, \quad \(21.2)$
```

```
$$\lambda = \pi \cdot \theta$
```