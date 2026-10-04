
# 100 ■ Quantum Artificial Intelligence with Qiskit

```python
qc.barrier()
qc.h([0,1,4])
qc.x([0,1,4])
qc.h(0)
qc.ccx(1,4,0)
qc.h(0)
qc.barrier()
qc.x([0,1,4])
qc.h([0,1,4])
```

```python
qc.measure(0,0)
qc.measure(1,1)
qc.measure(4,2)
```

```python
qc.draw(fold=165)

simulator = Aer.get_backend('qasm_simulator')
result=execute(qc,simulator,shots=1000).result()
counts = result.get_counts()
print("\nTotal count are:",counts)
```

```python
plot_histogram(counts)
```

## 6.3.4 No Solution

For the Boolean formula

> $\phi = (x_1 \leftrightarrow x_2) \wedge (\neg x_1 \wedge x_2) \wedge \neg x_3$

no solution exists, the formula can never evaluate to value true. We change our circuit correspondingly with

```python
#First And 2 is zero
qc.x(0)
qc.ccx(0,1,2)
qc.x(0)
qc.barrier()
#Result in 2
```

In the next step we apply Grover's amplification; however no state is marked. Figure 6.6 the distribution of the eight possible instantiations for $x_1, x_2$, and $x_3$ after one Grover's amplification and two Grover's amplifications are indicated.

![](img/52faec2d621d75e53089d939bb234a82_127_0.png)

**Figure 6.6** For the Boolean formula $\phi = (x_1 \leftrightarrow x_2) \wedge (\neg x_1 \wedge x_2) \wedge \neg x_3$ no solution exists. The qubits 0, 1, and 4 indicate the eight possible instantiations for $x_1, x_2$, and $x_3$. (a) The distribution of the eight possible instantiations for $x_1, x_2$, and $x_3$ after one rotation. (b) the distribution after two rotations. Each instantiation has nearly the same count, no solution exists.

The qubits 0, 1, and 4 indicate the eight possible instantiations for $x_1, x_2$ and $x_3$ for the $\phi = (x_1 \leftrightarrow x_2) \wedge (x_1 \wedge x_2) \wedge \neg x_3$ SAT problem. Each instantiation has nearly the same count after applying Grover's amplification and no solution exists.

## Symbolic State Representation

An economic symbolic representation of objects and attributes that can represent a state during problem solving is introduced. This representation is motivated by the biological what-where principle and requires a low number of bits. Such an economical demanded representation is ideal for the current generation of quantum computers. We describe the search tree on which problem solving is based. Nodes and edges represent a search tree. Each node represents a state, and each edge represents a transition from one state to the following state. The path descriptors are the basis of quantum tree search. In a quantum tree search we represent all possible path descriptors simultaneously and use Grover's amplification algorithm to determine the solution.

## 7.1 BIT REPRESENTATION OF OBJECTS AND ATTRIBUTES

We represent $n$ symbols with $\lceil\log_2n\rceil$ bits. To represent four symbols $A, B, C, D$ we require two bits with the following code: $A=00, B = 01, C = 10, D = 11$. To represent a string $B A D C$ we code each symbol at a corresponding position: $01 00 11 10$. In this representation the attribute is fixed, and the code descriptors of the object moves. Each object can have one or more attributes (adjectives), like position in one or two dimensions. In our case the attribute corresponds to the position in the representation. Instead of coding symbols we alternatively code the positions, for four positions we code the first position by 00, second position by 01, third position by 10 and fourth position by 11. A symbol would be represented by the order, to represent a string $D B A C$ with code $10 01 00 11$. $A$ at position 10 (the string), $B$ at position 01 (second position in the string), $C$ at position 11 (fourth position in the string), and $D$ at position 00 (first position in the string). In this representation the code descriptors of the object are fixed, and the attribute moves. In the case several attributes are present, it is more economical to represent the code fixed some attributes may change while the other remain fixed. During the problem solving of objects remains fixed, only the values of the attributes

# Symbolic Representation ■ 103

Objects cannot disappear or appear. A state is of object and attributes is described by fixed number bits that change its position, a rule corresponds to the permutation of bits. This kind of representation is related to the biological what principle.

### 7.1.1 “What” and “Where”

Gross and Misskin [34] suggested that the brain includes two mechanisms for visual categorization: one for the representation of the object and the other for the representation of localization [57, 52, 79]. The first mechanism is called the “what” pathway and is composed of the temporal lobe. The second mechanism is called the “where” pathway and is composed of the partial lobe [52, 79]. According to this division, the identity of a visual object can be coded apart from the location and the size of the object.

## 7.2 TREE SEARCH AND PATH DESCRIPTORS

Nodes and edges represent a search tree. Each node represents a state, and each edge represents a transition from one state to the following state. The initial state define the root of the tree. From each state, $B$ or $C$ states can be reached, or the state is a leaf. From a leaf, no other state can be reached, $B$ represents the branching factor of the node, the number of possible choices. A leaf represents either the goal of the computation or an impasse when there is no valid transition to a succeeding state. Every node beside the root has a unique node from which it was reached, which is called the parent. Each node and its parent are connected by an edge. Each parent has $B$ children, each has a reply of “yes” or “no” and can be represented by a bit (see Figure 7.1). The answers are represented by a binary number of length $m$. There are $n=2^m$ possible binary numbers of length $m$. Each binary number represents a path from the root to a leaf. For each goal, a certain binary number indicates the solution. For a constant branching factor $B>2$, each question has $B$ possible answers. The $m$ answers can be represented by $m$ digits. For example, with $B=8$, the number is represented by $2^3$ bits. These numbers represent all paths from the root to the leaves.

## 7.3 QUANTUM TREE SEARCH

In a quantum computation, we can simultaneously represent all possible path descriptors. This is one descriptor for each leaf of the search tree. Using Grover’s algorithm, we search through all paths and verify each path leads to the goal state. This type of procedure is a quantum tree search [107, 119]. For $n=B^m$ paths are (approximately) $\sqrt{n}$ (see Figure 7.2). A constraint of this approach is that we know the depth $m$ of the search in advance. The quantum tree search is equivalent to the iterative deepening search. The advantage can be overcome by iterative deepening search.

![](img/52faec2d621d75e53089d939bb234a82_130_0.png)

Figure 7.1 (a) Search tree for $B=2$ and $m=2$. (b) Each binary number (11, 10, 01, 00) represents a path from the root to the leaf.

![](img/52faec2d621d75e53089d939bb234a82_130_1.png)

Figure 7.2 For branching factor $B$ from 2 to 4 and the depth of the tree $m$ from 1 to 10. The cost on a conventional computer are $n = B^m$, upper plane. On a quantum computer we need $\sqrt{n} = B^{m/2}$ steps, plane below.

# Symbolic Representation — 105

Exponentially with depth, almost all time is spent in the deepest level, even though shallower levels are generated arithmetically increasing of times. The paradox can be explained using the arithmetic geometric sequence. A quantum iterative deepening search is equivalent to the iterative deepening search [108]. The total costs of $m$ iterations with $m$ measurements are

```
$O(1) + O(B) + O(B^2) + O(B^3) + \dots + O(B^m) = O(B^m); \quad\ (7.1)$
```

The time complexity of iterative deepening search has the same order of magnitude as the quantum tree search [51]. If the branching factor is not constant, the maximal branching factor $B_{max}$ must be used for the quantum tree search [107]. It turns out in the chapters 10 and 11 that this problem may be overcome elegantly.
