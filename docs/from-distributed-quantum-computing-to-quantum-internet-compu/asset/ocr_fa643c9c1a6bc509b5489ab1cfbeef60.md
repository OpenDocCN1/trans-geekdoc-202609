Let us look at an example of the client delegating to the server the following (contrived) quantum circuit acting on three qubits denoted by $q_1 q_2 q_3$ (top is $q_1$ to bottom $q_3$) as shown below.

![](bbox=[0.3, 0.18, 0.7, 0.28])

This circuit can be written as

$(I \otimes I \otimes X)(I \otimes R \otimes I)(CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R)$

where $CNOT_{q_1,q_2}$ denotes CNOT on the top two qubits, the top qubit $q_1$ as control, that is, the client wants the server to help it compute:

$|\psi'\rangle = (I \otimes I \otimes X)(I \otimes R \otimes I)(CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R) |\psi\rangle$

First, with randomly selected $a, b, c, d, e, f \in \{0, 1\}$, the client encrypts the three qubit state $|\psi\rangle$ using the following:

$(X^a Z^b \otimes X^c Z^d \otimes X^e Z^f) |\psi\rangle$

which is sent to the server. There are two R gate operations. For the first R gate operation, the client chooses randomly $y_1, d_1 \in \{0, 1\}$ and sends $x_1 = a \oplus y_1$ and $Z^{d} p^{y_i} |+\rangle$ and the above encrypted state to the server. From Figure 5.1, the server computes $c_1$ sending this to the client which the client keeps, and at slice 1, the server has computed: $(X^a Z^b \otimes X^c Z^d \otimes X^e \oplus c_1 Z^e (c_1, \oplus y_1 \oplus 1) \oplus \oplus d, \oplus y_i) (I \otimes I \otimes R) |\psi\rangle$.

Second, applying the CNOT to the top two qubits, at slice 2, the server has computed: $(X^a Z^{b \oplus d} \otimes X^a \oplus e Z^d \otimes X^{a''} Z^{b''})(CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R) |\psi\rangle$, where $a'' = e \oplus c_1$ and $b'' = e \cdot (c_1 \oplus y_1 \oplus 1) \oplus f \oplus d_1 \oplus y_1$.

Third, for the second R gate operation, the client chooses randomly $y_2, d_2 \in \{0, 1\}$, and sends $x_2 = (a \oplus c) \oplus y_2$ and $Z^{d_2} p^{y_2} |+\rangle$ to the server (note that these could be sent earlier even before computations begin to avoid any wait times in the middle of computations). From Figure 5.1, the server computes $c_2$ sending this to the client which the client keeps, and at slice 3, the server has computed:

$(X^a Z^{b \oplus d} \otimes X^{a''} Z^{b''} \otimes X^{a'''} Z^{b'''}) (I \otimes R \otimes I) (CNOT_{q_1,q_2} \otimes I)(I \otimes I \otimes R) |\psi\rangle,$

where $a''' = (a \oplus c) \oplus c_2$, and $b''' = (a \oplus c) \cdot (c_2 \oplus y_2 \oplus 1) \oplus d \oplus d_2 \oplus y_2$.

Fourth and finally, applying the X gate to the qubit $q_3$ we have, at slice 4: $(X^a Z^{b \oplus d} \otimes X^{a''} Z^{b''} \otimes X^{a'''} Z^{b'''})(I \otimes I \otimes X)(I \otimes R \otimes I) (CNOT_{q_1,q_2} \otimes I) (I \otimes I \otimes R) |\psi\rangle = (X^a Z^{b \oplus d} \otimes X^{a''} Z^{b''} \otimes X^{a'''} Z^{b'''}) |\psi'\rangle$ which the server then