
And letting $f_1 = (|0\rangle |++\rangle + |1\rangle |--\rangle)^{\otimes 2}$ and $f_2 = (|0\rangle |++\rangle - |1\rangle |--\rangle)^{\otimes 2}$, we have the above equal to:

(H \otimes I^{\otimes 7}) CNOT_{ms} (\alpha |0\rangle + \beta |1\rangle)_m \otimes \left( \frac{1}{2\sqrt{2}} |0\rangle_s \otimes f_1 + \frac{1}{2\sqrt{2}} |1\rangle_s \otimes f_2 \right)
= (H \otimes I^{\otimes 7}) CNOT_{ms} \left[ \frac{\alpha}{2\sqrt{2}} |00\rangle_{ms} \otimes f_1 + \frac{\alpha}{2\sqrt{2}} |01\rangle_{ms} \otimes f_2 + \frac{\beta}{2\sqrt{2}} |10\rangle_{ms} \otimes f_1 + \frac{\beta}{2\sqrt{2}} |11\rangle_{ms} \otimes f_2 \right]
= (H \otimes I^{\otimes 7}) \left[ \frac{\alpha}{2\sqrt{2}} |00\rangle_{ms} \otimes f_1 + \frac{\alpha}{2\sqrt{2}} |01\rangle_{ms} \otimes f_2 + \frac{\beta}{2\sqrt{2}} |11\rangle_{ms} \otimes f_1 + \frac{\beta}{2\sqrt{2}} |10\rangle_{ms} \otimes f_2 \right]
= \frac{\alpha}{4} (|00\rangle + |10\rangle)_{ms} \otimes f_1 + \frac{\alpha}{4} (|01\rangle + |11\rangle)_{ms} \otimes f_2 + \frac{\beta}{4} (|01\rangle - |11\rangle)_{ms} \otimes f_1 + \frac{\beta}{4} (|00\rangle - |10\rangle)_{ms} \otimes f_2
= |00\rangle_{ms} \otimes \left( \frac{\alpha}{4} f_1 + \frac{\beta}{4} f_2 \right) + |01\rangle_{ms} \otimes \left( \frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2 \right) + |10\rangle_{ms} \otimes \left( \frac{\alpha}{4} f_1 - \frac{\beta}{4} f_2 \right) + |11\rangle_{ms} \otimes \left( -\frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2 \right)

where we get $\frac{\alpha}{4} f_1 + \frac{\beta}{4} f_2, \frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2, \frac{\alpha}{4} f_1 - \frac{\beta}{4} f_2$ or $-\frac{\beta}{4} f_1 + \frac{\alpha}{4} f_2$ (with equal probability, i.e. 1/4) depending on the outcome of the measurement, i.e. when we measure the qubits m and s with respect to the computational basis. Suppose the measurement yielded $|00\rangle_{ms}$, then we transmit the 6-qubit cluster state:

$|r'\rangle = \frac{\frac{\alpha}{4} f_1 + \frac{\beta}{4} f_2}{\sqrt{1/4}} = \frac{\alpha}{2} f_1 + \frac{\beta}{2} f_2$, which is

$\frac{\alpha}{2} (|0\rangle |++\rangle + |1\rangle |--\rangle) \otimes (|0\rangle |++\rangle + |1\rangle |--\rangle)
+ \frac{\beta}{2} (|0\rangle |++\rangle - |1\rangle |--\rangle) \otimes (|0\rangle |++\rangle - |1\rangle |--\rangle)$

containing the quantum information to be transmitted (i.e. the amplitudes $\alpha$ and $\beta$). How is this more robust to transmission losses? From the example in Borregaard et al. [2020], suppose some of the qubits are lost during the transmission, say the first two qubits, we will then be left with either:

(i) $\frac{\alpha}{\sqrt{2}} |+\rangle \otimes (|0\rangle |++\rangle + |1\rangle |--\rangle) + \frac{\beta}{\sqrt{2}} |+\rangle \otimes (|0\rangle |++\rangle - |1\rangle |--\rangle)$

or

(ii) $\frac{\alpha}{\sqrt{2}} |-\rangle \otimes (|0\rangle |++\rangle + |1\rangle |--\rangle) - \frac{\beta}{\sqrt{2}} |-\rangle \otimes (|0\rangle |++\rangle - |1\rangle |--\rangle)$

with equal probability, since it is like measuring out the first two qubits. Then, we can measure (in the X basis) the first qubit above to get $|+\rangle$ or $|-\rangle$, i.e. one of the two cases. Suppose we get the resulting state in case (i), which we denote by $|(i)\rangle$:

$|(i)\rangle = \frac{\alpha}{\sqrt{2}}(|0\rangle |++\rangle + |1\rangle |--\rangle) + \frac{\beta}{\sqrt{2}}(|0\rangle |++\rangle - |1\rangle |--\rangle)$
$= \frac{\alpha+\beta}{\sqrt{2}} |0\rangle |++\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle |--\rangle$
$= \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle (|00\rangle + |01\rangle + |10\rangle + |11\rangle) + \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle (|00\rangle - |01\rangle - |10\rangle + |11\rangle)$
(recalling that $|+\rangle = (|0\rangle + |1\rangle)/\sqrt{2}$ and $|-\rangle = (|0\rangle - |1\rangle)/\sqrt{2}$)
$= \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |00\rangle + \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |01\rangle$
$+ \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |10\rangle + \left( \frac{\alpha+\beta}{2\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{2\sqrt{2}} |1\rangle \right) |11\rangle$

Then, upon measuring the last two qubits in the Z basis, we get with probability 1/4 one of the following: $|00\rangle$, $|01\rangle$, $|10\rangle$, or $|11\rangle$. Suppose we get $|00\rangle$, then we obtain:

$\frac{(I \otimes |0\rangle \langle 0| \otimes |0\rangle \langle 0|) |(i)\rangle}{\sqrt{1/4}} = \left( \frac{\alpha+\beta}{\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle \right) \otimes |00\rangle$

Noting that $\frac{\alpha+\beta}{\sqrt{2}} |0\rangle + \frac{\alpha-\beta}{\sqrt{2}} |1\rangle = \alpha |+\rangle + \beta |-\rangle$, by applying the Hadamard (\(H\)) gate to \(\alpha |+\rangle + \beta |-\rangle\), we obtain the message qubit \(\alpha |0\rangle + \beta |1\rangle\). If we get \(|01\rangle\), we obtain \(\frac{\alpha+\beta}{\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{\sqrt{2}} |1\rangle\), which can be rewritten:

$\frac{\alpha+\beta}{\sqrt{2}} |0\rangle - \frac{\alpha-\beta}{\sqrt{2}} |1\rangle = Z(\alpha |+\rangle + \beta |-\rangle)$

By applying HZ to \(Z(\alpha |+\rangle + \beta |-\rangle)\), we can then obtain \(\alpha |0\rangle + \beta |1\rangle\), and similarly, with \(|10\rangle\) and \(|11\rangle\). A similar reasoning with case (ii).

To get (i), for example, we compute $\frac{\langle 0|\langle 0|\langle +| + \langle +| \otimes \langle +| \otimes \langle +| |-\rangle}{\sqrt{1/2}}$ and leave out writing the measured qubits $|0\rangle |+\rangle$. Similarly, if measuring the first two qubits yields $|1\rangle |-\rangle$.

Hence, we see that losing two (or fewer) out of the six qubits (in the tree-cluster state) is fine as the quantum state of the message can still be recovered. (A larger tree-cluster state can be used to provide greater robustness.)

The above scheme is a process for recovering the message qubit. The method is basically as follows:

- 1. Measure out all the qubits in one branch (either one): measure the first-level qubit in the Z basis and second-level qubits in the X basis. (Note that in the example above, the two lost qubits are as though they have been “measured out” and then we measure one more second-level qubit (in that branch where the two qubits were lost) in the X basis, i.e. we measured out all the qubits in one branch.)

- 2. In the remaining branch, measure the two second-level qubits in the Z basis and perform some H and/or Pauli operations as required.

Once recovered, at a repeater, the qubit can be re-encoded in a similar way with a (new) tree-cluster state and transmitted to the next repeater (or destination).

However, we might want to first “test” to see if there is photon (qubit) loss or not, i.e. if the encoded message qubit arrived successfully or not, before proceeding to re-encoding with a new tree-cluster state. This is done as follows. Suppose the qubits received at this repeater is \(|\tau'\rangle = \frac{\alpha}{2}f_1 + \frac{\beta}{2}f_2\), i.e.

$|\tau'\rangle = \frac{\alpha}{2}(|0\rangle_{c1}|++\rangle + |1\rangle_{c1}|--\rangle) \otimes (|0\rangle_{c2}|++\rangle + |1\rangle_{c2}|--\rangle)$
$+ \frac{\beta}{2}(|0\rangle_{c1}|+-\rangle - |1\rangle_{c1}|--\rangle) \otimes (|0\rangle_{c2}|++\rangle - |1\rangle_{c2}|--\rangle)$

where we highlight the first-level qubits (recalling the tree-cluster idea where the first level qubits are marked as c1 and c2 here). The controlled-Z gate (CZ) operation is done with one of the first-level qubits in the transmitted state (say c1) and an auxiliary stationary qubit s in the state \(H|0\rangle\) and a measurement in the X basis is done. If the X basis measurement was successful, then a transfer to the new cluster state is heralded, and a Bell measurement is done between the auxiliary qubit and the root of a new tree-cluster state, transferring the quantum information to the new tree-cluster state. The circuit (showing only qubits c1 and s) is as follows:

![](img/fb3eb7e935470a2da12b03f528f097ee_183_0.png)
