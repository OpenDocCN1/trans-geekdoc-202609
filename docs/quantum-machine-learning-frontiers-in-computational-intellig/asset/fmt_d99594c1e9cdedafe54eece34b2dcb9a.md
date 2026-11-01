
Quantum entanglement \[[28](#bodymatter-004.xhtml#b_9783110670707-004_ref_028)\] is a very important property of quantum mechanics, in which qubits interact with each other instantaneously irrespective of the distances between them through an unknown way of communication that is not limited to the speed of light. Correlated particles remain entangled as long as they are isolated irrespective of the distance between them.

If we cannot factor a multi-qubit state into the direct product of a definite state for each qubit individually, then the states are entangled. Hence, a pair of qubits `A` and `B` are entangled if and only if we cannot write the joint state |`ψ`[`A``B`]?⟩ as the product of a state for qubit A and a state for qubit B, i.e., if and only if |`ψ`[`A``B`]?⟩=|`ψ`[`A`]?⟩ ⊗ |`ψ`[`B`]?⟩ for any choice of states |`ψ`[`A`]?⟩ and |`ψ`[`B`]?⟩.

We are considering two non-interacting systems `A` and `B`, with respect to finite dimensional Hilbert spaces `H`[`A`] and `H`[`B`].

`H`[`A`] ⊗ `H`[`B`] is the tensor product of the composite system in the Hilbert space. The state of the composite system is |`ψ`[`A`]?⟩ ⊗ |`ψ`[`B`]?⟩, where the first system is in state |`ψ`[`A`]?⟩ and the second in the state |`ψ`[`B`]?⟩.

The above represented states of the composite system are separable states. But, all states are not, in general, the separable states.

By fixing a basis |`i`[`A`]?⟩ for `H`[`A`] and a basis | `j`[`B`]?⟩ for `H`[`B`], the most general state in `H`[`A`] ⊗ `H`[`B`] is of the form:

(4.12)$|\\psi\_{AB}\\rangle = \\sum\\limits\_{i,j}c\_{ij}\\left| {i\_{A}\\rangle\\; \\otimes \\;} \\right|j\_{B}\\rangle$

This state is separable if

(4.13)*c*[*i**j*] = *c*[*i*]^(`A`)*c*[*j*]^(`B`)

yielding:

(4.14)$|{\\psi\_{A}\\rangle = \\sum\\limits\_{i,j}c\_{i}^{A}|{i\_{A}\\rangle\\;{and}}\\;|\\psi\_{B}\\rangle = \\sum\\limits\_{j}c\_{i}^{B}}|j\_{B}\\rangle\\ $

It is inseparable if

(4.15)*c*[*i**j*] ≠ *c*[*i*]^(`A`)*c*[*j*]^(`B`)

If a state is not separable, it is known as entangled state.

For example, the following composite state is an entangled state:

(4.16)$\\frac{1}{\\sqrt{2}}\\left( {\\left| {0\_{A}\\rangle\\; \\otimes \\;} \\right|1\_{B}\\rangle - \\left| {1\_{A}\\rangle\\; \\otimes \\;} \\right|0\_{B}\\rangle} \\right),$

where |0[`A`]?⟩ & |1[`A`]?⟩ are two basis vectors of `H`[`A`] and |0[`B`]? & |1[`B`]? are two basis vectors of `H`[`B`].

## 4.2.5 Quantum adiabatic model

If a quantum system is set in the ground state of a Hamiltonian `H`, the system remains in this state. According to the adiabatic theorem \[[18](#bodymatter-004.xhtml#b_9783110670707-004_ref_018)\], the system will still stay close to the ground state as long as the variation is very slow enough. Suppose that |`E`[0]; `t`⟩ & |`E`[1]; `t`⟩ are the ground and first excited states of the Hamiltonian `H`(`t`), where `E`[0](`t`) and `E`[1](`t`) are the energies corresponding to the ground and first excited states, respectively. We then define the minimum gap between these two eigenvalues as:

(4.17)$g\_{min} = \\min\\limits\_{0 \\leq t \\leq T}\\left\\lbrack {E\_{1}\\left( t \\right) - E\_{0}\\left( t \\right)} \\right\\rbrack$

So, when we prepared the system at time `t` = 0 in its ground state |`E`[0]; 0 and allow it to evolve under the Hamiltonian `H`(`t`), we find:

(4.18)|⟨`E`[0];`T`|`ψ`(`T`)⟩|² ≥ 1 − `ε`²

where $1 \\gg \\varepsilon \\geq \\frac{\\max\\limits\_{0 \\leq t \\leq T}\\left| \\left\\langle \\frac{dH}{dt} \\right\\rangle\_{1,0} \\right|}{g\_{min}^{2}}$, and $\\left\\langle \\frac{dH}{dt} \\right\\rangle\_{1,0} = \\left\\langle {E\_{1};\\, t|\\frac{dH}{dt}|E\_{0};\\, t} \\right\\rangle$

## 4.2.6 SWAP-test

A `SWAP-test` estimates |⟨`ψ`[1]|`ψ`[2]⟩|², when given two input quantum states |`ψ`[1]⟩ and |`ψ`[2]⟩, with precision $O\\left( \\frac{1}{\\sqrt{M}} \\right)$, where `M` is the number of times the measurement has been done.

## 4.2.7 Quantum algorithms

Quantum algorithms are the special type of algorithms that are written for running on a quantum computer. These algorithms are based on the principles of quantum mechanics. This is one very active research area, and recent research works show that many of the quantum versions of classical algorithms are way more efficient in terms of computational complexity, with some of them being exponentially faster than the classical counterparts. Some of the most known quantum algorithms are Grover’s search algorithm \[[10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010)\], Shore’s algorithm \[[19](#bodymatter-004.xhtml#b_9783110670707-004_ref_019)\], quantum support vector machine \[[21](#bodymatter-004.xhtml#b_9783110670707-004_ref_021), [23](#bodymatter-004.xhtml#b_9783110670707-004_ref_023), [24](#bodymatter-004.xhtml#b_9783110670707-004_ref_024)\], and the HHL algorithm \[[20](#bodymatter-004.xhtml#b_9783110670707-004_ref_020)\].

# 4.3 Essential foundations for building a quantum machine learning framework

In this section, we discuss the essential foundations to develop quantum machine learning algorithms. These foundational concepts are very important. No single concept can be used to develop a quantum machine algorithm, and different concepts are used to cultivate different algorithms. In this section, we explain some of the very key foundational concepts which provide support in building quantum machine learning algorithms. We have discussed how different approaches used these concepts to articulate a variety of quantum machine algorithms in Section 4.4 & [4.5](#bodymatter-004.xhtml#b_9783110670707-004_s_004_s_005).

## 4.3.1 Grover’s search algorithm

Grover’s search algorithm \[[10](#bodymatter-004.xhtml#b_9783110670707-004_ref_010)\] is a quantum search algorithm which performs the search to find a unique item from an unordered set of `N` items with $O(\\sqrt{N})$ run time complexity. The best counter classical search algorithm performs with `O`(`N`) runtime complexity. The algorithm is as follows \[[29](#bodymatter-004.xhtml#b_9783110670707-004_ref_029)\]:

### Algorithm 1: Grover’s Search Algorithm

1. Initialize quantum state |0⟩^( ⊗ `n`)

2. Apply the Hadamard transformation to all the qubits

$|\\psi\\rangle = H^{\\otimes n}|0\\rangle^{\\otimes n} = \\frac{1}{\\sqrt{2^{n}}}\\sum\\limits\_{y = 0}^{2^{n} - 1}|y\\rangle$

1. Apply the Grover iteration function `R` $\\approx \\frac{\\pi}{4}\\sqrt{2^{n}}$ times

\[(2|`ψ`⟩⟨`ψ`|`−`I`)𝒪\]^(`R`)|`ψ`⟩≈|`y`[0]

1. Perform the measurement for output, `y`[0]

## 4.3.2 Quantum random access memory

Quantum random access memory (`QRAM`) \[[30](#bodymatter-004.xhtml#b_9783110670707-004_ref_030)\] is the random access memory in a quantum paradigm. It encompasses the output and the address registers which are composed of qubits. The `QRAM` permits to access the data quantum mechanically and access the memory in coherent quantum superposition. The address register embraces a superposition of addresses. The data register `D`R stores the output of the `QRAM` as a superposition of data, which is associated with the address register `R`[`A`D`R`],

(4.19)∑[`j`]`ψ`[`j`]|`j`⟩[`R`[`A`D`R`]]→ ∑[`j`]`ψ`[`j`]|`j`⟩[`A`D`R`]|`D`[`j`]⟩[`D`R]

where `R`[`A`D`R`] holds a superposition of addresses ∑[`j`]`ψ`[`j`]|`j`⟩[`R`[`A`D`R`]], and `D`[`j`] is the `j`^(`t`h) memory cell content. Reconstructing any quantum state from `QRAM` takes `O`(`l`o`g` `N`) steps, where `N` is the complex vector dimension.

## 4.3.3 Quantum dot product
