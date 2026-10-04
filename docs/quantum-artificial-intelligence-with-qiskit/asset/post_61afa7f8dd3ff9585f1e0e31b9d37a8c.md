
[content]

| q_0: | P(2.0*x[0]) | |
| :--- | :--- | :--- |
| q_1: | P(2.0*x[0]) | X | P(2.0*(n - x[0])*(n - x[1])) | X |
| q_0: | U2(0,n) | U(0,0,2.0*x[0]) | |
| q_1: | U2(0,n) | U(0,0,2.0*x[1]) | X | U(0,0,2.0*(n - x[0])*(n - x[1])) | X |

Figure 17.3 (a) The ZZFeatureMap with 2 features and depth 1, this is the same feature map that was used in the previous section. (b) The same ZZFeatureMap indicated using twice decompose(),decompose() indicating the quantum gates that are used. (c) The ZZFeatureMap with 3 features and depth 1.

## 17.4 QUANTUM SUPPORT VECTOR MACHINE

The quantum kernel is plugged into classical kernel methods like Support Vector Machine (Kernel Machine). Only the Gram matrix (kernel matrix) is determined by a quantum computer (or a simulation), the other parts of the computation are performed on a conventional computer. Either one passes a function of the quantum kernel to a conventional algorithm or one precomputes the training and testing kernel matrices. Often the actual internal representations of the quantum kernel are hidden from the outside.

## qRAM

Quantum memory is proposed as an analogue to classical computer memory, like the random-access memory (RAM). RAM is a form of computer memory that can be read and changed in any order, typically used to store working data. In quantum machine learning domain, the usage of quantum random memory (qRAM) is proposed to avoid input destruction problem. We demonstrate the bucket brigade architecture of qRAM. The method of qRAM is related to the entanglement of the index qubits that are in the superposition with the patterns. We demonstrate an example of binary patterns and indicate why the representation of amplitude coding leads to the same complexity as a recall operation on a classical RAM.

## 18.1 QUANTUM RANDOM ACCESS MEMORY

In quantum machine learning domain, the usage of qRAM [32] is proposed to avoid input destruction problem (ID problem) [59], [39]. A qRAM copies basis states [32] and load the i-th binary pattern into the second register

$|i\rangle \rightarrow |x^i\rangle$. (18.1)

with $|x^i\rangle$ being a basis state representing a binary vector. Such an operation can be executed in parallel

$\frac{1}{\sqrt{m}} \sum_{i=1}^m |i\rangle \rightarrow \frac{1}{\sqrt{m}} \sum_{i=1}^m |x^i\rangle$, (18.2),$

with time complexity increasing the preparation cost of query (due to the input problem) is $O(\log(m))$.

### 18.1.1 The Bucket Brigade Architecture of qRAM

The bucket brigade architecture of qRAM is inspired by the traditional RAM architecture and consists of three main parts:

- *Addressing qubits*: Address for the memory cell we wish to read. In order to read a memory cell, the user must encode the address of memory cell to the addressing qubits. This address can be in superposition so that several patterns can be read in one step.
- *Routing nodes*: Determine the memory cell based upon the states of the addressing qubits. Once the addressing qubits have been set the states of the routing nodes qubits will be effected. Whatever qubit in the routing nodes is 1 will lead to the memory cell that we wish to read.
- *Memory cells*: Store and readout patterns.

The method of qRAM is related to the entanglement of the index qubits in the superposition with the patterns. As in the method of the entanglement of the index qubits, the qubits of qRAM are entangled during the reading operation and have to be un-computed after computation. An example of the qRAM (see Figure 18.1).

```python
from qiskit import QuantumCircuit, Aer, execute
from qiskit.visualization import plot_histogram

c = QuantumCircuit(9)
#address
#0-1
#Routing
#2-5
#Memory
#6-8
#address
qc.h(0) two first elements of the memory
#Routing operation
#The addresses are ordered 00, 01, 10, 11
qc.barrier()
qc.x(0)
qc.x(1)
qc.ccx(0,1,2)
qc.x(1)
qc.x(0)
qc.barrier()
qc.x(1)
qc.ccx(0,1,3)
qc.x(1)
qc.barrier()
qc.x(0)
qc.ccx(0,1,4)
qc.x(0)
qc.barrier()
qc.ccx(0,1,5)
qc.barrier()
#Memory cells 6-8
#First memory cell
qc.barrier()
qc.cx(2,6)
qc.cx(2,8)
#Second memory cell
qc.barrier()
```

![](img/52faec2d621d75e5308d93bb4a270_0.png)
![](img/52faec2d621d75e5308d93bb4a270_1.png)

Figure 18.1 (a) qRAM circuit: address is represented by qubits 0 and 1, routing by qubits 2 to 5, and the memory by qubits 6 to 8. The addresses are ordered 00, 01, 10 and for the last pattern 11. (b) The address corresponds to the first qubit in superposition, address 00 and 01. The first and second patterns are recalled.

```python
qc.cx(3,6)
qc.cx(3,7)
#Third memory cell
qc.barrier()
qc.cx(4,6)
qc.cx(4,7)
qc.cx(4,8)
#Fourth memory cell
qc.barrier()
qc.cx(5,7)

simulator = Aer.backend('statevector_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
plot_histogram(counts)
```

### 18.1.2 Amplitude Coding

An operation that would produce a copy of an arbitrary state as $|\psi\rangle$ is not possible; we cannot copy non-basis states because of the linearity of quantum mechanics. We can to some extent simulate the copy of non-basis states using qRAM, with the complexity $O(\log(m))$ where $n$ is the dimension of the resulting vector. We have a basis state of $m$ qubits $|x\rangle = |0\dots 1\rangle$ of dimension $2^m$ into a $n$-dimensional superposition we divide the binary vector of dimension $2^m$ into $v$ parts, each $code_i$, a real number with $n=2^m/v$.

$|0\dots1\rangle\cdot\frac{1}{\sqrt{n}}\sum_{i=1}^n|i\rangle\to|0\dots1\rangle\cdot\frac{1}{\sqrt{n}}\sum_{i=1}^n\alpha_i|i\rangle$. (18.3)

We add an auxiliary state $|0^n\rangle$

$|code_{1\dots v}\rangle\cdot\frac{1}{\sqrt{n}}\sum_{i=1}^n|i\rangle\to|code_{1\dots v}\rangle\cdot\frac{1}{\sqrt{n}}\sum_{i=1}^n|i\rangle|0^n\rangle$. (18.4)

For each $code_i$ represents a binary representation of a fractional real number that is smaller than one

$code_i = \alpha_i < 1$.

For each $value_i$, we perform a controlled rotation $R(\alpha_i)$

$(\alpha_i|1\rangle+\sqrt{1-\alpha_i^2}|0\rangle)$

and perform a measurement. By measuring the corresponding auxiliary register with the result 1 we know that the resulting state is correct. We repeat the procedure at least $n$ times with the resulting state

$|0\dots1\rangle\cdot\sum_{i=1}^n\alpha_i|i\rangle$. (18.6)

The resulting complexity of the routine is $O(n)$, which is the same as reading classical information. However to read classically $m$ vectors of dimension $n$, the complexity is $O(n\cdot m)$, using qRAM ignoring the preparation cost is $O(\log(m))$. The described routine is non-reversible since it is based on measurement.

## Quantum Fourier Transform

A periodic function can be represented in the frequency space. The frequency is the number of occurrences of a repeating event per unit of time. If something changes rapidly, then we say that it has a high frequency. If it does not change rapidly, i.e. it changes smoothly, we say that it has a low frequency. The discrete Fourier transform converts discrete time-based or space-based data into the frequency domain. We describe the DFT and indicate the relation to quantum Fourier transform (QFT). We indicate how the QFT can be factored into the tensor product of $m$ single-qubit operations and implemented by basic quantum gates. We demonstrate examples of QFT for two, three, and four qubits. We then indicate that the circuit for $m$ qubits can be imported from the qiskit library. We analyze the QFT costs and give an simple example of its operation.

## 19.1 DISCRETE FOURIER TRANSFORM

The DFTs discrete time-based or space-based data into the frequency sequence-based data. Given a sequence

$\alpha_t : [1, 2, \dots, n] \rightarrow C$.

The DFT produces a sequence $\omega$:

$\omega_f : [1, 2, \dots, n] \rightarrow C$.

The DFT of $\alpha(t)$ is

$\omega_f = \frac{1}{\sqrt{n}}\sum_{t=1}^{n} \alpha_t \cdot e^{-2\pi i(t-1) \frac{(f-1)}{n}}$

its wave frequency is $\frac{(f-1)}{n}$ events per sample. The inverse DFT of $\omega_f$ is

$\alpha_t = \frac{1}{\sqrt{n}}\sum_{f=1}^{n} \omega_f \cdot e^{2\pi i(t-1) \frac{(f-1)}{n}}$.

[/content]
