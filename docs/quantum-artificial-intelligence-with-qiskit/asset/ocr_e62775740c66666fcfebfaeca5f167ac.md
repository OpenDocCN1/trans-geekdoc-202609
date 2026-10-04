![](bbox=[0.313, 0.118, 0.653, 0.375])

**Figure 15.1** Five superposition states not equal to zero. The control qubit 14 equal indicates the firing of the units. The measured value is 0.625. The two probabilities 0.25 express the perfect match and the solution (1,0,0,1), indicated by the index qubits 12 and 13, with the values (11) for the first unit and (00) for the fourth unit. Note that the units are counted in reverse order by the index qubits (11) first unit, (10) for the second unit, (01) for the third unit, and (00) for the fourth unit. The control qubit 14 equal to zero indicates the units that do not fire. The measured value is 0.375. The probability 0.25 with the index qubits 12 and 13, with the value (01) for the third unit indicates the most dissimilar pattern (0,0,1,0).

#  15.4.1 Generalization

We generalize the description of $n$ units. After the entanglement of index qubits in superposition with the weight vectors following the state is, the state $count_j$ and $unit_j$ are represented by $[111]$, $[112]$,

```
$$\frac{1}{\sqrt{n}} \left( \sum_{j=1}^{n} |index_j\rangle |unit_j\rangle \right) \otimes |query\rangle. \quad (15.18)$
```

with the cost $O(n^2)$. We apply to the control qubit (ignoring the index qubits)

```
$$\frac{1}{\sqrt{2}} (|0\rangle + |1\rangle) \otimes \left( \sum_{j=1}^{n} |count_j\rangle |unit_j\rangle \right) \otimes |query\rangle = $$
$$\frac{1}{\sqrt{2} \cdot n} \cdot |0\rangle \left( \sum_{j=1}^{n} |count_j\rangle |unit_j\rangle \right) \otimes |query\rangle + $$
$$\frac{1}{\sqrt{2} \cdot n} \cdot |1\rangle \left( \sum_{j=1}^{n} |count_j\rangle |unit_j\rangle \right) \otimes |query\rangle. \quad (15.19)$
```