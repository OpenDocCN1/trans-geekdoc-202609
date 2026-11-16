at a quantum coin flipping protocol (a coin flipping protocol that uses quantum information), with an 0 < ε < 1/2.

# 3.2.1.2 Quantum Coin Flipping

Here, we use the quantum coin flipping protocol from Döscher and Keyl [2002], which uses qubits and qutrits (a three level quantum system, which can be in a superposition of three orthogonal states, |0⟩, |1⟩ and |2⟩).

+   1. Party A flips a coin with the result a ∈ {0, 1}, which is stored, and according to this result, a quantum state is prepared in a quantum system involving a qubit qs and a qutrit qr:
+   • if a = 0, then the state prepared is |ψ0⟩ = 1/√2(|0,0⟩ + |1,2⟩), and
+   • if a = 1, then the state prepared is |ψ1⟩ = 1/√2(|1,1⟩ + |0,2⟩).

(Note that the states |ψ0⟩ and |ψ1⟩ are orthogonal to each other, and so, can encode the two possible values of a.) Party A then sends parts of its quantum system’s state, i.e. the qutrit qr, to B, retaining the qubit state.

+   2. B receives the qutrit state and stores it. Also, B flips a coin with result b ∈ {0, 1} and sends the value of b to A.

+   3. Party A receives b and sends the qubit qs state to B. Party A can then already compute a ⊕ b at this point.

+   4. B now has the full state of A’s quantum system qsqr, and performs the projective measurement with operators P0 = |ψ0⟩⟨ψ0|, P1 = |ψ1⟩⟨ψ1| and P⊥ = I − P0 − P1, where I is the identity matrix. If the protocol was followed as above, given the way A’s quantum system was prepared, the full state of A’s quantum system (as obtained by B) will be either |ψ0⟩ (corresponding to a = 0) or |ψ1⟩ (corresponding to a = 1), and the measurement will reveal the state |ψ0⟩ with high probability if a had been 0, or the state |ψ1⟩ with high probability if a had been 1 due to (1) above, obtaining a result a′ = a. Party B can then already compute a′ ⊕ b, which should be equal to a ⊕ b obtained by A.

In the above, if both were honest, both can compute a ⊕ b, which is either 0 or 1 with equal probability – the protocol is correct.

Is the protocol secure? Note that A’s sending of its qutrit state to B in step (1) is in a way doing something like a bit commitment (though not quite as cheating is possible to an extent), and in step (3), when B receives qs is like a reveal, since it now has both qs and qr. Party A can try to cheat, however, by sending B some qutrit and some qubit that works out in its favor. For example, suppose A chose a = 0, and now tries to influence the outcome to be 0 (in A’s favor), as follows. Instead of |ψ0⟩, A uses the state

|ψ'0⟩ = 1/√6(|0,0⟩ + |0,1⟩ + 2|1,2⟩)