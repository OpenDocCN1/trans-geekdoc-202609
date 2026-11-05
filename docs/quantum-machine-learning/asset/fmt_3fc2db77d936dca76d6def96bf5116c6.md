
## Mathematical Example

After applying the Hadamard gate, the state `|Ψ⟩′` of the quantum neuron is:

$$\\left. \\mid \\Psi \\right\\rangle\\prime = \\left( 1/\\left. \\sqrt{}2 \\right)\\left( \\alpha \\mid 00 \\right\\rangle + \\alpha \\mid 01 \\right\\rangle\\left. + \\beta \\mid 10 \\right\\rangle\\left. + \\beta \\mid 11 \\right\\rangle\\left. + \\gamma \\mid 00 \\right\\rangle\\left. - \\gamma \\mid 01 \\right\\rangle\\left. + \\delta \\mid 10 \\right\\rangle\\left. - \\delta \\mid 11 \\right\\rangle).$$

When the quantum neuron is measured, the outcome would be one of the possible states with corresponding probabilities `|α|²`, `|β|²`, `|γ|²`, and `|δ|²`. The measurement result gives a probabilistic output for the quantum neuron.

Quantum neurons in deep neural networks are an essential component of quantum deep learning, harnessing the power of quantum superposition and entanglement to process information efficiently. By leveraging quantum properties, quantum neurons have the potential to provide computational advantages over classical neurons in solving specific problems. Quantum deep neural networks are an exciting area of research that bridges quantum computing with deep learning, promising advancements in various fields, including optimization, pattern recognition, and machine learning.

## 10.2.4 Quantum Operations and Quantum Gates

In quantum computing, quantum operations are fundamental transformations applied to quantum states to manipulate and process information. These operations are implemented using quantum gates, which are analogous to logic gates in classical computing. Quantum gates act on qubits, the basic units of quantum information, to perform specific transformations and computations.

### 10.2.4.1 Quantum Operations

Quantum operations are unitary transformations that preserve the norm of quantum states, ensuring that the total probability of finding the system in any state remains 1. These operations are reversible, meaning that they can be undone by applying the inverse operation. Some common quantum operations include ([Figure 10.7](#ch10.xhtml#fig10_7)):

![Figure 10.7 Quantum operations.](images/fig10_7_B.jpg)

[Figure 10.7 Quantum operations.](#ch10.xhtml#R_fig10_7)

1. Hadamard Gate (`H`): The Hadamard gate is a fundamental quantum gate that creates superposition by evenly distributing the probability amplitudes of `|0⟩` and `|1⟩` states. It is represented as:

$$H = \\frac{1}{\\sqrt{2}} \\ast \\begin{bmatrix} 1 & 1 \\\\ 1 & {- 1} \\\\ \\end{bmatrix}\\mspace{2mu}$$

When applied to a single qubit, the Hadamard gate transforms the states as follows:

$$\\left. H \\mid 0 \\right\\rangle = 1/\\left. \\sqrt{}2\\;\\left( \\mid 0 \\right\\rangle + \\mid 1 \\right\\rangle),$$

$$\\left. H \\mid 1 \\right\\rangle = 1/\\left. \\sqrt{}2\\;\\left( \\mid 0 \\right\\rangle - \\mid 1 \\right\\rangle).$$

2. Pauli Gates (`X`, `Y`, `Z`): The Pauli gates are single-qubit gates that correspond to rotations around the `X`, `Y`, and `Z` axes of the Bloch sphere, respectively. They are represented as:

$$X = \\begin{bmatrix} 0 & 1 \\\\ 1 & 0 \\\\ \\end{bmatrix},$$

$$Y = \\begin{bmatrix} 0 & {- i} \\\\ i & 0 \\\\ \\end{bmatrix},$$

$$Z = \\begin{bmatrix} 1 & 0 \\\\ 0 & {- 1} \\\\ \\end{bmatrix},$$

When applied to a single qubit, the Pauli gates transform the states as follows:

`X`|0⟩=`|1⟩`,

`X`|1⟩=`|0⟩`,

`Y`|0⟩=`i`|1⟩,

`Y`|1⟩=`−i`|0⟩,

`Z`|0⟩=`|0⟩`,

`Z`|1⟩=`−`|1⟩.

3. Controlled-NOT (`CNOT`) Gate: The CNOT gate is a two-qubit gate that applies the Pauli-X gate to the target qubit (second qubit) if and only if the control qubit (first qubit) is in the state `|1⟩`. It is represented as:

$$\\text{CNOT} = \\begin{bmatrix} 1 & 0 & 0 & 0 \\\\ 0 & 1 & 0 & 0 \\\\ 0 & 0 & 0 & 1 \\\\ 0 & 0 & 1 & 0 \\\\ \\end{bmatrix}.$$

When applied to two qubits in the state `|00⟩`, `|01⟩`, `|10⟩`, and `|11⟩`, the CNOT gate performs the following transformations:

`CNOT`|00⟩=`|00⟩`,

`CNOT`|01⟩=`|01⟩`,

`CNOT`|10⟩=`|11⟩`,

`CNOT`|11⟩=`|10⟩`.

## 10.2.5 Quantum Gates in Quantum Circuits

Quantum circuits are constructed using a combination of quantum gates, enabling complex quantum computations. Quantum gates are applied sequentially to perform specific operations on qubits. Quantum circuits are designed to solve quantum algorithms, simulate quantum systems, and perform various quantum tasks ([Figure 10.8](#ch10.xhtml#fig10_8)).

![Figure 10.8 Quantum gates in quantum circuits.](images/fig10_8_B.jpg)

[Figure 10.8 Quantum gates in quantum circuits.](#ch10.xhtml#R_fig10_8)

### Example Quantum Circuit

Consider a simple quantum circuit consisting of two qubits, represented as `|ψ⟩ = α|00⟩ + β|01⟩ + γ|10⟩ + δ|11⟩`. To apply the Hadamard gate (`H`) to the first qubit, the quantum circuit is as follows:

Apply Hadamard gate (`H`) to the first qubit:

`H` ⊗ `I` (identity gate) applied to `|ψ⟩`.

The resulting quantum state would be:

`H`|ψ⟩ = (`H`⊗`I`)(`α`|00⟩+`β`|01⟩+`γ`|10⟩+`δ`|11⟩) = (`α`+`β`)|00⟩ + (`γ`+`δ`)|10⟩.

In this example, the Hadamard gate creates a superposition of `|00⟩` and `|10⟩` states, demonstrating the power of quantum gates to manipulate quantum states and perform quantum operations.

Quantum operations and quantum gates are fundamental building blocks of quantum computing. They enable the manipulation and processing of quantum information and play a critical role in quantum algorithms and quantum circuits. Quantum gates, such as the Hadamard gate, Pauli gates, and CNOT gate, perform specific transformations on qubits, allowing quantum systems to leverage unique quantum properties, such as superposition and entanglement, for solving complex problems and outperforming classical counterparts in specific tasks.

### 10.2.5.1 Quantum Circuit Layers

Quantum circuit layers are essential components of quantum algorithms and quantum computations. A quantum circuit is composed of a sequence of quantum gates applied to qubits, and these gates are typically grouped into layers to facilitate the execution of specific operations on quantum states. Each layer represents a specific transformation of the quantum state and can be customized based on the problem being solved or the quantum algorithm being executed ([Figure 10.9](#ch10.xhtml#fig10_9)).

![Figure 10.9 Quantum circuit layers.](images/fig10_9_B.jpg)

[Figure 10.9 Quantum circuit layers.](#ch10.xhtml#R_fig10_9)

1. Structure of Quantum Circuit Layers:

* ***Layered quantum gates***: In a quantum circuit, quantum gates are organized into layers, where each layer consists of multiple gates applied sequentially. Gates within the same layer are typically applied in parallel to qubits, allowing for quantum parallelism and efficient computation.

* ***Depth and width of quantum circuits***: The depth of a quantum circuit refers to the number of layers, and the width refers to the number of qubits in the circuit. The depth of the circuit determines the number of sequential steps required to perform a computation, while the width defines the number of qubits involved in each step.

2. Advantages of Quantum Circuit Layers:

* ***Modular design***: Quantum circuit layers allow for a modular design, where different layers can be designed independently to perform specific operations on qubits. This modular structure makes it easier to design and optimize quantum circuits for specific tasks and quantum algorithms.

* ***Error mitigation***: Layered quantum circuits can be designed with error mitigation techniques in mind. By grouping gates into layers, it becomes possible to identify and correct errors that may arise during the quantum computation, enhancing the robustness and reliability of the quantum circuit.
