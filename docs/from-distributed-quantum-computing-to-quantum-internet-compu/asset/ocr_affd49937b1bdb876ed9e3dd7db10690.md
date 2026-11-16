# 4
Distributed Quantum Computing – Distributed Control of Quantum Gates

This chapter looks at distributed quantum computing from a different perspective compared to Chapter 3. We will look at computations described by quantum circuits involving multiple qubits, where the qubits reside on multiple nodes, each node hosting one or more of the qubits. This chapter discusses nonlocal gates, or quantum gates for computations over several nodes. In particular, the chapter discusses the distributed CNOT gate, and different ways for its implementation, and discusses distributed control of gates beyond the CNOT gate. The discussion in this chapter is mainly based on the work by Yimsiriwattana and Lomonaco [2005] and earlier work by Eisert et al. [2000]. The CNOT gate is significant since using this gate and single qubit gates (or some suitable selection of gates as we saw in Chapter 2), one can achieve a universal gate set and realize a universal quantum computer. Hence, with single qubit gates (which would be local to the respective nodes on which the qubits reside) together with distributed CNOT operations, one effectively covers the range of possible distributed quantum circuit computations. The chapter also reviews briefly work on distributing quantum circuits and architectures for distributed control and management for distributed quantum computers.

# 4.1 Performing a Distributed CNOT

Consider a distributed CNOT operation where the control qubit is on one machine (say machine A) and the target qubit is on another machine (i.e. B). How can this be done?

# 4.1.1 Using Teleportation

Recall teleportation from Chapter 3 where a qubit state can be moved from one machine to another. So, one way is to teleport the qubit from A to B and then use