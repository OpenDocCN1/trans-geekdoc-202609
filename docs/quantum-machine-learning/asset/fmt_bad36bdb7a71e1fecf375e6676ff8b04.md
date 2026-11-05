
*   Reduce the quadratic function `f`(`x`) = `x`² − 4`x` + 4 its simplest form.
*   Subject to the restriction `x` as 0, 1

We may frame this problem as a quadratic binary optimization problem by introducing a binary variable `y` that represents the variable `x` in order to solve it using quadratic binary optimization. The following transformation can be used:

`x` = `y`(1−`y`)

Now, let’s convert the objective function and constraint into their binary forms:

Objective function:

$$\\begin{array}{cll} {f\\left( x \\right)} & = & {x^{2} - 4x + 4} \\\\ & = & {\\left( y\\left( 1 - y \\right) \\right)\\hat{}2 - 4\\left( y\\left( 1 - y \\right) \\right) + 4} \\\\ & = & {y\\hat{}2 - 2y\\hat{}2 + y\\hat{}2 - 4y + 4} \\\\ & = & {- 2y\\hat{}2 - 4y + 4} \\\\ \\end{array}$$

Constraint:

`x` ∈ {0,1}

=> `y`(1−`y`) ∈ {0,1}

The original problem has now been turned into a quadratic binary optimization problem. It can be expressed in the following standard form:

$$\\text{Reduce}: - 2y\\hat{}2 - 4y + 4$$

Subject to `y`(1−`y`) € {(0,1)}

Solving this quadratic binary optimization issue will provide us with the optimal `y` value, which we can then use to get the equivalent `x` value. Here are several QUBO problems that can be handled with quantum computing. One of the major problems is the Max-cut problem which is solved by a QUBO problem in the following way.

### 11.4.1 The Max-Cut Problem

Given an undirected graph containing a set of nodes and edges, the goal is to divide the nodes into two disjoint sets while maximizing the number of edges between the two sets. This problem may be expressed as a QUBO problem, with the variables representing node assignment to sets and the objective function aiming to maximize the number of severed edges.

The following is a definition of the Max-Cut problem:

Given an undirected graph `G` = (`V`, `E`), we wish to discover a partition of `V` into two disjoint sets, `S` and `S'`, such that the number of edges between `S` and `S'` (i.e., the cut) is maximized [[12](#ch11.xhtml#ref11_12)].

We can use quantum computing to solve the Max-Cut issue by mapping it to a QUBO problem.

The QUBO formula is as in equation (11.3):

(11.3)

Minimize : `H` = − ∑(`i`,`j`) ∈ `E` `w`(`i`,`j`)(`x`[`i`] * (1−`x`[`j`]) + (1−`x`[`i`]) * `x`[`j`])

where:
*   (`i`, `j`) represents a graph edge.
*   The weight of the edge between nodes `i` and `j` is represented by `G`. `w`(`i`, `j`).
*   `x`[`i`] and `x`[`j`] are binary variables that indicate whether node `i` and `j` are assigned to set `S` or `S'`.

The goal is to minimize the above Hamiltonian `H`, which equates to having the most clipped edges. Quantum computing technologies such as quantum annealing, or variational quantum algorithms can be used to solve this QUBO formulation. Quantum annealing searches for the lowest energy state of the QUBO problem, which corresponds to the optimum node partition. In contrast, variational quantum algorithms employ parameterized quantum circuits to iteratively optimize the QUBO objective function, eventually convergent to the ideal solution.

We may explore the solution space more efficiently and discover better answers than classical optimization techniques in some situations by transferring the Max-Cut problem to a QUBO formulation and employing quantum computing technologies.

## 11.5 Ising Model

The Ising model is a traditional statistical physics model for studying magnetic systems. It represents a collection of spins that can be in either an “up” or “down” state and their interactions are guided by an energy function that relies on their respective orientations. The Ising model has also been utilized as a starting point for understanding some types of quantum systems in the context of quantum computing. The Ising model is especially relevant to certain types of quantum annealing devices, such as those based on superconducting qubits. It has a lattice structure because it only considers the closest neighbor interactions dictated by the alignment or anti-alignment of spin projections along the Z axis. The alignment in the Ising model is likewise regulated by the external magnetic field [[13](#ch11.xhtml#ref11_13)].

The Hamiltonian of the quantum Ising model is given by equation (11.4):

(11.4)

$$H = - J\\;\\left( {}\_{(i,j)}^{\\Sigma}z\_{i}z\_{j} + g\\sum\\limits\_{j}x\_{j} \\right.$$

The indexes `i`, and `j` are representing lattice sites and the sum is taken over the pairs of nearest neighbors. The prefactor `j` has dimensions of energy and factor `g` indicates the strength of the externally applied field relating to nearest neighbor interaction. The `x`[`j`] and `z`[`j`] represent components or spin algebra acting over spin variables of corresponding sites.

The 1D model of each lattice site is a two-dimensional complex Hilbert space. The Hamiltonian of the 1D quantum model poses `z`[2] symmetry, it remains invariant under the transformation of flipping of all the spins about the `Z` axis. As we know that every phase transition involves some kind of spontaneous symmetry breaking. The 1D model also has two phases depending on whether the ground state preserves or breaks the spin-flip symmetry [[14](#ch11.xhtml#ref11_14)]. Qubits in the Ising model are often expressed using Dirac notation or ket notation. A qubit can be expressed as a column vector:

|ψ⟩ = α|0⟩ + β|1⟩,

where `α` and `β` are complex probability amplitudes, |0⟩ represents the “0” state, and |1⟩ represents the “1” state.

## 11.6 Sparsity, Bit Depth, and Generalization Performance

Sparsity, bit depth, and generalization performance are key concerns in the context of quantum computing, as they relate to the efficiency and efficacy of quantum algorithms. Sparsity is a quality of a quantum system, or the data on which it acts, in which a large part of the components or parameters are zero or near to zero. Sparsity denotes that only a tiny proportion of the components in a quantum state or a quantum operation are non-zero. Quantum systems are distinguished by short coherence durations, imprecise gates, and vulnerability to noise and mistakes. Using sparsity to limit the number of processes and resources required to conduct a computation can result in increased efficiency. Quantum algorithms can minimize the number of operations, gate operations, or measurements required by focusing on non-zero items and disregarding zero elements, reducing the effect of mistakes and the total computational cost. Sparsity is also important in quantum computing data representation and transmission. In terms of memory consumption and communication bandwidth, storing and sending sparse quantum states or processes can be more efficient. Rather than recording and transmitting all of the constituents of a quantum state, just the non-zero elements can be represented and sent, resulting in decreased storage needs and enhanced communication efficiency [[15](#ch11.xhtml#ref11_15)]. Sparsity in quantum computing can be theoretically described using various notations and frameworks depending on the circumstance. The following are some typical mathematical notations for describing sparsity in quantum computing:

(11.5)

$$|ψ⟩ = ∑ c[i] |i⟩$$
