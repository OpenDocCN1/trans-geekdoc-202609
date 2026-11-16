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

+   2) and if we get a 1, and this is sent from A to B and C, and since it is 1, the X gate is applied at both B and C, then, at slice 3, we have:

```
at slice 3 : (α |0100⟩ + β |1111⟩) ⊗ |t⟩ ⊗ |s⟩
```

and then applying the CNOT between the two qubits at B and C, locally:

```
at slice 4 : α |0100⟩ |t⟩ |s⟩ + β |1111⟩ (X |t⟩)(X |s⟩)
```