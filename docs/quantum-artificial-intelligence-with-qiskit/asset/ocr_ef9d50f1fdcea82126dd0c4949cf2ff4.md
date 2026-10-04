![](bbox=[0.31, 0.11, 0.66, 0.42])

**Figure 15.14** Teen superposition states not equal to zero. The qubits 24, 25, and 26 are the index qubits. Note that the units are counted in the reverse order by the index qubits: 111 first unit, 110 for the second unit, till 000 being the eighth unit. The measured value for the control qubit 27 equal one indicates the firing of the units. The measured value is just 0.5. This happens since the weight matrix is relatively small and not homogeneously filled. For the query vector $x_q = (1, 1, 0, 0, 0, 0, 0, 0)$, the three values 0.125 indicate the answer vector $(1, 1, 0, 0, 0, 0, 1, 0)$ by the index qubits 24, 25, and 26: for the first unit with the value (111), the second unit (110), and seventh unit (001). The control qubit 27 equal to zero indicates the units that do not fire.

```
gate = MCXGate(3)
```

```
#1st weights
qc.append(gate, [24, 25, 26, 8])
qc.append(gate, [24, 25, 26, 9])
qc.append(gate, [24, 25, 26, 14])

#2nd weights
qc.x(24)
qc.append(gate, [24, 25, 26, 8])
qc.append(gate, [24, 25, 26, 9])
qc.append(gate, [24, 25, 26, 11])
qc.append(gate, [24, 25, 26, 12])
qc.append(gate, [24, 25, 26, 14])
```