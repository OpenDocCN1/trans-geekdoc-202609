query vector, in our example x_q = (1, 0, 0, 1, 1, 0, 1). We apply controlled phase operation with N = 4 with count_j \le 4, see Figure 15.17, and the qiskit definition of the circuit

```
qc = QuantumCircuit(23)
#0-3 query
#4-4 data aggregated
#8-11 data
#12-19 count
#Index Pointer
#20-21
#Aux
#22

#Sleep Phase
#Index Pointer
qc.h(20)
qc.h(21)
#1st weights
#OR Aggregated
qc.barrier()
qc.ccx(20,21,4)
qc.ccx(20,21,7)
#Original
qc.barrier()
qc.ccx(20,21,8)
qc.ccx(20,21,11)
#2th weights
qc.x(20)
#OR Aggregated
qc.barrier()
qc.ccx(20,21,4)
qc.ccx(20,21,7)
#Original
qc.barrier()
qc.ccx(20,21,8)
qc.x(20)
#3th weights
qc.x(21)
#OR Aggregated
qc.barrier()
qc.ccx(20,21,4)
qc.ccx(20,21,6)
qc.ccx(20,21,7)
#Original
qc.barrier()
qc.ccx(20,21,10)
qc.x(21)
#4th weights
qc.x(20)
qc.x(21)
```