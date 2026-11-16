quantum circuits comprising a composition of quantum gates, analogous to digital circuits comprising a composition of logic gates. Each line in a quantum circuit is a wire representing a qubit and the passage of time is typically from left to right, and the order of computations as shown in a circuit is read from left to right (note that this is in reverse order to a sequence of matrices representing the operations) as we illustrate below. As an example, consider the following two-qubit circuit, shown in Figure 2.6.

![](bbox=[0.66, 0.11, 0.88, 0.26])

Equivalently, supposing the state of the two-qubit system can be written as \(|q_1\rangle \otimes |q_2\rangle\), the operations represented by the circuit can be written in matrix form, as follows:

```
(I \otimes U_3)(U_1 \otimes U_2)(|q1\rangle \otimes |q2\rangle)
```

which is the product of the matrices \(I \otimes U_3\), and \(U_1 \otimes U_2\) in the order shown above – we used the identity matrix \(I\) since there is no operation on that qubit at that stage. Using the property about the product of tensor products, i.e. \((A \otimes B)(C \otimes D) = AC \otimes BD\), we rewrite the above as \((I \otimes U_3)(U_1 \otimes U_2)(|q1\rangle \otimes |q2\rangle) = U_1|q1\rangle \otimes U_3 U_2|q2\rangle\). But as we shall see when we talk about entanglement that not all two-qubit states can be written as a product of two vectors of the form \(|\psi\rangle \otimes |\psi\rangle = |\psi\psi\rangle\), but more generally, a two-qubit state \(|\psi\rangle\) is a linear combination of such products, as we have seen, e.g. with respect to the computational basis, \(|\psi\rangle = \alpha|00\rangle + \beta|01\rangle + \gamma|10\rangle + \delta|11\rangle\); a relabeling is shown in Figure 2.7a. In fact, for each component of the superposition, one could imagine a corresponding circuit as illustrated in Figure 2.7b. Hence, one might consider Figure 2.7a as an “abbreviation” for Figure 2.7b.

That is, in this case, we have

```
(U_1 \otimes U_3 U_2)|\psi\rangle = (U_1 \otimes U_3 U_2)(\alpha|00\rangle + \beta|01\rangle + \gamma|10\rangle + \delta|11\rangle)
= \alpha(U_1 \otimes U_3 U_2)|00\rangle + \beta(U_1 \otimes U_3 U_2)|01\rangle
+ \gamma(U_1 \otimes U_3 U_2)|10\rangle + \delta(U_1 \otimes U_3 U_2)|11\rangle
```

with probabilities corresponding to the components in Figure 2.7b.

We consider another example of a circuit; the following three qubit circuit, shown in Figure 2.8. We can see how the single and double qubit gates we mentioned can be combined to form quantum circuits, representing operations over a set of qubits.

Note also that the operations represented by an n-qubit quantum circuit corresponds to an n-qubit unitary operation; the tensor product of unitary matrices is