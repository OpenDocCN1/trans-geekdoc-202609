# 140  Quantum Artificial Intelligence with Qiskit

| 7 | 8 | 6 |
| 0111 | 1000 | 0110 |
| 35 34 33 32 | 31 30 29 28 | 27 26 25 24 |
| 4 | X | 5 |
| 0100 | 1111 | 0101 |
| 23 22 21 20 | 19 18 17 16 | 15 14 13 12 |
| 1 | 2 | 3 |
| 0001 | 0010 | 0001 |
| 11 10 9 8 | 7 6 5 4 | 32 10 |

Figure 10.1 8-puzzle coding. The 9 objects are are by a register of 36 qubits. We indicate the state, its representation and below the position of the 36 qubits. In this representation, position descriptor (adjective) is fixed and the class descriptors move.

#2
#3
..

#Flag 36
#1st Trace 37-45
#1st Path Descriptor in superposition 46, 47
qc.x(46)
qc.h(47)
#Preparation of Aux
qc.x(48)
qc.h(48)

In the case the empty cell is in the center, four movements are possible. For a cell in the edge only three movements are possible, for the corner only two movements are possible

```
def if_rules():
    qc = QuantumCircuit(46)
    #Mark the trace indicate rule group through trace
    gate = MCGate(4)
    #Empty Space in corner, 2 movements
    qc.append(gate, [0, 1, 2, 3, 37])
    #Empty Space in edge, 3 movements
    qc.append(gate, [4, 5, 6, 7, 38])
    #Empty Space in corner, 2 movements
    qc.append(gate, [8, 9, 10, 11, 39])
    #Empty Space in edge, 3 movements
    qc.append(gate, [12, 13, 14, 15, 40])
    #Empty Space in center, 4 movements
    qc.append(gate, [16, 17, 18, 19, 41])
```