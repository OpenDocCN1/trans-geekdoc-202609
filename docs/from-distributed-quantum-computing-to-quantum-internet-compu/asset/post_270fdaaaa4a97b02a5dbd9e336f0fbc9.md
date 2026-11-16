
![](img/fb3eb7e935470a2da12b03f528f097ee_134_0.png)

Figure 4.3 Distributed CNOT with single control qubit (on A) for multiple target qubits (one on B and one on C).

Then, the second qubit (from the top) is measured, and

- if we get a 0, and this is sent from A to B and C, and since it is 0, the X gate is not applied at both B and C, then, at slice 3, we have:

at slice 3 : \(\sqrt{2} \cdot \left( \frac{\alpha}{\sqrt{2}} |0000\rangle + \frac{\beta}{\sqrt{2}} |1011\rangle \right) \otimes |t\rangle \otimes |s\rangle = (\alpha |0000\rangle + \beta |1011\rangle) \otimes |t\rangle \otimes |s\rangle\)

since \(\frac{1}{\sqrt{\text{prob(0) in second qubit}}} = \frac{1}{\sqrt{|\frac{\alpha}{\sqrt{2}}|^2 + |\frac{\beta}{\sqrt{2}}|^2}} = \frac{1}{\sqrt{1/2}} = \sqrt{2}\), and then applying the CNOT between the two qubits at B and at C, both locally:

at slice 4 : \(\alpha |0000\rangle |t\rangle |s\rangle + \beta |1011\rangle (X |t\rangle)(X |s\rangle)\)

and then applying gate H in the third line and fifth line (from the top):

at slice 5 : \(\alpha |00\rangle (H |0\rangle)(H |0\rangle) |t\rangle |s\rangle + \beta |10\rangle (H |1\rangle)(H |1\rangle)(X |t\rangle)(X |s\rangle)\)
\(= \frac{\alpha}{2} |0000\rangle |t\rangle |s\rangle + \frac{\alpha}{2} |0001\rangle |t\rangle |s\rangle\)
\(+ \frac{\alpha}{2} |0010\rangle |t\rangle |s\rangle + \frac{\alpha}{2} |0011\rangle |t\rangle |s\rangle\)
\(+ \frac{\beta}{2} |1000\rangle (X |t\rangle)(X |s\rangle) - \frac{\beta}{2} |1001\rangle (X |t\rangle)(X |s\rangle)\)
\(- \frac{\beta}{2} |1010\rangle (X |t\rangle)(X |s\rangle) + \frac{\beta}{2} |1011\rangle (X |t\rangle)(X |s\rangle)\)

Then, measuring the qubits at $B$ and $C$ (at third and fifth line from the top), suppose we get 0 at both $B$ and $C$, we have:

```
at slice 6 : α |0000⟩ |t⟩ |s⟩ + β |1000⟩ (X |t⟩)(X |s⟩)
= α |0⟩ |000⟩ |t⟩ |s⟩ + β |1⟩ |000⟩ (X |t⟩)(X |s⟩))
```

and both “0’s sent to $A$ which XORs (or sum modulo 2) the results to get 0 meaning that the Z gate is not applied, and so, leaving out the second, third and fourth qubits, and adding subscripts, we can write the final state as

```
α|0⟩_A|t⟩_B|s⟩_C + β|1⟩_A(X|t⟩_B)(X|s⟩_C)
```

where we observe that the control qubit at $A$ has been similarly applied to the target qubits at both $B$ and $C$. A similar reasoning can be applied for other combinations of results of measurements at $B$ and $C$, and then at slice 6, we get states as summarized in the table below.

| Measured at B | Measured at C | At slice 6 |
|---|---|---|
| 0 | 0 | α |0⟩|000⟩ |t⟩|s⟩ + β |1⟩ |000⟩ (X |t⟩)(X |s⟩) |
| 0 | 1 | α |0⟩|001⟩ |t⟩|s⟩ – β |1⟩ |001⟩ (X |t⟩)(X |s⟩) |
| 1 | 0 | α |0⟩|010⟩ |t⟩|s⟩ – β |1⟩ |010⟩ (X |t⟩)(X |s⟩) |
| 1 | 1 | α |0⟩|011⟩ |t⟩|s⟩ + β |1⟩ |011⟩ (X |t⟩)(X |s⟩) |

Note that in the cases where the measurements from B and C are “0” and “1,” and “1” and “0,” respectively, then at A, the sum (modulo 2) is 1 so that the Z gate in the first line is applied. That is, e.g. in the case of the results being “0” at B and “1” at C, the final state, after applying the Z gate (which effectively converts the “–” in front of the β to “+”) is α |0⟩|001⟩ |t⟩ |s⟩ + β |1⟩ |001⟩ (X |t⟩)(X |s⟩), and so, leaving out the second, third and fourth qubits, and adding subscripts, we get the final state: α|0⟩_A|t⟩_B|s⟩_C + β|1⟩_A(X|t⟩_B)(X|s⟩_C), which is the same result as when the measurement results are “0” at both B and C.

- if we get a 1, and this is sent from A to B and C, and since it is 1, the X gate is applied at both B and C, then, at slice 3, we have:

```
at slice 3 : (α |0100⟩ + β |1111⟩) ⊗ |t⟩ ⊗ |s⟩
```

and then applying the CNOT between the two qubits at B and C, locally:

```
at slice 4 : α |0100⟩ |t⟩ |s⟩ + β |1111⟩ (X |t⟩)(X |s⟩)
```

and then applying gate $H$ in the third line and fifth line (from the top):

```
at slice 5 : \(\alpha |01\rangle (H|0\rangle)(H|0\rangle)|t\rangle|s\rangle + \beta |11\rangle (H|1\rangle)(H|1\rangle)(X|t\rangle)(X|s\rangle)\)
\(= \frac{\alpha}{2} |0100\rangle|t\rangle|s\rangle + \frac{\alpha}{2} |0101\rangle|t\rangle|s\rangle\)
\(+ \frac{\alpha}{2} |0110\rangle|t\rangle|s\rangle + \frac{\alpha}{2} |0111\rangle|t\rangle|s\rangle\)
\(+ \frac{\beta}{2} |1100\rangle (X|t\rangle)(X|s\rangle) - \frac{\beta}{2} |1101\rangle (X|t\rangle)(X|s\rangle)\)
\(- \frac{\beta}{2} |1110\rangle (X|t\rangle)(X|s\rangle) + \frac{\beta}{2} |1111\rangle (X|t\rangle)(X|s\rangle)\)
```

Then, measuring the qubits at \(B\) and \(C\) (at third and fifth line from the top),
and depending on the outcomes, we can get the states as summarized in the
following table.

| Measured at B | Measured at C | At slice 6 |
|---|---|---|
| 0 | 0 | \(\alpha |0\rangle |100\rangle |t\rangle|s\rangle + \beta |1\rangle |100\rangle (X|t\rangle)(X|s\rangle)\) |
| 0 | 1 | \(\alpha |0\rangle |101\rangle |t\rangle|s\rangle - \beta |1\rangle |101\rangle (X|t\rangle)(X|s\rangle)\) |
| 1 | 0 | \(\alpha |0\rangle |110\rangle |t\rangle|s\rangle - \beta |1\rangle |110\rangle (X|t\rangle)(X|s\rangle)\) |
| 1 | 1 | \(\alpha |0\rangle |111\rangle |t\rangle|s\rangle + \beta |1\rangle |111\rangle (X|t\rangle)(X|s\rangle)\) |

and then applying the \(Z\) gate when required, and leaving out the second, third,
and fourth qubits, and adding subscripts for location of qubits, we get the final
state:

```
\(\alpha|0\rangle_A|t\rangle_B|s\rangle_C + \beta|1\rangle_A(X|t\rangle_B)(X|s\rangle_C)\)
```

which is the same result as case (1) above.

We point out the three qubit cat-like state at slice 3 in both cases (1) and (2)
above:

```
case (1) : (\(\alpha |\underline{000}\rangle + \beta |\underline{101}\rangle\)) \(\otimes |ts\rangle\)
case (2) : (\(\alpha |\underline{010}\rangle + \beta |\underline{111}\rangle\)) \(\otimes |ts\rangle\)
```

leaving out the second qubit, we have, in both cases, the state: (\(\alpha |000\rangle +
\beta |111\rangle\))\(|ts\rangle\), from the underlined qubits.

One can generalize further so that the control qubit is applied to target
qubits on more than two machines as follows, e.g. target qubits on three
machines: \(B\), \(C\), and \(D\), we have the circuit shown in Figure 4.4 with the
state of the form: (\(\alpha |0000\rangle + \beta |1111\rangle\))\(|tsr\rangle\) at slice 3 having the four qubit
cat-like state, leaving out the second qubit. One can draw a similar circuit for
\(n\) target qubits \(|t_i\rangle\) on \(n\) machines, which uses the \((n+1)\) qubit cat-like state:
\((\alpha|0\rangle^{\otimes(n+1)} + \beta|1\rangle^{\otimes(n+1)})\) \(|t_1\rangle \otimes \cdots \otimes |t_n\rangle\).

![](img/fb3eb7e935470a2da12b03f528f097ee_137_0.png)

Figure 4.4 Distributed CNOT with single control qubit (on A) and three target qubits (on A, B, and C).

## 4.2.2 Multiple Control Qubits for the Same Target Qubit on a Different Machine

What if we wanted to have multiple controls (with each control qubit on a different machine) on one target qubit (on a machine different from those of the control qubits)? For example, we have an operation of the following form, where there are two control qubits and all needs to be “1” before the target qubit is flipped; otherwise, the target qubit is unchanged:

![](img/fb3eb7e935470a2da12b03f528f097ee_137_1.png)

This is also called the CCNOT gate or the Toffoli gate. So, if we use the notation \wedge_1(X) to represent the CNOT gate, then the above gate is denoted as \wedge_2(X).

One way to implement this is to use teleportation. The control qubits are teleported from where they are (say, on different machines) to the machine containing the target qubit, and then the above operation is performed. And then the control qubits are teleported back to their origin machines. For two control qubits on different machines (from the target qubit), resources required for this would be two ebits and four classical bits for the two teleportation operations, and then another two ebits and four classical bits for teleporting the control qubits back to their origin machines, i.e. four ebits and eight classical bits.

A more efficient way is as follows also due to Eisert et al. [2000], as shown in Figure 4.5 for two control qubits, which uses four control classical bits and two ebits.

Assume that the control qubit at \(A\) is \(|c1\rangle = \alpha_1|0\rangle_{A1} + \beta_1|1\rangle_{A1}\) and at \(B\) it is \(|c2\rangle = \alpha_2|0\rangle_{B1} + \beta_2|1\rangle_{B1}\). Then, considering the qubits \(A1, A2\), and \(C1\), we start with \((\alpha_1|0\rangle_{A1} + \beta_1|1\rangle_{A1})|0\rangle_{A2}|0\rangle_{C1}\). Then, \(A2\) and \(C1\) are entangled, i.e. we have at slice 1: \((\alpha_1|0\rangle_{A1} + \beta_1|1\rangle_{A1}) \otimes (|00\rangle_{A2,C1} + |11\rangle_{A2,C1})/\sqrt{2}\). Then, at slice 2 (after the CNOT between \(A1\) and \(A2\)), we have: \((\alpha_1 |000\rangle + \alpha_1 |011\rangle + \beta_1 |110\rangle + \beta_1 |101\rangle)/\sqrt{2}\). At slice 3, after measuring the second qubit \(A2\) at \(A\) (second line):

- If we get a 0, and this is sent from \(A\) to \(C\), and since it is 0, the \(X\) gate on line 5 is not applied, then, at slice 3, we have:

at slice 3 : \(\alpha_1|0\rangle_{A1}|0\rangle_{A2}|0\rangle_{C1} + \beta_1|1\rangle_{A1}|0\rangle_{A2}|1\rangle_{C1}\)

with an expression showing only the qubits on \(A\) and the first qubit at \(C\) (i.e. \(C1\)) – the other qubits are unchanged at this point from the starting point.

- If a 1 is obtained instead, and this is sent from \(A\) to \(C\), and since it is 1, the \(X\) gate on line 5 is applied to qubit \(C1\), then, at slice 3, we have:

at slice 3 : \(\alpha_1|0\rangle_{A1}|1\rangle_{A2}|0\rangle_{C1} + \beta_1|1\rangle_{A1}|1\rangle_{A2}|1\rangle_{C1}\)

and the other qubits are unchanged.

Note that if we omit writing \(A2\) in both cases above, we get

at slice 3 : \(\alpha_1|0\rangle_{A1}|0\rangle_{C1} + \beta_1|1\rangle_{A1}|1\rangle_{C1}\)

that is, \(A1\) has been effectively entangled with \(C1\).

Then at slice 6, after measuring the second qubit at \(B\) (line 4):

- If we get a 0, and this is sent from \(B\) to \(C\), and since it is 0, the \(X\) gate on line 6 is not applied, then, at slice 6, we have:

at slice 6 : \(\alpha_2|0\rangle_{B1}|0\rangle_{B2}|0\rangle_{C2} + \beta_2|1\rangle_{B1}|0\rangle_{B2}|1\rangle_{C2}\)

with an expression showing only the qubits on \(B\) and the second qubit at \(C\) (i.e. \(C2\)), while the qubits at \(A\) and \(C1\) at slice 6 are as above when at slice 3 (since qubits at \(A\) and \(C1\) are not changed between slice 3 and slice 6).
