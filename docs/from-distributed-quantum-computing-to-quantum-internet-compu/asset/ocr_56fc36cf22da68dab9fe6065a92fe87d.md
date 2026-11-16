adjust its keys when it wants to do a test run (while the server also does not need to do anything, like in the computation run).

# 5.2.2 Z Gate Gadget

We saw earlier how the client can get the server to do a Z gate on an encrypted qubit. Similar to the X gate, the server can do nothing (or send back the original encrypted qubit unchanged) and the client just adjusts its keys, this time to \(a' = a\) and \(b' = b \oplus 1\) so that we have:

```
\(Z^{b'} X^{a'} X^a Z^b |\psi\rangle = Z^{b \oplus 1} X^a X^a Z^b |\psi\rangle = Z Z^b Z^b |\psi\rangle = Z |\psi\rangle\)
```

As in the case of the X-gate, the client adjusts its keys only in a computation run. Since it intends to compute the identity operation in the X-test and Z-test runs, the client does not adjust its keys (while the server also does not need to do anything, like in the computation run).

# 5.2.3 CNOT Gate Gadget

In the case of the client wanting the server to perform the CNOT gate, the approach for the computation run is as in Table 5.1: applying a CNOT gate on qubits \(i\) and \(j\), where \(i\) is the control and \(j\) is the target, suppose qubit \(i\) has key \((a_i, b_i)\) and qubit \(j\) has key \((a_j, b_j)\), then, the server performs the CNOT between these two qubits, and the client adjusts the keys as follows to have the new keys \((a'_i, b'_i)\) and \((a'_j, b'_j)\): \(a'_i = a_i\), \(b'_i = b_i \oplus b_j\), and \(a'_j = a_i \oplus a_j\), \(b'_j = b_j\). In either a X-test and Z-test run, the server still does the CNOT, but the client does not adjust its keys since CNOT(\(|0\rangle|0\rangle\)) = \(|0\rangle|0\rangle\) and CNOT(\(|+\rangle|+\rangle\)) = \(|+\rangle|+\rangle\).

# 5.2.4 R Gate Gadget

Let us look at the way the R operation is carried out, i.e. the R gate “gadget,” as given in Figure 5.2.

Compared to the previous R gadget in Figure 5.1, here, the R gate is “done” on the client side. In fact, similar to Section 5.1, for this gadget, the client does not need to be able to actually perform these gate operations on arbitrary quantum states, but just be able to prepare a state chosen randomly and uniformly from one of the following states, here specified in terms of results of operations: {R\(|+\rangle\), R\(|-\rangle\), PR\(|+\rangle\), PR\(|-\rangle\)} (similar to Assumption 1 earlier); this is equivalent to the client choosing randomly and uniformly \(d, e, y \in \{0, 1\}\) and computing \(X^d Z^e P^y R|+\rangle\) since: