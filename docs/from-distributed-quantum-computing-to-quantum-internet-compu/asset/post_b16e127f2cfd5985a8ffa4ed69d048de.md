

## Table 5.1 Table summarizing the protocol for computing with encrypted data for different gates for each qubit (single qubit gates) or each pair of qubits (for the CNOT).

| From client | U on server | Computed on server | Keys for dec |
| :--- | :--- | :--- | :--- |
| $X^a Z^b |\psi\rangle$ | X | $X(X^a Z^b |\psi\rangle) \equiv X^a Z^b (X |\psi\rangle)$ | $a'=a, b'=b$ |
| $X^a Z^b |\psi\rangle$ | Z | $Z(X^a Z^b |\psi\rangle) \equiv X^a Z^b (Z |\psi\rangle)$ | $a'=a, b'=b$ |
| $X^a Z^b |\psi\rangle$ | H | $H(X^a Z^b |\psi\rangle) \equiv X^b Z^a (H |\psi\rangle)$ | $a'=b, b'=a$ |
| $X^a Z^b |\psi\rangle$ | P | $P(X^a Z^b |\psi\rangle) \equiv X^a Z^{a \oplus b} (P |\psi\rangle)$ | $a'=a, b'=a \oplus b$ |
| $X^a Z^b \otimes X^c Z^d |\psi\rangle$ | CNOT | $CNOT(X^a Z^b \otimes X^c Z^d |\psi\rangle) \equiv (X^a Z^{b \oplus d} \otimes X^{a \oplus c} Z^d) (CNOT |\psi\rangle)$ | $a'=a, b'=b \oplus d$<br>$c'=a \oplus c, d'=d$ |
| $X^a Z^b |\psi\rangle$,<br>$x = a \oplus y$,<br>$Z^d P^v |+\rangle$ | R (and server's operations in Figure 5.1) | $c$ and $X^{a''} Z^{b''} (R |\psi\rangle)$<br>where $a'' = a \oplus c$ and<br>$b'' = a \cdot (c \oplus y \oplus 1) \oplus b \oplus d \oplus y$ | $a'=a'', b'=b''$ |

a) We ignore global phases in the equivalences "$\equiv$". The keys for decrypting are $(a', b')$ using $Z^{b'} X^{a'}$ (and $(c', d')$ in the case of CNOT).

- (1) The client encrypts its quantum register with the quantum one-time pad we saw earlier and then sends the contents of the register to the server (and the circuit to be executed).
- (2) The server then performs the computations according to the circuit using the encrypted quantum data, according to the procedures shown in Table 5.1, with the client computing the encryption keys for the corresponding quantum wire after each operation.
- (3) On completion, the server sends the output register to the client which then decrypts it using its computed keys.

The protocol in general is illustrated as follows, which implements a circuit $\mathcal{U} = U_1 \dots U_n$.

![](img/fb3eb7e935470a2da12b03f528f097ee_161_0.png)

```
Effectively, we want to compute $\mathcal{U} |\psi\rangle = dec(\mathcal{U} (enc(|\psi\rangle)))$
```

Let us look at an example of the client delegating to the server the following (contrived) quantum circuit acting on three qubits denoted by $q_1 q_2 q_3$ (top is $q_1$ to bottom $q_3$) as shown below.

![](img/fb3eb7e935470a2da12b03f528f097ee_162_0.png)

This circuit can be written as

$(I \otimes I \otimes X)(I \otimes R \otimes I)(CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R)$

where $CNOT_{q_1,q_2}$ denotes CNOT on the top two qubits, the top qubit $q_1$ as control, that is, the client wants the server to help it compute:

$|\psi'\rangle = (I \otimes I \otimes X)(I \otimes R \otimes I)(CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R) |\psi\rangle$

First, with randomly selected $a, b, c, d, e, f \in \{0, 1\}$, the client encrypts the three qubit state $|\psi\rangle$ using the following:

$(X^a Z^b \otimes X^c Z^d \otimes X^e Z^f) |\psi\rangle$

which is sent to the server. There are two R gate operations. For the first R gate operation, the client chooses randomly $y_1, d_1 \in \{0, 1\}$ and sends $x_1 = a \oplus y_1$ and $Z^{d_1} p^{y_1} |+\rangle$ and the above encrypted state to the server. From Figure 5.1, the server computes $c_1$ sending this to the client which the client keeps, and at slice 1, the server has computed: $(X^a Z^b \otimes X^c Z^d \otimes X^{e \oplus c_1} Z^{e \cdot (c_1 \oplus y_1 \oplus 1) \oplus f \oplus d_1 \oplus y_1}) (I \otimes I \otimes R) |\psi\rangle$.

Second, applying the CNOT to the top two qubits, at slice 2, the server has computed: $(X^a Z^{b \oplus d} \otimes X^{a \oplus e} Z^d \otimes X^{a''} Z^{b''})(CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R) |\psi\rangle$, where $a'' = e \oplus c_1$ and $b'' = e \cdot (c_1 \oplus y_1 \oplus 1) \oplus f \oplus d_1 \oplus y_1$.

Third, for the second R gate operation, the client chooses randomly $y_2, d_2 \in \{0, 1\}$, and sends $x_2 = (a \oplus c) \oplus y_2$ and $Z^{d_2} p^{y_2} |+\rangle$ to the server (note that these could be sent earlier even before computations begin to avoid any wait times in the middle of computations). From Figure 5.1, the server computes $c_2$ sending this to the client which the client keeps, and at slice 3, the server has computed:

$(X^a Z^{b \oplus d} \otimes X^{a''} Z^{b''} \otimes X^{a'''} Z^{b'''}) (I \otimes R \otimes I) (CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R) |\psi\rangle,$

where $a''' = (a \oplus c) \oplus c_2$, and $b''' = (a \oplus c) \cdot (c_2 \oplus y_2 \oplus 1) \oplus d \oplus d_2 \oplus y_2$.

Fourth and finally, applying the X gate to the qubit $q_3$ we have, at slice 4: $(X^a Z^{b \oplus d} \otimes X^{a''} Z^{b''} \otimes X^{a'''} Z^{b'''})(I \otimes I \otimes X)(I \otimes R \otimes I) (CNOT_{q_1,q_2} \otimes I) (I \otimes I \otimes R) |\psi\rangle = (X^a Z^{b \oplus d} \otimes X^{a''} Z^{b''} \otimes X^{a'''} Z^{b'''}) |\psi'\rangle$ which the server then sends to the client as the result. To decrypt the above, the client can apply to the result the operation: $Z^{b \oplus d} X^a \otimes Z^{b''} X^{a''} \otimes Z^{b'''} X^{a'''}$, in order to get $|\psi'\rangle$! Note that the client has $b$, $d$, and $a$, and all the information to compute $b''$, $a'''$, $b'''$, and $a''$, which can be viewed as the keys to decrypt each of the qubits in the result, i.e. the pairs $(a, b \oplus d)$, $(a'', b'')$, and $(a''', b''')$; the client effectively adjusts these keys according to the operations to compute the final keys.

An experimental demonstration of a protocol for delegated computation is explained in Fisher et al. [2014]. There is also an associated patent on quantum computing with encrypted data.$^4$

## 5.2 How to Verify Delegated Private Quantum Computations

Note that in the above scheme for delegated computation, there is a question of trust, whether the client trusts the server to perform the computations that it wants the server to perform. While the server cannot know what input it is receiving from the client due to the use of the quantum one-time pad, the server might not be performing the operation required by the client! How can the client verify that when it wants the server to apply an X gate, for example, that the server actually performs an X gate operation? The server might actually do nothing or apply some other operation. Worse still, the server might not be a quantum computer after all and pretending to be one!

This is a broader issue of verifying quantum computations. Sometimes it is easy to verify the result from a quantum computation. For example, for the problem of factoring a large number using Shor’s algorithm [Shor, 1994], once the client receives the answers from the server (which are suppose to be factors of a given large number), the client can do a multiplication to verify if the answers returned are indeed factors (and this would be true for other NP problems where verification can be done in polynomial time, say). But what about some problems where it is difficult, or intractable (at least if using only a classical computer or a client with limited quantum computing capabilities) to verify? This problem has been discussed extensively elsewhere – e.g. see the review in Gheorghiu et al. [2019].

Hence, the client, when delegating quantum computations to the server, doesn’t just want to hide its data from the server (so-called *private* or *blind quantum computing* [Fitzsimons, 2017]) but also verify that the server is honest or performing computations correctly (i.e. *verifiability*). Here, we outline and discuss briefly the idea of using test runs to detect a dishonest server, from Broadbent [2018], i.e. the idea of test runs being interleaved with actual computation runs in such a way that the server does not know which type of run it is, so that the server cannot adapt or react to avoid or pass such tests.

Suppose the client wants to apply the circuit C to input $|0\rangle^{\otimes n}$. Note that without loss of generality, we can assume the input is $|0\rangle^{\otimes n}$ since the preparation for an input $|x\rangle$ can be integrated into the circuit, i.e. \(C'|x\rangle = C|0\rangle^{\otimes n} = C'U|0\rangle^{\otimes n}\), where \(C = C'U\) and \(|x\rangle = U|0\rangle^{\otimes n}\).

The client randomly and uniformly chooses one of three possible types of runs (without telling the server its choice), sending to the server the quantum one-time pad encrypted input $|0\rangle^{\otimes n}$ and the circuit C; the client also sends to the server additional auxiliary qubits required for R-gate gadgets as we explain later:

- **Computation run**: The client delegates the actual required computation \(C|0\rangle^{\otimes n}\) to the server
- **X-test run**: The client delegates the identity computation on \(|0\rangle^{\otimes n}\) to the server
- **Z-test run**: The client delegates the identity computation on \(|+\rangle^{\otimes n}\) to the server

The server does not know which run it has been delegated since it is also given the circuit C in any of the above type of run, and the server simply performs each operation in C. The idea is that the server's actions or operations is the same in any of the above runs, and it is what the client does on its side that determines which type of run has happened, as we explain below.

The protocol for the runs is similar to what we have seen in Section 5.1, as shown in Table 5.1, but there are key differences in the way the R-gate and the H gate are performed. Let's look at how the runs would proceed for each type of gate (these procedures which we simply call gadgets), which will then provide an idea of how the computation of an entire circuit comprising such gates might be delegated.

### 5.2.1 X Gate Gadget

Suppose the client wants to perform the X gate operation on an encrypted qubit \(X^a Z^b |\psi\rangle\). We saw earlier that the server can perform an X gate operation on the encrypted qubit \(X^a Z^b |\psi\rangle\) to get \(XX^a Z^b |\psi\rangle \equiv X^a Z^b X |\psi\rangle\) which the client can decrypt using the keys a, b, i.e. using \(Z^b X^a\) to get \(X |\psi\rangle\). Another way to do this is actually have the server do nothing and just the client adjusting the keys to a', b', where \(a' = a \oplus 1\) and b' = b; this works since if the server sends back the original input \(X^a Z^b |\psi\rangle\), unchanged, then decrypting using a', b' gives:

```
\(Z^{b'} X^{a'} X^a Z^b |\psi\rangle = Z^b X^{a \oplus 1} X^a Z^b |\psi\rangle = Z^b X X^a X^a Z^b |\psi\rangle \equiv X |\psi\rangle\)
```

Note that the client adjusts its keys only in a computation run. Since it intends to compute the identity operation in the X-test and Z-test runs, the client does not

