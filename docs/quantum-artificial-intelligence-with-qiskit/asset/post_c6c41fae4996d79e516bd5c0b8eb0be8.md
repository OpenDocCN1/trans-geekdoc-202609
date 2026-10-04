
# Preface

which two players take turns removing objects from distinct piles. A simplified version of the nim game with no piles, the five pennies nim game. Two players alternate remove either one, two, three pennies from a stack that initially contains five pennies. The player who pick up last penny loses. The five pennies nim game is a zero game where neither player has any legal options. The first player, wins if correct moves are chosen.

We indicate the architecture for the five pennies nim game and indicate that a quantum tree cannot implement the minimax-algorithm. We can determine the search path, but we cannot model the behavior of the player who chooses the best move since we cannot compare different states that are described by different path descriptors.

# Basis Encoding of Binary Vectors – Chapter 13

Quantum encoding is a process to transform classical information into quantum states. It plays a crucial role in using quantum algorithm. Basis encoding is the most intuitive way to encode classical binary vectors into a quantum state. It encodes n dimensional binary vector to an n-qubit state represented computational basis state. We will describe two approaches, a method that was developed by Ventura and Martinez and the method of entanglement of binary patterns with qubits in superposition.

# Quantum Associative Memory – Chapter 14

Quantum associative memory (QuAM) in the domain of quantum computation is a model with a capacity exponential in the number of neurons. Quantum Nearest Neighbor (QNN) is related to the QuAM. In QNN the binary patterns are stored by entanglement with index qubits. For Grover's amplification to the index qubits, we have to uncompute the entanglement of index qubits with the patterns. In QNN we need to uncompute. However, in QuAM we do not uncompute. In the QuAM proposed by Ventura and Martinez, a modified version of Grover's search algorithm is applied to determine the answer to a query vector so that instead of uncomputing we can apply Grover's algorithm to all qubits. Most QAM algorithms quantum associative memory suffer from the destruction problem where the classical data must be read and after the measurement the superposition collapses. However, the destruction problem is not solved until today, and usually theoretical speed ups are utilized. We will demonstrate a single QNN model, and a modified version of Grover's algorithm as proposed by Ventura and Martinez. We analyze the input destruction problem.

# Quantum Lernmatrix – Chapter 15

We introduce quantum Lernmatrix based on where n units are stored in the quantum superposition. Lernmatrix is an associative-memory-like architecture. During the retrieval phase, quantum counting of ones based on Euler's formula is used for the pattern recovery as proposed by Trugenberger. We demonstrate how to represent the quantum Lernmatrix by a quantum circuit and preform experiments using qiskit. Then we introduce a tree-like structure that increases the measured value of correct answers. During the active phase quantum Lernematics are queried and the results are estimated efficiently. The required time is much lower compared to the conventional approach or Grover's algorithm.

# Amplitude Encoding – Chapter 16

Amplitude encoding encodes a real or complex value vector of the length one into the amplitudes of a quantum state. We describe the top-down strategy and indicate the algorithm step by step. We describe the combining states strategy. Instead of representing the binary tree by multi-control rotation gates, we can use controlled SWAP operators with simple rotation gates. The resulting circuits depth less than the top-down divide; however, we require the same number of qubits as the number of rotation gates, and the qubits are entangled after the operation. We describe the possibility of initializing the desired states using qiskit commands. We cannot access the kernels that represent vectors, but we estimate the value of the scalar product between them using the swap test. We give two examples of the swap test.

# Quantum Kernels – Chapter 17

A quantum computer can estimate a quantum kernel, and the estimate can be used by a kernel method on a classical computer. This is because the exponential quantum advantage in evaluating inner products allows us to estimate the quantum kernel directly in the higher dimensional space. We give an example of quantum kernels and the swap test. We then describe quantum kernels and the inversion test. Quantum feature maps encode classical data into quantum data via a parametrized quantum circuit. Parameterized quantum kernels are based on superposition and entanglement. They are hard to simulate classically and could lead to an advantage over the classical ML approach. The inversion test is based on the usual use of estimating the fidelity (similarity) between two states. We describe an example using the qiskit command ZZFeatureMap. We then indicate how the quantum kernel is plugged into classical kernels like support vector machines.

# qRAM – Chapter 18

Quantum memory is proposed as an analogue to classical computer memory, like the random-access memory (RAM). RAM is a form of computer memory that can be read and changed in any order, typically used to store working data. In a quantum domain, the design of quantum random access memory (qRAM) is proposed to avoid the input destruction problem. We demonstrate the bucket brigade architecture of qRAM. The method of qRAM is related to the entanglement of the index qubits that are in the superposition with the patterns. We demonstrate an example of patterns and why the representation of amplitude coding leads to the same complexity as a recall on a classical RAM.

# Quantum Fourier Transform – Chapter 19

A periodic function can be represented in the frequency space. The frequency is the number of occurrences of a recurring event per unit of time. If something changes rapidly, then we say that it has a high frequency. If it does not change rapidly, it changes smoothly, so we say that it has a low frequency. The discrete Fourier transform converts time-based or space-based data into the frequency domain.

We describe the discrete Fourier transforms (DFT) and indicate the relation to the Quantum Fourier transform (QFT). We indicate how the QFT can be factored into the tensor product of $m$ single-qubit operations and implemented by basic quantum gates. We demonstrate examples of QFT for two, three, and four qubits. Then we indicate that the circuit for $m$ qubits can be imported from the qiskit library. We analyze the QFT costs and give a simple example of its

# Phase Estimation – Chapter 20

The Kitaev's Phase Estimation Algorithm (also referred to as a quantum eigenvalue estimation algorithm), is a quantum algorithm to estimate the phase (or eigenvalue) of an eigenvector of a unitary operator. We explain the algorithm and indicate an example of the determination of eigenvalue of the $T$ gate. Then we introduce the quantum counting algorithm based on the quantum phase estimation algorithm and on Grover's search algorithm. The quantum counting algorithm is a quantum algorithm for counting the number of solutions for a given search problem.

# Quantum Perceptron – Chapter 21

The classical perceptron describes an algorithm for supervised learning considers only linearly separable problems in which groups can be separated by a line or hyperplane. The quantum perceptron does not usually include learning, but instead computes the output of a binary unit (neuron) efficiently. It is based on the Kitaev's phase estimation algorithm. A quantum perceptron can be used as a building block of larger systems and it can process any arbitrary number of input vectors in parallel. We present a simple example of the quantum perceptron for two-dimensional input.

# HHL – Chapter 22

The quantum algorithm for linear systems of equations is one of the fundamental algorithms expected to provide a speedup over their classical counterparts. In honor of its inventors Arrow Harrow, Avinatan Hassidim, and Seth Lloyd, it is called the HHL algorithm. HHL is going to be one of the useful subroutines for any quantum ML algorithm because almost all ML uses some form of a linear system of equations. For example, in support vector machines and quantum support vector machines, maximizing the objective function with the optimum values of the Lagrange multipliers are based on solving linear equations. We describe the HHL algorithm, give an example step by step using qiskit command HamiltonianGate, and indicate the constraints of the algorithm.
