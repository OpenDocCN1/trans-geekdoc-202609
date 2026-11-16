following quantum circuit C to be computed using nodes QC2 and QC3 connected as in Figure 6.4 via an intermediate node (call this QCM):

```
$C \left\{ \begin{matrix} q_2 & \bullet & \bullet & \bullet \\ q_3 & \oplus & \oplus & \oplus \end{matrix} \right.$
```

where q_i is located on QC i so that the three CNOT gates are actually distributed-CNOT operations. For each distributed-CNOT to be performed separately, an entangled pair involving (communication) qubits on the two nodes is needed as in Figure 4.2, here depicted as in Figure 6.5.

We can consider the resource requirements, e.g. in terms of the number of entangled pairs required, and time (i.e. the number of steps required to execute the circuit). One way to execute the quantum circuit is to perform each of the three distributed-CNOT gates separately. Now for each distributed-CNOT gate, an entangled pair is required – what resources are required for this? Assuming that an entangled pair is generated between QC2 and QCM and another entangled pair generated between QCM and QC3 (call these neighbor entanglement links). Then, an entanglement swapping operation is performed to get the entangled pair between QC2 and QC3, i.e. for each distributed-CNOT gate, 2 neighbor entanglement links are consumed, and suppose s steps of a quantum circuit are required for this, and then another d steps are required for the circuit in Figure 6.5, i.e. a total of (s + d) steps are required for each distributed-CNOT gate between q2 and q3. For the quantum circuit C above with three distributed-CNOT operations, 6 neighbor entanglement links are consumed, and 3(s + d) steps are required. In general, suppose there are n distributed CNOTs to perform in a row instead of just 3, then 2n neighbor entanglement links are consumed and n(s + d) steps are required.

Is there a way to reduce resources required? Indeed, there is, given that the control qubit is actually used three times without change in the circuit. One way

![](bbox=[0.13, 0.69, 0.83, 0.835])

Figure 6.5 A circuit implementing a distributed-CNOT between qubits q2 and q3 across nodes QC2 and QC3. The communication qubits sharing an entangled pair are marked comm, and the two data qubits are marked data.