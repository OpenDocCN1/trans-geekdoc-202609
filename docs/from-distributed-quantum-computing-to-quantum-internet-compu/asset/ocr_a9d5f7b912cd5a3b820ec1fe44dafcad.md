then apply \( U_b \) to \( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |0\rangle \) (i.e. the result from (i) plus an ancillary qubit in state \( |0\rangle \)) to get:

\( U_b \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |0\rangle \right) = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} U_b |i\rangle |0\rangle \)

(by linearity)

\( = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |0 \oplus b_i\rangle = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |b_i\rangle \)

(iii) and apply \( I^{\otimes l} \otimes Z \) to the result from (ii) to get:

\( (I^{\otimes l} \otimes Z) \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} |i\rangle |b_i\rangle \right) = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |b_i\rangle \)

(iv) and finally to “disentangle” the first \( l \) qubits from the last qubit, we apply \( U_b \) (again!) to the result from (iii) to get:

\( U_b \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |b_i\rangle \right) \\
= \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} U_b |i\rangle |b_i\rangle = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |b_i \oplus b_i\rangle \\
= \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle |0\rangle = \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle \right) \otimes |0\rangle \)

That is, in (ii)–(iv), we applied \( U_b(I^{\otimes l} \otimes Z)U_b \) and the last qubit can be measured (discarded) to get the state we wanted to prepare \( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle \); this \( l \)-qubit state is then sent to \( A \) (e.g. via teleportation – say, by teleporting each qubit separately).

+   2. \( A \) receives the state and applies an operation that maps \( |i\rangle \) to \( (-1)^{\alpha_i} |i\rangle \), and then also applies the Hadamard transform to each qubit and measures the resulting \( l \)-qubit string.

The mapping from \( |i\rangle \) to \( (-1)^{\alpha_i} |i\rangle \) can be done using an operation \( U_a \) defined similarly to \( U_b \) above; that is, we apply \( U_a(I^{\otimes l} \otimes Z)U_a \) to the received state with an ancilla qubit \( |0\rangle \):

\( U_a(I^{\otimes l} \otimes Z)U_a \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{b_i} |i\rangle \right) |0\rangle = \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{\alpha_i + b_i} |i\rangle \right) |0\rangle \)

and the last qubit discarded. Then, after the Hadamard transforms, what is measured is the state:

\( H^{\otimes l} \left( \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{\alpha_i + b_i} |i\rangle \right) = \frac{1}{\sqrt{n}} \sum_{i=0}^{n-1} (-1)^{\alpha_i + b_i} H^{\otimes l} |i\rangle \)