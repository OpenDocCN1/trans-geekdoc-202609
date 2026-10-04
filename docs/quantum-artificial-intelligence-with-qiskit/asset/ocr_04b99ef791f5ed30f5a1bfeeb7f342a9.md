# 228 Quantum Artificial Intelligence with Qiskit

```
# 3
#ang = Sqrt[0.2]/(Sqrt[0.3]); a6
#ArcCos[ang]*2
ccry = RYGate(1.23096).control(2)
qc.append(ccry,[2,1,0])
#ang = Sqrt[0.1]/(Sqrt[0.4]); a5
#ArcCos[ang]*2
ccry = RYGate(2.0944).control(2,label=None)
ccry = RYGate(2.0944).control(2)
qc.x(1)
qc.append(ccry,[2,1,0])
qc.x(1)
#ang = Sqrt[0.15]/(Sqrt[0.2]); a4
#ArcCos[ang]*2
ccry = RYGate(1.0472).control(2)
qc.append(ccry,[2,1,0])
#ang = Sqrt[0.03]/(Sqrt[0.1]); a3
#ArcCos[ang]*2
ccry = RYGate(1.98231).control(2)
qc.x(1)
qc.append(ccry,[2,1,0])
qc.x(1)
qc.x(2)
```

# 16.3 COMBINING STATES

Instead of representing the binary tree by multi-control rotation gates, we can use controlled SWAP operators with simple rotation gates [8].

# 16.3.1 Level 2

The binary tree at level two is represented by three qubits, to each qubit a rotation gate is applied. To the qubit 1 we apply the rotation $	heta_{01} = 1.98231$, to the qubit 0 we apply the rotation $	heta_{10} = 1.2745$, and to qubit 2 we apply the rotation $	heta_{00} = 1.9106$. The value of the qubit 1 controls the SWAP operation and the measured tensor product of qubit 2 represents the required distribution of the two qubits representing four states (see Figure 16.5)

# 16.3.2 Level 3

The binary tree at level three is represented by seven qubits, to each qubit a rotation gate is applied. To the qubit 3 we apply the rotation $	heta_{011} = 1.98231$, to the qubit 1 we apply the rotation $	heta_{101} = 1.2745$, and to qubit 5 we apply the rotation $	heta_{000} = 1.9106$. The value of the qubit 3 controls the SWAP operation. For the level three we apply the additional four rotations, we apply the rotation $	heta_{110} = 1.23096$ to the qubit 0, $	heta_{100} = 2.0944$ to the qubit 2, $	heta_{010} = 1.0472$ to the qubit 4, and $	heta_{001} = 1.98231$ to the qubit 6. The qubit 1 and 5 represent the level 2 control of the two subtrees. The two sub-trees are merged with the results of level one by the controlled SWAP operation by the qubit 3. The measured tensor product