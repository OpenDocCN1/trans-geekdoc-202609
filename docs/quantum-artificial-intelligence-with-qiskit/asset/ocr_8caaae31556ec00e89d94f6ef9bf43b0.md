# Quantum Associative Memory

Quantum associative memory (QuAM) in the domain of quantum computation is a model with a capacity exponential in the number of neurons. Quantum Nearest Neighbor (QNN) is related to the QuAM. In QNN the binary patterns are stored by entanglement with Grover's amplification to the index qubits, we have to un-compute the entanglement of index qubits with the patterns. In QNN we need to un-compute. However, in QuAM we do not uncompute. In QuAM as proposed by Venture and Martinez, a modified version of Grover's search algorithm is applied to determine the answer vector to a query vector instead of computing one can apply Grover's algorithm to all qubits. Most quantum machine learning algorithms including quantum associative memory suffer from the input destruction problem where the classical data must be read and after the measurement superposition collapses. However, the input destruction problem is not solved today, and usually theoretical speed ups are analyzed. We will demonstrate a simple QNN model, and a modified version of Grover's search algorithm as proposed by Venture and Martinez. Then we analyze the input destruction problem.

# 14.1 QUANTUM NEAREST NEIGHBOR

We store in binary patterns,

```
|101⟩4 · |011⟩3, |111⟩2, |010⟩1
```

by entanglement with the four index qubits |indexj⟩ in superposition

```
|index4⟩ = |11⟩ |index3⟩ = |10⟩ |index2⟩ = |01⟩ |index1⟩ = |00⟩
```

The four patterns with their indices represented in a uniform distribution of the states

```
|ψ⟩ = ½(|00010⟩1 + |011111⟩2 + |11101⟩4).
```

We represent the patterns by the qubits 0, 1, and 2 and the index by the qubits 3 and 4. The qubit 5 represents the auxiliary qubit for the Grover's amplification (see

DOI: 10.1201/9781003374404-14