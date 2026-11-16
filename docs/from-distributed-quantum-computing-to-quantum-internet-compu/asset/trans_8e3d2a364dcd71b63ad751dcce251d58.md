

adjust its keys when it wants to do a test run (while the server also does not need to do anything, like in the computation run).

## 5.2.2 Z 门小器件

We saw earlier how the client can get the server to do a Z gate on an encrypted qubit. Similar to the X gate, the server can do nothing (or send back the original encrypted qubit unchanged) and the client just adjusts its keys, this time to \(a' = a\) and \(b' = b \oplus 1\) so that we have:

```
\(Z^{b'} X^{a'} X^a Z^b |\psi\rangle = Z^{b \oplus 1} X^a X^a Z^b |\psi\rangle = Z Z^b Z^b |\psi\rangle = Z |\psi\rangle\)
```

As in the case of the X-gate, the client adjusts its keys only in a computation run. Since it intends to compute the identity operation in the X-test and Z-test runs, the client does not adjust its keys (while the server also does not need to do anything, like in the computation run).

## 5.2.3 CNOT 门小器件

In the case of the client wanting the server to perform the CNOT gate, the approach for the computation run is as in Table 5.1: applying a CNOT gate on qubits \(i\) and \(j\), where \(i\) is the control and \(j\) is the target, suppose qubit \(i\) has key \((a_i, b_i)\) and qubit \(j\) has key \((a_j, b_j)\), then, the server performs the CNOT between these two qubits, and the client adjusts the keys as follows to have the new keys \((a'_i, b'_i)\) and \((a'_j, b'_j)\): \(a'_i = a_i\), \(b'_i = b_i \oplus b_j\), and \(a'_j = a_i \oplus a_j\), \(b'_j = b_j\). In either a X-test and Z-test run, the server still does the CNOT, but the client does not adjust its keys since CNOT(\(|0\rangle|0\rangle\)) = \(|0\rangle|0\rangle\) and CNOT(\(|+\rangle|+\rangle\)) = \(|+\rangle|+\rangle\).

## 5.2.4 R 门小器件

Let us look at the way the R operation is carried out, i.e. the R gate “gadget,” as given in Figure 5.2.

Compared to the previous R gadget in Figure 5.1, here, the R gate is “done” on the client side. In fact, similar to Section 5.1, for this gadget, the client does not need to be able to actually perform these gate operations on arbitrary quantum states, but just be able to prepare a state chosen randomly and uniformly from one of the following states, here specified in terms of results of operations: {R\(|+\rangle\), R\(|-\rangle\), PR\(|+\rangle\), PR\(|-\rangle\)} (similar to Assumption 1 earlier); this is equivalent to the client choosing randomly and uniformly \(d, e, y \in \{0, 1\}\) and computing \(X^d Z^e P^y R|+\rangle\) since:

![](img/fb3eb7e935470a2da12b03f528f097ee_166_0.png)

Figure 5.2 A slightly modified protocol for an R-gate for a computation run, where the output from the server is \(|\phi\rangle = X^{c \oplus d} Z^{(a \oplus c) \cdot (d \oplus y) \oplus b \oplus c \oplus e \oplus y} R |\psi\rangle\). The client chooses randomly and uniformly \(d, e, y \in \{0, 1\}\). This can be called an R-gate “gadget.”

| d | e | y | \(X^d Z^e P^y R |+\rangle\) |
|---|---|---|---|
| 0 | 0 | 0 | \(R |+\rangle\) |
| 0 | 0 | 1 | \(PR |+\rangle\) |
| 0 | 1 | 0 | \(ZR |+\rangle = RZ |+\rangle = R |-\rangle\) |
| 0 | 1 | 1 | \(ZPR |+\rangle = PZR |+\rangle = PRZ |+\rangle = PR |-\rangle\) |
| 1 | 0 | 0 | \(XR |+\rangle \equiv ZPRX |+\rangle = ZPR |+\rangle = PZR |+\rangle = PRZ |+\rangle = PR |-\rangle\) |
| 1 | 0 | 1 | \(XPR |+\rangle \equiv ZXPR |+\rangle \equiv ZP ZPRX |+\rangle = ZPZPR |+\rangle = R |-\rangle\) |
| 1 | 1 | 0 | \(XZR |+\rangle = -ZXR |+\rangle \equiv -ZZPRX |+\rangle = -PR |+\rangle \equiv PR |+\rangle\) |
| 1 | 1 | 1 | \(XZPR |+\rangle \equiv RX |+\rangle = R |+\rangle\) |

where in the above, we are using the identities: \(XZ = -ZX, PZ = ZP, ZR = RZ, RX \equiv XZPR, XR \equiv ZPRX, PR = RP, XP \equiv ZPX, X|+\rangle = |+\rangle, Z|+\rangle = |-\rangle\), and \(P^2 = Z\), where the equivalences are due to ignoring global phases.

The circuit in Figure 5.2 can be derived as follows, similar to how we derived the R-gate gadget in Section 5.1.

- 1) Let’s start with the following circuit, similar to the one in step (3) of the previous derivation for Figure 5.1, but with the additional \(R\) gate before the \(P^y\) gate in the bottom wire and input being \(X^a Z^b |\psi\rangle\), so that the output becomes \(Z^e P^y R X^c X^a Z^b |\psi\rangle\):

![](img/fb3eb7e935470a2da12b03f528f097ee_166_1.png)

One can check as we have done for step (3) in the previous derivation that the output is Z^x P^y RX^c X^a Z^b |ψ⟩.

- 2) Then, we add the X^d gate after the control in the bottom wire, so that the output becomes X^d Z^e P^y RX^c X^a Z^b |ψ⟩:

   X^a Z^b |ψ⟩─────────●──meter── c
             │
   |+⟩──R──P^y──Z^e──┬──X^d── X^d Z^e P^y RX^c X^a Z^b |ψ⟩

- 3) Then, we add the gate P^x = P^{a \oplus c \oplus y} after the X^d gate to the bottom wire as follows, so that the output becomes |φ⟩ = P^{a \oplus c \oplus y} X^d Z^e P^y RX^c X^a Z^b |ψ⟩:

   X^a Z^b |ψ⟩─────────●──meter── c
             │
   |+⟩──R──P^y──Z^e──┬──X^d──P^{a \oplus c \oplus y}──|φ⟩

Now, we rephrase the output:

P^x X^d Z^e P^y RX^c X^a Z^b |ψ⟩ = P^{a \oplus c \oplus y} X^d Z^e P^y RX^{a \oplus c} Z^b |ψ⟩
(since x = a \oplus c \oplus y)
\equiv P^{a \oplus c \oplus y} X^d Z^e P^y X^{a \oplus c} Z^{a \oplus c} P^{a \oplus c} R Z^b |ψ⟩
(since RX^{a \oplus c} \equiv X^{a \oplus c} Z^{a \oplus c} P^{a \oplus c} R, ignoring the global phase)
= P^{a \oplus c \oplus y} X^d Z^e P^y X^{a \oplus c} P^{a \oplus c} Z^{a \oplus c} Z^b R |ψ⟩
(using PZ = ZP, ZR = RZ)
\equiv P^{a \oplus c \oplus y} X^d Z^e P^y Z^{a \oplus c} P^{a \oplus c} X^{a \oplus c} Z^{a \oplus c} Z^b R |ψ⟩
(using XP \equiv ZPX, and ignoring the global phase)
= -P^{a \oplus c \oplus y} X^d Z^e P^y P^{a \oplus c} X^{a \oplus c} Z^b R |ψ⟩
(using PZ = ZP, -ZX = XZ and Z^{a \oplus c} Z^{a \oplus c} = I)
= -P^{a \oplus c \oplus y} P^d P^y Z^e P^{a \oplus c} X^{a \oplus c} Z^b R |ψ⟩
(using PZ = ZP)
\equiv -P^{a \oplus c \oplus y} P^{d+y} P^x Z^d P^{a \oplus c} X^{a \oplus c} Z^b R |ψ⟩
(using X^d P^y \equiv Z^{d.y} P^y X^d, ignoring the global phase)
= P^{a \oplus c \oplus y} Z^{d.y} P^y Z^d X^d P^{a \oplus c} X^{a \oplus c} Z^b R |ψ⟩
(using XZ = -ZX)
\equiv P^{a \oplus c \oplus y} Z^{d.y} P^y P^y Z^d P^{d(a \oplus c)} P^{a \oplus c} X^d X^{a \oplus c} Z^b R |ψ⟩
(using X^d P^{a \oplus c} \equiv Z^{d(a \oplus c)} P^{a \oplus c} X^d , ignoring the global phase)

= P^(a⊕c)⊕y P^y P^(a⊕c) Z^d y⊕e⊕d·(a⊕c) X^d X^(a⊕c) Z^b R |ψ⟩
(using PZ = ZP)
= Z^y·(a⊕c) P^(a⊕c) P^y P^y P^a Z^c y⊕e⊕d·(a⊕c) X^d X^(a⊕c) Z^b R |ψ⟩
(using Z^y·(a⊕c) P^(a⊕c) P^y = P^(a⊕c⊕y) )
= X^d X^(a⊕c) Z^y·(a⊕c) Z^(a⊕c⊕y) Z^d y⊕e⊕d·(a⊕c) Z^b R |ψ⟩
(using P^y P^y = Z^y, P^(a⊕c) P^(a⊕c) = Z^(a⊕c) and ZX = -XZ)
= X^(a⊕c⊕d) Z^(y·(a⊕c)⊕a⊕c⊕y) d·y⊕e⊕d·(a⊕c) ⊕b R |ψ⟩
= X^(a⊕c⊕d) Z^(y·(a⊕c)⊕a⊕c⊕y) d·y⊕e⊕d·(a⊕c) ⊕b·d⊕d⊕d R |ψ⟩
(since d · d ⊕ d = d ⊕ d = 0)
= X^(a⊕c⊕d) Z^((a⊕c⊕d)·(d⊕y)⊕a⊕b⊕c⊕d⊕e⊕y) R |ψ⟩
= X^(a⊕c') Z^((a⊕c')·(d⊕y)⊕a⊕b⊕c'⊕e⊕y) R |ψ⟩
(where we let c' = c ⊕ d)

- 4) Then, we make use of the following equivalence about the CNOT and X gates:

![](img/fb3eb7e935470a2da12b03f528f097ee_168_0.png)

so that if we add an X-gate after the target to the top wire, we have:

![](img/fb3eb7e935470a2da12b03f528f097ee_168_1.png)

And so, the circuit from step (3) can be equivalently drawn as follows:

![](img/fb3eb7e935470a2da12b03f528f097ee_168_2.png)

where |φ⟩ = X^(a⊕c') Z^(a⊕c')·(d⊕y)⊕a⊕b⊕c'⊕e⊕y R |ψ⟩ with c' = c ⊕ d, from the calculations above.

- 5) Finally, we observe that for any qubit α|0⟩ + β|1⟩ emerging after the target in the top wire, since X^d(α|0⟩ + β|1⟩) = α|0⊕d⟩ + β|1⊕d⟩, applying X^d to the qubit and then measuring will return the result c (where c = 0 ⊕ d or c = 1 ⊕ d), but if c' = c ⊕ d, then the equivalent circuit is as follows:

![](img/fb3eb7e935470a2da12b03f528f097ee_169_0.png)

Figure 5.3 The R-gate gadget in an X-test run. Note that the client randomly and uniformly chooses \(x, d \in \{0, 1\}\), the server does the same operations as in a computation run (compare with Figure 5.2), and note that operations on the client is such that the identity operation is carried out (the identity operation is up to encryption, i.e. as long as the client keeps track of the key, in this case, after this gadget, the key has changed from \(a\) to \(d\); the client can apply \(X^d\) to get back \(|0\rangle\)). Also, there is a test - after receiving \(c\) from the server, the client verifies that \(c = a \oplus d\).

![](img/fb3eb7e935470a2da12b03f528f097ee_169_1.png)

which is the circuit in Figure 5.2.

In the X-test run and the Z-test run, different R-gate gadgets are used.

Figure 5.3 shows the R gate used in the X-test run. Note that the gadget has a test to check that the server's output \(c\) satisfies \(c = a \oplus d\). This is because the state after the target and before measurement in the top wire is \(X^{a \oplus d} |0\rangle\), which upon measurement should provide \(c = a \oplus d\) if the server has been doing the right thing, and noting that the output from the bottom wire would be \(P^x X^d |0\rangle \equiv X^d |0\rangle\) (ignoring the global phase).

Figure 5.4 shows the R gate used in the Z-test run. The output \(X^c Z^{b \oplus d \oplus y} |+\rangle\) is obtained as shown via calculations. From the circuit, (similar to the idea in step (3) of the derivation for Figure 5.1) the output is

```
\(P^x Z^d P^y X^c Z^b |+\rangle = P^x P^y Z^d X^c Z^b |+\rangle = Z^y Z^d X^c Z^b |+\rangle = X^c Z^{b \oplus d \oplus y} |+\rangle\)
(since \(x=y\), \(ZP = PZ\), and \(P^x P^y = Z^y\))
```

## 5.2.5 H 门小器件

The H gate is what makes the Z-test run needed since it changes \(|0\rangle\) to \(|+\rangle\). There are some difficulties here if the H gate is simply applied by the server like we did in Section 5.1, see Table 5.1 since, this time, we don't have just computation

