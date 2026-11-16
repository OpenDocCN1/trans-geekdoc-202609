b) suppose we get 1, we then have:

at slice 6 : $\alpha |011\rangle |t\rangle - \beta |111\rangle (X |t\rangle)$
$= \alpha |0\rangle |11\rangle |t\rangle - \beta |1\rangle |11\rangle (X |t\rangle)$

and "1" sent to A means that the Z gate is applied, and so, leaving out the second and third qubits, and adding subscripts, we can write the final state as

$\alpha |0\rangle_A |t\rangle_B + \beta |1\rangle_A(X|t\rangle_B)$

which is the same as in case (a).

Note that the cases (1)(a), (1)(b), (2)(b), and (2)(a) all have the same result if we consider just the first and fourth qubits, which is also the same as the result from the teleportation method, which is what we expect – we now have a more efficient way to implement a distributed CNOT. Note that in this method, the distributed CNOT operation was done using one pair of entangled qubits (i.e. one ebit) shared between A and B and two classical bits (one from A to B and the other from B to A), which is half the resources required for the teleportation method! It turns out that this is optimal as shown by Eisert et al. [2000], in that one bit of classical communication from A to B, one classical bit from B to A and one shared ebit are together what is minimal to implement a distributed CNOT gate.

Let us take a closer look at why the above has worked. One main observation is that the first and third qubits (as underlined below) form a cat-like state at slice 3 in both cases:

+   case (1) : $(\alpha |000\rangle + \beta |101\rangle) \otimes |t\rangle$
+   case (2) : $(\alpha |010\rangle + \beta |111\rangle) \otimes |t\rangle$

that is, leaving out the second qubit, the cat-like state in both cases is

$\alpha |00\rangle |t\rangle + \beta |11\rangle (X |t\rangle)$

from the underlined qubits, where we see that the first and third qubits always have the same value (0 or 1) – which means that controlling on the first qubit (at A) is the same as controlling on the third qubit (i.e. the first qubit at B). Now, adding the subscripts to denote the location of the first and third qubits, and the target qubit, in slice 3:

$\alpha |0\rangle_A |0\rangle_B |t\rangle_B + \beta |1\rangle_A |1\rangle_B (X|t\rangle_B)$

We see that step 4 (the local CNOT between the third and fourth qubits at B) is effectively a CNOT between the first qubit (at A) and the fourth qubit (at B)!

Distribution of such cat-like states is key to being able to implement distributed control gates using entanglement as a resource. In general, we can summarize this concept via the following circuit – where the second qubit is omitted.