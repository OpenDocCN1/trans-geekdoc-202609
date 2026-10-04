# 3 Puzzle ■ 135

![](bbox=[0.335, 0.115, 0.662, 0.363])

**Figure 9.8** One marked state after one iteration is indicated with a probability value 0.781 and the path descriptor 001 represented by the qubits 13, 18, and 23 by the statevector simulator. All other states are zero due to un-computation. The path descriptor can be verified by measurement using the *qasm simulator* of the qubits representing the path descriptor as well.

# 9.5 SEARCH DEPTH THREE WITH TWO ITERATIONS

We apply the $U_3$-puzzle operator ignoring the trace for simplicity for the depth $t$ resulting in $2^t$ states represented by the path descriptor

$U_{3-puzzle} = ((L(t) \otimes I_i)^*) \cdot (I_t \otimes T) \cdot (L(t) \otimes I_i)^f \quad (9.10)$

With Grover amplification on $t$ qubits representing the path descriptor by the unitary operator $G_t$

$\Gamma_t := (G_t \otimes I_0) \cdot U_{3-puzzle}. \quad (9.11)$

With $r$ iterations

$\Gamma_t^r = \prod_{t=1}^{r} \Gamma_t \quad (9.12)$

and determine the solution by the measurement of the register that represents the path descriptor. In the case $t=3$ and $r=2$, with $\Gamma_t^2$ resulting in the circuit represented in the Figure 9.9.

```
qc = QuantumCircuit(25)
#State Preparation 0-7
#Working Memory for Flag bit 8
#1St Trace 9-12
#1St Descriptor in superposition
qc.h(13)
#1St Trace 14-17
```