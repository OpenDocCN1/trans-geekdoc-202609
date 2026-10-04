```
def rules2_inv():
qc=rules2()
qc_inv=qc.inverse()
qc_inv.name="R2_INV"
return qc_inv
```

The Grover's amplification is applied to the two qubits 13 and 16 representing the path descriptor

```
Grover():
qc = QuantumCircuit(19)
#Diffuser
qc.h([13,18))
qc.z([13,18))
qc.cz([13,18))
qc.h([13,18))
qc.name="G"
return qc
```

The quantum circuit using the defined functions is represented as

```
qc = QuantumCircuit(20,2)
#State Preparation 0-7
# Flag bit 8
#1ST Trace 9-12
#1ST Path Descriptor in superposition
qc.h(13)
#1ST Trace 14-17
#2th Path Descriptor in superposition
qc.h(18)
#Aux Bit c indicating the solution is negated and put in superposition
qc.z(19)
qc.h(19)
qc.barrier()
#Preperation of state
qc.append(state_A(),range(8))
#Depth1
qc.append(rules1(),range(14))
#Depth2
qc.append(rules2(),range(19))
#Oracle
qc.append(oracle(),range(20))
#Depth2
qc.append(rules2_inv(),range(19))
#Depth1
qc.append(rules1_inv(),range(14))
#Redo Preperation
qc.append(state_A(),range(8))
qc.barrier()
#Redo Superposition of Aux Bit
qc.h(19)
qc.barrier()
```