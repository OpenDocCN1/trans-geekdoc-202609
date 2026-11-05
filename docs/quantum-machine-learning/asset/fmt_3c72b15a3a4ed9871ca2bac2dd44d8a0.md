
where `y(t)` denotes the total response of the system, `x1(t)` represents the signal that fed to the system due to the first source, `x2(t)` is the input signal due to the second source, and `α` and `β` are constants that determine the amplitude of each input signal’s contribution to the total response.

This equation works on the assumption that the system is linear, which means that the relationship between its response to an input signal and the signal itself is linear. Superposition, in other words, enables us to treat every single input signal as a distinct building block in order to understand how the system reacts to each input separately. The system’s overall reaction to all inputs acting collectively can then be determined by adding these individual responses.

When two particles get entangled, even though they are separated by a great distance, their states cannot be defined independently of one another. This phenomenon is known as entanglement and is seen in quantum mechanics. In other words, two particles’ quantum states start to correlate in ways that exceed the laws of classical physics. This enables a number of remarkable features, including the capacity to quickly transform one particle’s state by observing another particle, irrespective of their spatial separation. Due to the potential for quicker computation and more secure communication, entanglement is an area of great significance in both quantum information theory and quantum computing.

The fundamental idea of entanglement in quantum physics is explained via a number of equations. Some examples include:

1. `The Bell Inequality`: John S. Bell, a physicist, developed this equation, which is frequently used to check for entanglement. It says that the correlation between two entangled quantum particles has a limit for every local hidden variable theory. Particles are said to be entangled if the measured correlation between them is greater than this threshold.
2. `The Schrödinger Equation`: This equation is the basic one for quantum mechanics, which explains how quantum states change over time. Two entangled particles will have a unique wave function that accounts for their entangled condition.
3. `The Entanglement Entropy`: The amount of entanglement between two quantum systems is measured using this equation. The degree to which the state of one system is associated with the state of the other is measured. The entanglement entropy is greatest when the two systems are most intertwined.
4. `The Density Matrix`: Mixed states, which are quantum states that are not purely entangled, can be defined by this equation. It considers the likelihood of each individual state that the system might be in, along with any relationships between various states.

In general, quantum information has the ability to have a profound impact on a number of scientific, engineering, and technological applications such as military manufacturing, construction,and finance modeling among others.

```
from qiskit import QuantumCircuit, exe, x
q = QuantumCircuit(1, 1)
# Apply Hadamard gate to create a superposition state
q.h(0)
# Evaluate qubit and store the result in a classical bit
q.measure(0, 0)
# Implement the circuit and get the result
simulator = x.get_backend('Gasm_Simulator')
result = execute(q, simulator).result()
# Publish the measurement value is result
print(result.get_counts(q))
```

A single qubit in a superposition of the 0 and 1 states is created by this circuit, which then measures it and records the results in a conventional bit. The measurement’s outcome will be printed out. Even though this is just a simple illustration, `Qiskit` is used to show the fundamental layout of a quantum circuit.

## 6.4 Entropy: Classical vs. Quantum

In contrast to classical entropy, which has been defined in its phase space, quantum entropy seems to be a measure of frequencies over an expanded Hilbert space. In information theory, quantum entropy deals with the entanglement of formation for both pure and mixed bipartite quantum states, whereas classical entropy corresponds to the study of collecting, transferring, and processing information [[9](#ch6.xhtml#ref6_9)]. Entropy is a thermodynamic term used to describe the degree of disorder or unpredictability in a system. In classical systems, where entropy is always non-negative, the rules of classical thermodynamics apply. The laws of quantum thermodynamics are more complicated than those of classical thermodynamics because entropy can be negative in quantum physics. In essence, the fundamental mathematical structure and underlying physical principles are what distinguish classical from quantum entropy.

The concepts used in information theory and the study of entropy include Shannon entropy and von Neumann entropy [[9](#ch6.xhtml#ref6_9)]. A measurement of the ambiguity in a random variable or probability distribution is called the Shannon entropy, named after Claude Shannon. It is referred to as an average amount of data required to determine the random variable’s value. The following is the formula for Shannon entropy:

(6.3)

`H(X) = - Σ[p(x) log2 p(x)]`

John von Neumann proposed the term von Neumann entropy to describe how unpredictable a quantum state is. It is known as the entropy of a density matrix and is employed in the study of quantum information. This is the entropy equation:

(6.4)

`S(ρ) = - Tr(ρ log2 ρ)`

Although the mathematical formulas for both notions are similar, they are applied in distinct situations. During the study of quantum phenomena, the entropy of a quantum state can be measured using von Neumann entropy. Shannon entropy is commonly employed in classical information theory for measuring the entropy of an uncertain variable or probabilistic distribution.

### 6.4.1 Classical Information Theory

Classical information theory is a mathematical theory of information handling, such as the transmission and storage of information, and was established by Claude Shannon in the 1940s and 1950s. The main areas addressed by the theory are the quantification, compression, and transmission of classical information, or information that is represented by a set of bits, as in digital communication systems. The fundamental constraints of information transmission via various channels and with varying levels of noise or distortion are the primary focus of classical information theory. Numerous industries, including telecommunications, computer science, cryptography, and data compression have found extensive uses for this. There are various mathematical equations and formulas applied in classical information theory, thus, there is no single equation that describes it all.

However, the Shannon entropy equation, which provides the entropy in the units of bits (per symbol), is among the most notable equations in classical information theory. It is written as follows:

(6.5)

`H(X) = - Σ p(x) log[2] p(x)`

where `p(x)` refers to the probability of the symbol `x`, and `log[2]` is the base-2 logarithm.

The Shannon channel capacity equation, which provides the highest speed in which data gets transferred across an uncertain communication path with an arbitrarily minimal error probability, is another, often-used equation. It is written as follows:

(6.6)

`C = B log[2](1 + S/N)`

where `C` refers to the channel capacity, `B` represents the channel bandwidth, `S` is the average signal power, `N` is the average noise power, and `log[2]` is the base-2 logarithm. Depending on the specific issue, classical information theory employs a number of additional equations and formulas.

A well-established field, namely classical information theory, studies the quantification and transmission of information. Given a channel’s capacity and level of noise, it offers a framework for evaluating how much data can be transmitted across it.
