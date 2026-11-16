the ballot state (since if we get the resulting state (|i⟩ + |j⟩), then the ballot state contains either the term |i⟩ + |j⟩ or -|i⟩ - |j⟩, so that it must be that xi = xj, and if we get the resulting state (|i⟩ - |j⟩), then the ballot state contains either the term |i⟩ − |j⟩ or −|i⟩ + |j⟩, so that it must be that xi ≠ xj). This means that the voter can learn the parity p of xi and xj. This parity is then used to encode its vote, i.e. if its vote is v ∈ {0, 1}, then its encoded vote is a = p ⊕ v. For example, rewriting the ballot state example above to:

$$\frac{1}{\sqrt{6}}(-(|000\rangle + |011\rangle) + (|001\rangle + |100\rangle) - (|010\rangle - |101\rangle))$$

if the projectors above were used for measurement on the ballot state example, the voter might get the state:

$$\frac{1}{\sqrt{2}}(|000\rangle + |011\rangle)$$

and find out the parity between x0 and x3, i.e. it finds that x0 = x3, and use p = 0.
Each voter broadcasts its encoded vote a and its edge (i,j), i.e. each vote is accompanied by a distinct edge. Note that other voters, on hearing this, cannot yet decode the vote since they do not know x.

Once all the voters have broadcast their encoded vote (and the corresponding edge), that is, have effectively cast their votes, the tallyman reveals x to all so that each voter can decipher all the votes from everyone, and each determine the winner.

Only votes accompanied by distinct edges are counted, to prevent double voting. For example, if there are two votes accompanied by the same edge, then only the first one broadcasted can be counted. Or if there are two votes where the two edges share a node, then, only the first one broadcasted is counted. This would prevent, for example, two voters colluding to forge a vote, e.g. one voter used the edge (i,k) and another used the edge (k,j), then because xi ⊕ xj = (xi ⊕ xk) ⊕ (xk ⊕ xj), then they can collude to send in a vote accompanied by the edge (i,j) - two voters then provide three votes! The bit string length n can be made large enough so that the probability of two honest voters sampling, by chance, overlapping edges can be minimized.

What if a voter tries to present two votes, one encoded with the parity obtained from the actual edge obtained from measurement on the ballot state, and another encoded by guessing the parity of any other random edge? Note that the probability of guessing the parity of the other edge right is 1/2. Even if the guess was wrong, the additional vote could mess up results. This is prevented by repeating the voting protocol O(N) rounds and averaging the votes over the rounds – this means that the additional votes will on average have an equal number of 0s and 1s, and so, not affect the final result.