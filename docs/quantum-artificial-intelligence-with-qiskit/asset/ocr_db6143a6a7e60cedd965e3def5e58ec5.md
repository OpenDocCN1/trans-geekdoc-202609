# Quantum Associative Memory ■ 185

| | | | | | | | | | | | |
|---|---|---|---|---|---|---|---|---|---|---||
| q_0 | X | | | | | | | | | | |
| q_1 | | X | | | | | | | | | |
| q_2 | | | X | | | | | | | | |
| q_3 | | | | X | | | | | | | |
| q_4 | | | | | X | | | | | | |


(a)

![](bbox=[0.318, 0.233, 0.703, 0.439])

Figure 14.2 (a) Grover's amplification to the index qubits 3 and 4. (b) Since the qubits are entangled with the patterns we do not get the correct results.

```
def store():
    qc = QuantumCircuit(5)
    #First patern
    qc.ccx(3,4,0)
    qc.ccx(3,4,2)
    qc.barrier()
    #Second patern
    qc.x(3)
    qc.ccx(3,4,0)
    qc.ccx(3,4,1)
    qc.x(3)
    qc.barrier()
    #Third patern
    qc.x(4)
    qc.ccx(3,4,0)
    qc.ccx(3,4,1)
    qc.ccx(3,4,2)
    qc.x(4)
    qc.barrier()
    #Fourth patern
    qc.x(3)
    qc.x(4)
    qc.ccx(3,4,1)
    qc.x(4)
```