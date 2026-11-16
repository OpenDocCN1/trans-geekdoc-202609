qubits are teleported back to their origin machines. For two control qubits on different machines (from the target qubit), resources required for this would be two ebits and four classical bits for the two teleportation operations, and then another two ebits and four classical bits for teleporting the control qubits back to their origin machines, i.e. four ebits and eight classical bits.

A more efficient way is as follows also due to Eisert et al. [2000], as shown in Figure 4.5 for two control qubits, which uses four control classical bits and two ebits.

Assume that the control qubit at \(A\) is \(|c1\rangle = \alpha_1|0\rangle_{A1} + \beta_1|1\rangle_{A1}\) and at \(B\) it is \(|c2\rangle = \alpha_2|0\rangle_{B1} + \beta_2|1\rangle_{B1}\). Then, considering the qubits \(A1, A2\), and \(C1\), we start with \((\alpha_1|0\rangle_{A1} + \beta_1|1\rangle_{A1})|0\rangle_{A2}|0\rangle_{C1}\). Then, \(A2\) and \(C1\) are entangled, i.e. we have at slice 1: \((\alpha_1|0\rangle_{A1} + \beta_1|1\rangle_{A1}) \otimes (|00\rangle_{A2,C1} + |11\rangle_{A2,C1})/\sqrt{2}\). Then, at slice 2 (after the CNOT between \(A1\) and \(A2\)), we have: \((\alpha_1 |000\rangle + \alpha_1 |011\rangle + \beta_1 |110\rangle + \beta_1 |101\rangle)/\sqrt{2}\). At slice 3, after measuring the second qubit \(A2\) at \(A\) (second line):

+   1) If we get a 0, and this is sent from \(A\) to \(C\), and since it is 0, the \(X\) gate on line 5 is not applied, then, at slice 3, we have:

at slice 3 : \(\alpha_1|0\rangle_{A1}|0\rangle_{A2}|0\rangle_{C1} + \beta_1|1\rangle_{A1}|0\rangle_{A2}|1\rangle_{C1}\)

with an expression showing only the qubits on \(A\) and the first qubit at \(C\) (i.e. \(C1\)) – the other qubits are unchanged at this point from the starting point.

+   2) If a 1 is obtained instead, and this is sent from \(A\) to \(C\), and since it is 1, the \(X\) gate on line 5 is applied to qubit \(C1\), then, at slice 3, we have:

at slice 3 : \(\alpha_1|0\rangle_{A1}|1\rangle_{A2}|0\rangle_{C1} + \beta_1|1\rangle_{A1}|1\rangle_{A2}|1\rangle_{C1}\)

and the other qubits are unchanged.

Note that if we omit writing \(A2\) in both cases above, we get

at slice 3 : \(\alpha_1|0\rangle_{A1}|0\rangle_{C1} + \beta_1|1\rangle_{A1}|1\rangle_{C1}\)

that is, \(A1\) has been effectively entangled with \(C1\).

Then at, slice 6, after measuring the second qubit at \(B\) (line 4):

+   1) If we get a 0, and this is sent from \(B\) to \(C\), and since it is 0, the \(X\) gate on line 6 is not applied, then, at slice 6, we have:

at slice 6 : \(\alpha_2|0\rangle_{B1}|0\rangle_{B2}|0\rangle_{C2} + \beta_2|1\rangle_{B1}|0\rangle_{B2}|1\rangle_{C2}\)

with an expression showing only the qubits on \(B\) and the second qubit at \(C\) (i.e. \(C2\)), while the qubits at \(A\) and \(C1\) at slice 6 are as above when at slice 3 (since qubits at \(A\) and \(C1\) are not changed between slice 3 and slice 6).