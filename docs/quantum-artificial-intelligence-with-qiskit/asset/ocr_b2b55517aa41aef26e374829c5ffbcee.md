# 134 ■ Quantum Artificial Intelligence with Qiskit

| q_0 | q_1 | q_2 | q_3 | q_4 | q_5 | q_6 | q_7 | q_8 | q_9 | q_10 | q_11 | q_12 | q_13 | q_14 | q_15 | q_16 | q_17 | q_18 | q_19 | q_20 | q_21 | q_22 | q_23 | q_24 | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---||
| | 1 | | | | | | | | | | | | | | | | | | | | | | | | |
| | | 1 | | | | | | | | | | | | | | | | | | | | | | | |
| | | | 1 | | | | | | | | | | | | | | | | | | | | | | |
| | | | | 1 | | | | | | | | | | | | | | | | | | | | | |
| | | | | | 1 | | | | | | | | | | | | | | | | | | | | |
| | | | | | | 1 | | | | | | | | | | | | | | | | | | | |
| | | | | | | | 1 | | | | | | | | | | | | | | | | | | |
| | | | | | | | | 1 | | | | | | | | | | | | | | | | | |
| | | | | | | | | | 1 | | | | | | | | | | | | | | | | |
| | | | | | | | | | | 1 | | | | | | | | | | | | | | | |
| | | | | | | | | | | | 1 | | | | | | | | | | | | | | |
| | | | | | | | | | | | | 1 | | | | | | | | | | | | | |
| 1 | | | | | | | | | | | | | 1 | | | | | | | | | | | | |
| | 1 | | | | | | | | | | | | | | 1 | | | | | | | | | | |
| | | 1 | | | | | | | | | | | | | | 1 | | | | | | | | | |
| | | | 1 | | | | | | | | | | | | | |1 | | | | | | | | |
| | | | | | 1 | | | | | | | | | | | 1 | | | | | | | | |
|| | | | | | 1 | | | | | | | | | | 1 | | | | | | | | |
| | | | | | | | | 1 | | | | | | | | | 1 | | | | | | | |
| | | | | | | | | | 1 | | | | | | | | | 1 | | | | | | |
| | | | | | | | | | | 1 | | | | | | | | | 1 | | | | | | |
| | | | | | | | | | | | 1 | | | | | | | | | 1 | | | | | |
| | | | | | | | | | | | | 1 | | | | | | | | | 1 | | | | |
| 1 | | | | | | | | | | | | | | | | | | | | | | 1 | | |

Figure 9.7 The quantum circuit for the 3-puzzle task of the depth search 3. Since we are using the statevector simulator, we do not need any measurement since the simulator demonstrates the exact probabilities of each qubit. The circuits in the number of quantum gates is 13. The depth of a circuit is a metric that calculates the longest path between the data input and the output. The path descriptor has eight possible states represented by three qubits. One marked state results in a solution after one iteration in the histogram of Figure 9.8.

```
qc.h([13,18,23])
qc.name=""
return qc
```

The circuit is indicated in Figure 9.7. The statevector simulator without any measurements represents all probabilities of all qubits.

```
simulator = Aer.get_backend('statevector_simulator')
result=execute(qc,simulator).result()
counts = result.get_counts()
plot_histogram(counts)
```

The circuit's depth in the number of quantum gates is 13. The depth of a circuit is a metric that calculates the longest path between the input data and the output data. The path descriptor has eight possible states represented by three qubits. One marked state results after one iteration is indicated in the histogram of Figure 9.8. One marked state resulted after one iteration is indicated with a probability value 0.781 and the path descriptor 001. The path descriptor can be verified by measurement using the qasm simulator as well.