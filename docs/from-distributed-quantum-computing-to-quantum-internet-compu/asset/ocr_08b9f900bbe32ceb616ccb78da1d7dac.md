What if \( A \) wanted \( B \) to perform a \( H \) gate instead of a \( Z \) gate? As before, \( A \) has \( |\psi\rangle \) and then sends an encrypted quantum state to \( B \), i.e. choosing \( a, b \in \{0, 1\} \) it sends \( |\psi'\rangle = X^a Z^b |\psi\rangle \), to get \( B \) to apply \( H \) on the state. \( B \) performs \( H \) on it to get \( H |\psi'\rangle \) and sends this back to \( A \). \( A \), on receiving \( H |\psi'\rangle \), then applies \( Z^a X^b \) to it (note that this decryption operation is different from \( Z^b X^a \) used for the \( X \) and \( Z \) gates) to get:

```
Z^a X^b \left( H \, | \psi' \rangle \right) = Z^a X^b H X^a Z^b | \psi \rangle
= Z^a X^b Z^a H Z^b | \psi \rangle \qquad \text{(since } H X^a = Z^a H \text{)}
= Z^a X^a Z^b X^b H \, | \psi \rangle \qquad \text{(since } H Z^b = X^b H \text{)}
= \left\{\begin{array}{ll} H \, | \psi \rangle, \quad & \text{if } a=0, b=0 \\ XXX H \, | \psi \rangle = H \, | \psi \rangle, \quad & \text{if } a=0, b=1 \\ ZZ H \, | \psi \rangle = H \, | \psi \rangle, \quad & \text{if } a=1, b=0 \\ ZXZX H \, | \psi \rangle = - Z X X Z H \, | \psi \rangle = - H \, | \psi \rangle, \quad & \text{if } a=1, b=1 \end{array}\right.
```

Ignoring the global phase "-", \( A \) then gets \( H \, | \psi \rangle \) as required.

What if \( A \) wanted \( B \) to perform a \( P \) gate instead of a \( Z \) gate? The \( P \) gate or phase gate takes the following form: \(\begin{bmatrix} 1 & 0 \\ 0 & i \end{bmatrix}\), that is, \( P \, | 0 \rangle = | 0 \rangle \), and \( P \, | 1 \rangle = i \, | 1 \rangle \). As before, \( A \) has \( |\psi\rangle \) and then sends an encrypted quantum state to \( B \), i.e. choosing \( a, b \in \{0, 1\} \) it sends \( |\psi'\rangle = X^a Z^b |\psi\rangle \), to get \( B \) to apply \( P \) on the state. \( B \) performs \( P \) on it to get \( P \, |\psi'\rangle \) and sends this back to \( A \). \( A \), on receiving \( P \, |\psi'\rangle \), then performs \( Z^{a \oplus b} X^a \) to it (note this is different from the cases above) to get:

```
Z^{a \oplus b} X^a P \, | \psi' \rangle = Z^{a \oplus b} X^a P X^a Z^b \, | \psi \rangle
= (-i)^a Z^{a \oplus b} X^a Z^a X^a P Z^b \, | \psi \rangle \qquad \text{(since } P X^a = (-i)^a Z^a X^a P \text{)}
= (-i)^a Z^{a \oplus b} X^a Z^a X^a Z^b P \, | \psi \rangle \qquad \text{(since } P Z^b = Z^b P \text{)}
= \left\{\begin{array}{ll} P \, | \psi \rangle, \quad & \text{if } a=0, b=0 \\ ZZ P \, | \psi \rangle = P \, | \psi \rangle, \quad & \text{if } a=0, b=1 \\ (-i) X Z X X P \, | \psi \rangle = i X Z X X P \, | \psi \rangle = i P \, | \psi \rangle, \quad & \text{if } a=1, b=0 \\ (-i) X X Z X P \, | \psi \rangle = i X Z X X P \, | \psi \rangle = i P \, | \psi \rangle, \quad & \text{if } a=1, b=1 \end{array}\right.
```

Ignoring the global phase "i", \( A \) then gets \( P \, | \psi \rangle \) as required.

What if \( A \) wanted \( B \) to perform a CNOT gate instead? \( A \) now has a two qubit state \( |\psi\rangle \) and then sends the encrypted quantum state to \( B \), i.e. choosing \( a, b, c, d \in \{0, 1\} \) it sends \( |\psi'\rangle = X^a Z^b \otimes X^c Z^d |\psi\rangle \), to get \( B \) to apply CNOT on the state. \( B \) performs CNOT on it to get CNOT \( |\psi'\rangle \) and sends this back to \( A \). \( A \), on receiving CNOT \( |\psi'\rangle \), then applies \( Z^{b+d} X^a \otimes Z^d X^{a+c} \) to it to get: