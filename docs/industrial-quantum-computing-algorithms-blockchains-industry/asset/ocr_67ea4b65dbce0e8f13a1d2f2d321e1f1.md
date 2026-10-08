# 3.1 Fundamentals of quantum computing

Electronic data that is extremely dense can be processed more quickly, thanks to quantum computing. Computers process any binary (0s and 1s) for any logic gate sequentially. Instead of being limited to two states, quantum computers store data as quantum bits, or qubits, which may simultaneously be both 0 and 1 in a process known as superposition. Quantum computing is a subsection of quantum information systems, which are used to process information utilizing quantum mechanical processes [1]. Qubits, which are nothing more than quantum bits, are encoded using two kinds of quantum mechanical phenomena: superposition and entanglement. For the comparable idea, the qubits represent exponentially more values than their classical-bit counterparts. Compared to a traditional 0 and 1 bit, a qubit superposition indicates a greater state [1].

![](bbox=[0.196, 0.345, 0.614, 0.563])

**Figure 3.1:** Representation of classical bits and qubits [9].

# 3.1.1 Representation of qubits

The quantum mechanics state of qubits is represented using the Dirac notation, which is the matrix representation. As Figure 3.1 illustrates, the chance of collapsing to state 0 is represented by the higher value, while the possibility of collapsing to state 1 is represented by the bottom value inside each matrix (3.1):

```
0 = [1; 0]; 1 = [0; 1]  (3.1)
```

As the number of qubits increases, so does the representation of a quantum matrix. In this case, the matrix may hold $n^2$ records for every $n$ qubits.