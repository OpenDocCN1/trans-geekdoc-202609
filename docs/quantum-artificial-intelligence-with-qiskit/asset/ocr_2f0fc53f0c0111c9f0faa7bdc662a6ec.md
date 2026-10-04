164 ■ Quantum Artificial Intelligence with Qiskit

```
qc.x(3)
qc.x(2)
qc.x(1)
qc.x(0)
```

```
qc.name="Q"
return qc
```

```
def Grover():

qc = QuantumCircuit(13)
#Diffuser(6, 7, 11, 12)

qc.h({6,7,11,12})
qc.x({6,7,11,12})
qc.h(6)
gate = MCXGate(3)
qc.append(gate, [7,11,12,6])
qc.h(6)
qc.x({6,7,11,12})
qc.h({6,7,11,12})
```

```
qc.name="G"
return qc
```

# 12.1.3 Search of Depth Two

The following listing calls the defined functions. It represents the search of depth two, including the un-computing and the Grover's amplification of the marked state, Figure 12.3.

qc = QuantumCircuit(14,4)

```
#State Preparation 0–4
qc.x(6)
qc.x(1)
qc.x(2)
qc.x(3)
qc.x(4)
#Working Memory for Flag bit 5
#1St Path descriptor 6, 7
qc.h(6)
qc.h(7)
#2th trace 8-11
#2St Path descriptor 6,11
qc.h(11)
qc.h(12)
#Auxiliary qubit 13
qc.x(13)
qc.h(13)
qc.barrier()
```