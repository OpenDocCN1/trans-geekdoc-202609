+   3. measure all the qubits in the resulting state in the computational basis

Analysis: In each Grover iterate operation involving \( V_{a,b} \), two messages, each of \( (l + 1) = (\log_2 n + 1) \) qubits, are sent, and there would be \( t = O(\sqrt{n}) \) iterations; so, the algorithm uses a total of \( O(\sqrt{n} \cdot \log n) \) qubits of communication. Each qubit, sent by teleportation, would use a shared ebit and two classical bits, and so, \( O(\sqrt{n} \cdot \log n) \) classical bits of communication is required. In fact, a more efficient algorithm can do better – communicating only \( O(\sqrt{n}) \) qubits [Buhrman et al., 2010]. This contrasts with the classical algorithm which would require communicating about \( n \) bits, and so we have a quadratic gap of improvement in communication complexity with the quantum solution (particularly notable when \( n \) is very large)!

# 3.1.1.4 Discussion

We have seen an example of a distributed computation where the communication complexity was reduced using entanglement, by one bit, compared to the best possible classical protocol (without entanglement), an example on computing the DJ Promise Problem where the communication complexity was reduced by an exponential gap by transferring quantum states (e.g. using teleportation which might use entanglement), and a third example on computing the distributed intersection where a quadratic improvement gap is obtained. This leads to the following question raised by Buhrman et al. [2010]: “Could quantum communication complexity be much more efficient for every communication problem?” Unfortunately, the answer to the question is in the negative, and it was noted that for most communication complexity problems, “quantum communication does not help much”; for example, computing the inner product (of two \( n \)-bit strings with \( A \) having one and \( B \) having the other) was pointed out as an example where the best classical and quantum protocols both need \( n \) qubits/bits to be communicated to solve.

# 3.1.2 Enabling Distributed Computations Not Possible Classically

We have looked at how certain distributed computation problems can be solved with lower communication complexity with the use of quantum communication. We now look at certain distributed computation problems which cannot be solved without the use of quantum protocols, in particular, without entanglement. We look at two problems from Buhrman et al. [2010].

# 3.1.2.1 Greenberger–Horne–Zeilinger and Mermin (GHZ&M) Game

The name GHZ&M comes from the earlier authors on this problem [Buhrman et al., 2010]. Consider three parties with the inputs and outputs shown in