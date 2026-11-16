

p(+1) = |\frac{\alpha + \beta}{\sqrt{2}}|^2 with resulting state |0⟩, and the probability of getting an outcome corresponding to eigenvalue -1 is p(-1) = |\frac{\alpha - \beta}{\sqrt{2}}|^2 with resulting state |1⟩, i.e. the same probabilities as when we were measuring in the Hadamard basis! This means that measuring with respect to the Hadamard basis is effectively equivalent (except for the resulting states) to first applying H to the state and then measuring with respect to the computational basis. Hence, a key observation from the last two paragraphs is that the same state can be measured with respect to different bases, with potentially different outcome states (corresponding to the basis states) and probabilities of outcomes. A more extensive discussion of measurement operators is in Nielsen and Chuang [2000]. The symbol we will use for measurement is as shown in Figure 2.4.

![](img/fb3eb7e935470a2da12b03f528f097ee_43_0.png)

## 2.2.3 Multiple Qubit Gates

Just like we have logic gates that take more than one operand, we have quantum gates that can take multiple qubits as input. One example is the controlled-NOT (or CNOT) gate which takes two qubits, one called a control qubit and another called a target qubit, and depending on the state of the control qubit, determines whether to apply an X gate to the target qubit. It does the following mapping, where reading from left to right, the first qubit is the control qubit and the second qubit is the target qubit: |00⟩ → |00⟩, |01⟩ → |01⟩, |10⟩ → |11⟩, |11⟩ → |10⟩, or in general: |c⟩|t⟩ → CNOT |c⟩|t ⊕ c⟩, where “⊕” denotes the exclusive OR operator (or addition modulo 2). The symbol for a CNOT gate is given in Figure 2.5. More generally, we can also have a controlled-U gate of the form: |c⟩|t⟩ → controlled-U |c⟩ U|t⟩. The CNOT gate is basically a controlled-X gate. The symbol for a controlled-U gate is given in Figure 2.5.

## 2.2.4 Quantum Circuits

We have seen some examples of symbols for quantum gates. When these gates are composed and the gates are acting on one or more qubits, we can construct

![](img/fb3eb7e935470a2da12b03f528f097ee_43_1.png)

quantum circuits comprising a composition of quantum gates, analogous to digital circuits comprising a composition of logic gates. Each line in a quantum circuit is a wire representing a qubit and the passage of time is typically from left to right, and the order of computations as shown in a circuit is read from left to right (note that this is in reverse order to a sequence of matrices representing the operations) as we illustrate below. As an example, consider the following two-qubit circuit, shown in Figure 2.6.

![](img/fb3eb7e935470a2da12b03f528f097ee_44_0.png)

Equivalently, supposing the state of the two-qubit system can be written as \(|q_1\rangle \otimes |q_2\rangle\), the operations represented by the circuit can be written in matrix form, as follows:

```
(I \otimes U_3)(U_1 \otimes U_2)(|q_1\rangle \otimes |q_2\rangle)
```

which is the product of the matrices \(I \otimes U_3\), and \(U_1 \otimes U_2\) in the order shown above – we used the identity matrix \(I\) since there is no operation on that qubit at that stage. Using the property about the product of tensor products, i.e. \((A \otimes B)(C \otimes D) = AC \otimes BD\), we rewrite the above as \((I \otimes U_3)(U_1 \otimes U_2)(|q_1\rangle \otimes |q_2\rangle) = U_1|q_1\rangle \otimes U_3 U_2|q_2\rangle\). But as we shall see when we talk about entanglement that not all two-qubit states can be written as a product of two vectors of the form \(|\psi\rangle \otimes |\psi\rangle = |\psi\psi\rangle\), but more generally, a two-qubit state \(|\psi\rangle\) is a linear combination of such products, as we have seen, e.g. with respect to the computational basis, \(|\psi\rangle = \alpha|00\rangle + \beta|01\rangle + \gamma|10\rangle + \delta|11\rangle\); a relabeling is shown in Figure 2.7a. In fact, for each component of the superposition, one could imagine a corresponding circuit as illustrated in Figure 2.7b. Hence, one might consider Figure 2.7a as an “abbreviation” for Figure 2.7b.

That is, in this case, we have

```
(U_1 \otimes U_3 U_2)|\psi\rangle = (U_1 \otimes U_3 U_2)(\alpha|00\rangle + \beta|01\rangle + \gamma|10\rangle + \delta|11\rangle)
= \alpha(U_1 \otimes U_3 U_2)|00\rangle + \beta(U_1 \otimes U_3 U_2)|01\rangle
+ \gamma(U_1 \otimes U_3 U_2)|10\rangle + \delta(U_1 \otimes U_3 U_2)|11\rangle
```

with probabilities corresponding to the components in Figure 2.7b.

We consider another example of a circuit; the following three qubit circuit, shown in Figure 2.8. We can see how the single and double qubit gates we mentioned can be combined to form quantum circuits, representing operations over a set of qubits.

Note also that the operations represented by an n-qubit quantum circuit corresponds to an n-qubit unitary operation; the tensor product of unitary matrices is

![](img/fb3eb7e935470a2da12b03f528f097ee_45_0.png)

![](img/fb3eb7e935470a2da12b03f528f097ee_45_1.png)

**Figure 2.7** An example of a two-qubit circuit and label for the new state after the operations of the circuit. (b) Illustration of four circuits with two wires, one for each possible component in a superposition \(\alpha |00\rangle + \beta |01\rangle + \gamma |10\rangle + \delta |11\rangle\) with the new state after the operations of the circuit, for each possible component.

also a unitary matrix,<sup>15</sup> and the product of two unitary matrices is also a unitary matrix.<sup>16</sup>

15 We can see this since \((A \otimes B)^\dagger = A^\dagger \otimes B^\dagger\), we have \((A \otimes B)(A \otimes B)^\dagger = (A \otimes B)(A^\dagger \otimes B^\dagger) = AA^\dagger \otimes BB^\dagger = I_{\text{dim}(A)} \otimes I_{\text{dim}(B)} = I_{\text{dim}(A)\text{dim}(B)}\), and similar calculations for \((A \otimes B)^\dagger (A \otimes B)\).
16 To see this, since \((AB)^\dagger = B^\dagger A^\dagger\), we have \(AB(AB)^\dagger = ABB^\dagger A^\dagger = AIA^\dagger = AA^\dagger = I\).

It is interesting to observe the following circuit which is used later in the book, shown in Figure 2.9, where we have \(|\psi\rangle = \alpha|0\rangle + \beta|1\rangle\), which computes the CNOT on \(|\psi\rangle|0\rangle = (\alpha|0\rangle + \beta|1\rangle)|0\rangle = \alpha|00\rangle + \beta|10\rangle\), with the resulting state \(\alpha|00\rangle + \beta|11\rangle\). Note that the circuit does not, in general, actually compute a copy of \( |\psi\rangle \) since
\( |\psi\rangle |\psi\rangle = \alpha^2 |00\rangle + \alpha\beta |01\rangle + \beta\alpha |10\rangle + \beta^2 |11\rangle \)
which is equal to \( \alpha |00\rangle + \beta |11\rangle \) when \( \alpha\beta = 0, \alpha^2 = \alpha \), and \( \beta^2 = \beta \), e.g. when \( \alpha = 1 \) and \( \beta = 0 \), or when \( \alpha = 0 \) and \( \beta = 1 \).

![](img/fb3eb7e935470a2da12b03f528f097ee_46_0.png)

Figure 2.8 An example circuit with three wires for three qubits.

In fact, there is no unitary operation that will, for any quantum state \( |\psi\rangle \), take \( |\psi\rangle |0\rangle \) and yield \( |\psi\rangle |\psi\rangle \), a fact called the *no-cloning theorem* - see a proof in Nielsen and Chuang [2000]. This theorem has consequences for robust computations and quantum communications since making copies of information is a typical way to deal with lost or corrupted information, at least with classical information. The area of study called *quantum error correction* looks at ways to deal with errors in quantum information. If obtaining \( |\psi\rangle |\psi\rangle \) was possible, then if, say, the first qubit was lost (or somehow “measured”), we still retain the information in the second qubit \( |\psi\rangle \) (the notation \( |\psi\rangle |\psi\rangle = |\psi\rangle \otimes |\psi\rangle \) essentially suggests the two qubits are “separate”), but if we have \( \alpha |00\rangle + \beta |11\rangle \), then losing the first qubit (effectively, somehow “measured out”), the state “collapses” to \( |00\rangle \) or \( |11\rangle \) and the first qubit lost, then we either have \( |0\rangle \) or \( |1\rangle \) remaining and basically losing all the information encoded in the probability amplitudes \( \alpha \) and \( \beta \). We will see many other quantum circuits in this book for different computations.

![](img/fb3eb7e935470a2da12b03f528f097ee_46_1.png)

Figure 2.9 An example circuit which looks like a copying operation.

## 2.2.5 Universal Quantum Computer and Gate Sets

By composing gates in a quantum circuit, complex manipulations can be performed on qubits. The gates composed can be drawn from a small finite set, and with the right set of gates, any unitary operation can be approximated (to arbitrary accuracy) by composing gates (drawn from the set) together in a quantum circuit.

The Solovay-Kitaev theorem states that, given a distance \(\epsilon\) (using a distance measure representing the difference between two operations, which we will not go into detail here), one can approximate any given unitary operation on \(n\) qubits using \(O(n^2 4^n \log^c(n^{2^4} / \epsilon))\) gates [Nielsen and Chuang, 2000]. This is analogous to how a small set of logic gates (e.g. {AND, OR, NOT}) can be considered universal in

