```
E(-\pi/16, -\pi/16) \approx \frac{N_{00}^{+1,+1} + N_{00}^{-1,-1} - N_{00}^{+1,-1} - N_{00}^{-1,+1}}{N_{00}}
= \frac{1}{N_{00}} \sum_{v=0}^{N_{00}} A_0^v B_0^v = \langle A_0 B_0 \rangle
```

where we used the definition of \(\langle A, B_j \rangle\) we saw earlier. We can get estimates for \(E(-\pi/16, 3\pi/16)\), \(E(3\pi/16, -\pi/16)\) and \(E(3\pi/16, 3\pi/16)\) in a similar way and compute \(S(\theta_1 = -\pi/16, \theta_2 = 3\pi/16)\) experimentally. Violations of the CHSH inequality have been experimentally shown as discussed in Wolf [2021].

# ## 3.1.2.3 Discussion

We can see from the above that there is something remarkable with entanglement that allows certain "no communication" problems to be solved that classically cannot be solved, by allowing certain correlated bits to be shared. In fact, the CHSH problem can be used as a test of genuine entanglement – if \(A\) and \(B\) can share genuine entangled pairs of qubits, then they should be able to solve the CHSH problem with higher probability than 0.75! In a way, entanglement seems to have made up (at least in part) for the "no communication" constraint between \(A\) and \(B\).

# ## 3.2 Other Quantum Protocols

We briefly consider several other quantum versions of distributed system protocols, including quantum coin flipping, quantum leader election, quantum key distribution, quantum voting, quantum oblivious transfer, and the quantum Byzantine Generals solution.

# ### 3.2.1 Quantum Coin Flipping

# #### 3.2.1.1 Classical Coin Flipping

Coin flipping (or tossing) is the following problem first proposed by Blum [1983]. Before introducing quantum coin flipping, let us discuss the classical coin flipping problem first.⁵

Suppose machines \(A\) and \(B\) don't trust each other (or two people, typically Alice and Bob who is divorced and don't trust each other anymore) but wants to agree on a fair coin flip over the telephone. For example, machine \(A\) chooses "head" (or 1) and \(B\) chooses "tail" (or 0), and \(A\) flips a (presumably non-bias) coin and tells \(B\) over the phone that it is "head" – if \(B\) trusts \(A\), then this is not a problem, but if not,

⁵ Parts of our discussion here uses the explanations from https://zoo.cs.yale.edu/classes/cs467/2013s/lectures/ln21.pdf [last accessed: 9/11/2022].