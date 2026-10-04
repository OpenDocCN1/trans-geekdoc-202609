
```python
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
qc.append(crit, [3,4,5,6,7])
# Do inverse QFT on counting qubits
qc.append(qft_dagger, [0,1,2,3])
# Measure counting qubits
qc.measure([0,1,2,3], [0,1,2,3])
```

simulator = Aer.get_backend('qasm_simulator')
result = execute(qc,simulator, shots=1000).result()
counts = result.get_counts()
plot_histogram(counts)

```

The maximal measured value corresponds to the binary value 0011 (3 decimal) or 1101 (13 decimal), see [Figure 20.3 (b)](fig203). The phase is either $\theta_1 = \frac{7}{16}$ or $\theta_2 = \frac{13}{16}$ corresponding to the two eigenvalues $\lambda_1 = e^{i\theta}$ or $\lambda_2 = e^{-i\theta}$ with positive and negative phase with

$$\sin^2(\theta) = \sin^2(-\theta)$$

$$k = 4.9 \approx \sin^2\left(\frac{\pi \cdot 3}{16}\right) \cdot 16 = \sin^2\left(\frac{\pi \cdot 13}{16}\right) \cdot 16.$$

with approximately the correct answer

The more control qubits ($m$) we use, the higher precision we get. In our example four control qubits lead only to an approximate estimation of the phase $\theta$. For example if marks finds five solutions ($k=5$) out of 16 states we measure exactly the same maximal measured values 0011 (3 decimal) or 1101 (13 decimal). More control qubits would be required for less approximate counts. The counts of the two maximal values identifying the phase $\theta_1$ and $\theta_2$ would be higher and the counts of the other states would approximate the value zero.

![](img/52faec2d621d75e53089d939bb234a82_289_0.png)

![](img/52faec2d621d75e53089d939bb234a82_289_1.png)

**Figure 20.3** (a) The controlled Grover operator is implemented using use the circuit library with an oracle that has four solutions ($k=4$) out of 16 states ($m^*=4$). The circuit is composed of 8 qubits, qubits 0, 1, 2, 3 represent the 4 qubits in the control register. The qubits 5 to 7 represents the four qubits in the computational basis representing 16 states. All qubits are mapped to superposition by Hadamard gates. The control register controls the unitary operations $G$ resulting in the Fourier basis representation of the three control qubits. To estimate the phase $\theta$ we perform the inverse QFT to the 4 control qubits and measure the 4 qubits. (b) The maximal measured value corresponds to the binary value 0011 (3 decimal) or 1101 (13 decimal) indicating phase $\theta_1 = \pi \cdot 3/16$ or $\theta_2 = \pi \cdot 13/16$.

# Quantum Perceptron

The classical perceptron describes an algorithm for supervised learning that considers only linearly separable problems in which groups can be separated by a line or hyperplane. The quantum perceptron does usually not include learning, instead it computes the output of a binary unit (neuron) efficiently. It is based on the Kitaev's phase estimation algorithm. A quantum perceptron can be used as building block of larger systems, it can process an arbitrary number of input vectors in parallel. We present a simple example of the quantum perceptron for two-dimensional input.

# 21.1 COUNTING ONES WITH KITAEV'S PHASE ESTIMATION ALGORITHM

The phase gate

```
$P(\lambda) = \begin{pmatrix} 1 & 0 \\ 0 & e^{i\lambda} \end{pmatrix}$
```

Has two eigenvectors [1] and [0] with the eigenvalues $e^{i\lambda}$ and 1. Setting $\lambda$ to

```
$$\lambda = \pi \cdot \frac{net}{2^{m-1}}$$
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
$$\theta = 0\cdot x_m \cdot \dots \cdot x_2x_1 = \frac{x}{2^m} = \frac{net}{2^m}, \quad (21.2)$$
```

```
$$\lambda = \pi \cdot \theta$$
```

# 21.2 QUANTUM PERCEPTRON

The classical perceptron describes an algorithm for supervised learning that consists only linearly separable problems in groups which can be separated by a line or hyperplane. The quantum perceptron [96], [95] does usually include learning and instead it computes the binary representation of the function $net$ modulo $D$ with $w_0 = 1$

```
$$net := \left(\sum_{j=0}^{D} w_j \cdot x_j\right) \mod D = \left(\sum_{j=1}^{D} w_j \cdot x_j + w_0\right) \mod D = (|\mathbf{w}| + w_0) \mod D$$
```

with the constraint $x_j \in \{0, 1\}$, the value $w_0$ is called the "bias", it is a constant value that does not depend on any input. Each dimension $j$ is represented by a controlled phase gate $CP_j$

```
$$\lambda = \pi \cdot \frac{w_j}{2^{m-1}}$$
```

and $D = 2^m$. For $D = 2$,

```
$$net = w_0 + w_1 \cdot x_1 + w_2 \cdot x_2$$
```

will be represented by three phase gate that performs the computation

```
$$e^{i\pi \cdot \frac{w_j}{2}}$$
```

The estimated values of $net$ are represented by two qubits $[00], [01], [11]$. The natural number of $net$ corresponds to four states. A nonlinear activation function

```
$$\phi(net) = \begin{cases} 1 & \text{if } net \geq \text{threshold} \\ 0 & \text{if } net < \text{threshold} \end{cases}$$
```

with $\theta = \text{threshold}$, the quantum perceptron can be used as building block of larger systems, it can process an arbitrary number of input vectors in parallel, when the input is presentedpsi.

```
$$|\psi\rangle = \sum_{k=0}^{2^m-1} c_k |k\rangle$$
```

with $s$

```
$$|\psi\rangle = \sum_{k=0}^{s} c_k |k\rangle$$
```

The estimated values of $net$ are represented by two qubits $[00], [01], [11]$. The natural number of $net$ corresponds to four states. A nonlinear activation function
