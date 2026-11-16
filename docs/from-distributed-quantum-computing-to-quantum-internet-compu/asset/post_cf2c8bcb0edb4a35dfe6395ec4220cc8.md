
well-studied. As far back as 1984, Charles Bennett and Gilles Brassard introduced the BB84 protocol which uses quantum information to generate such a shared key among two communicating parties.10 QKD is well described in other sources, e.g. see Wolf [2021] and Van Assche [2006], but we outline the BB84 protocol here, based mainly on the excellent description by Vidick and Wehner.11 In this protocol, A basically generates the key and “communicates” it to B but in a way that is secure and an eavesdropper would not be able to get the key without being detected. We assume that there is a classical channel between A and B.

- 1. A chooses an n-bit string \(x = x_1 ... x_n \in \{0, 1\}^n\) uniformly at random. A also chooses a basis string \(\theta = \theta_1 ... \theta_n\) uniformly at random, which determines what basis to encode each bit of \(x\). A transmits \(x\) to \(B\) by encoding each bit in a quantum state as follows: \(H^{\theta_j}|x_j\rangle\), where \(\theta_j \in \{0, 1\}\), i.e. \(A\) effectively sends \(n\) qubits to \(B\). This means that for some \(x_j\), if \(\theta_j = 0\), the computational basis is used, and \(x_j\) is encoded as \(|x_j\rangle\) and if \(\theta_j = 1\), the Hadamard basis is used, and \(x_j\) is encoded as \(H|x_j\rangle\) (recall that \(H |0\rangle = |+\rangle = (|0\rangle + |1\rangle)/\sqrt{2}\) and \(H |1\rangle = |-\rangle = (|0\rangle - |1\rangle)/\sqrt{2}\)).

- 2. B chooses a basis string \(\theta' = \theta'_1 ... \theta'_n\) uniformly at random and measures qubit \(j\) it received from \(A\) in the basis \(\theta'_j\) to produce outcome \(x'_j\).

- 3. B tells A over the classical channel that it has received and measured all the qubits.

- 4. A and B then tell each (over the classical channel) their basis strings \(\theta\) and \(\theta'\).

- 5. A and B then discards all rounds where they did not use the same basis. The set of indices for rounds which are kept \(S = \{j \mid \theta_j = \theta'_j\}\), and since \(A\) and \(B\) choose from two basis options with equal probability, we have for large \(n\), roughly \(n/2\) bits kept, discarding roughly half of the rounds.

- 6. To test for an eavesdropper, which might have intercepted qubits from \(A\), measuring them and resending them to \(B\), i.e. an intercept-resend attack, \(A\) picks a subset \(T \subseteq S\) for testing, where \(|T| = n/4\) bits, that is, roughly half the kept bits (which were measured in the same basis). Note that for the bits indexed in \(T\), since they were the result of using the same basis (for encoding by \(A\) and measurement by \(B\)), we should expect all of these bits to be the same; if a significantly more of these bits are not the same (i.e. the qubits have been “disturbed”), this suggests there has been an eavesdropper who did an intercept-resend attack – to see this, see **Aside**.

**Aside:** Consider an eavesdropper that _always measures in the computational basis_ (there could be more sophisticated attackers but this is just an example), e.g. when _A_ sends |_x<sub>j</sub>_⟩ (i.e. encoding the bit _x<sub>j</sub>_ in the computational basis), the eavesdropper measures in the same basis as _A_ and suppose _B_ also measures in the same basis, then the eavesdropper has got it right and will be undetected in this instance! But suppose _x<sub>j</sub>_ = 0, and _A_ sends _H_|_x<sub>j</sub>_⟩ = |+⟩ = (|0⟩ + |1⟩)/√2 (i.e. encoding the bit 0 in the Hadamard basis), the eavesdropper measures in the computational basis and gets eigenvalue 1 say with |0⟩ with probability 1/2 and -1 with |1⟩ with probability 1/2. Suppose the eavesdropper gets |0⟩ and forward this to _B_, and suppose _B_ happens to measure in the same basis that _A_ used, then, since |0⟩ = (|+⟩ + |-⟩)/√2, _B_ gets |+⟩ with probability 1/2 and |-⟩ with probability 1/2; now, suppose _B_ gets |-⟩, then the summary is that _A_ and _B_ used the same basis, but the result that _B_ obtained is |-⟩ which is different from what _A_ sent! So the eavesdropping has affected the qubits so that the result is not what is expected – in this case, leading to errors that should not have happened. We can compute the statistics to see how much error such an eavesdropper _E_ will introduce in all cases where _A_ and _B_ used the same basis (that is, when we do not expect an error):

| A's bit | A's encoding | E's measured and resend state | B's result using the same basis as A | Error? |
|---|---|---|---|---|
| 0 | `|0⟩` | `|0⟩` | `|0⟩` | N |
| 1 | `|1⟩` | `|1⟩` | `|1⟩` | N |
| 0 | `|+⟩` | `|0⟩` | `|+⟩` | N |
| 0 | `|+⟩` | `|0⟩` | `|-⟩` | Y |
| 0 | `|+⟩` | `|1⟩` | `|+⟩` | N |
| 0 | `|+⟩` | `|1⟩` | `|-⟩` | Y |
| 1 | `|-⟩` | `|0⟩` | `|+⟩` | Y |
| 1 | `|-⟩` | `|0⟩` | `|-⟩` | N |
| 1 | `|-⟩` | `|1⟩` | `|+⟩` | Y |
| 1 | `|-⟩` | `|1⟩` | `|-⟩` | N |

> One can see a lot more errors due to E; without E there would not be any errors when both A and B are using the same basis (ignoring noisy channels).

The test for an eavesdropper is done as follows: A and B announce (over the classical channel) to each other values \(x_j\) and \(x'_j\) where \(j \in T\) and compute the error rate \(err = |W|/|T|\), where \(W = \{j \in T | x_j \neq x'_j\}\) is the set of indices where there is a mismatch even when A and B used the same basis. So, if the error rate \(err > 0\), then A and B abort the protocol, since there is likely an eavesdropper. But if \(err = 0\), then there is likely no eavesdropping (though that is no guarantee that it is so since the eavesdropper might indeed be super-lucky to be undetected!) the set of bits corresponding to those in S but not used for testing, that is, indices in S\T will be a sequence of shared bits that will be used by A and B to form the key, i.e. on A's side, the key is \(x_j\) where \(j \in S \setminus T\), and on B's side, the key is \(x'_j\) where \(j \in S \setminus T\). Note that \(|S \setminus T|\) is around \(n/4\). In fact due to possible errors in transmission, it may be alright to not abort as long as \(err < \epsilon\) for some bound \(\epsilon\) on the error rate. Note that we used \(n/4\) bits for testing to check if the remaining \(n/4\) bits would be usable – and the tested bits are not the ones used – how does this work? As explained in Wolf [2021], and we won't repeat the argument here, the error rate in the sample \(T \subseteq S\) is, with high probability, close to the error rate for the whole string (of bits in) S, when \(n\) is large, i.e. a high error rate in the sample suggests a high error rate in the whole string, so that testing with the sample already provides an adequate picture of the error rate to expect with the bits in S \ T.

- 7. A and B can go through a process called *privacy amplification* (an example given below) to further improve security, just in case (e.g. since small errors due to transmission is difficult to be differentiated from errors due to eavesdropping), which would result in the final key \(k\) of length less than \(|S \ T| = n/4\).

The idea of privacy amplification is to further improve the secrecy of keys by extracting a (smaller) “real key” (of length less than \(n/4\)) to be used from the remaining bits indexed in \(S \ T\). One way to do simple privacy amplification is to take pairs of bits from \(S \ T\) and XOR them, (or add modulo two, i.e. applying \(\oplus\)) to obtain a shorter (but more secure key).\(^12\) There are other more sophisticated privacy amplification methods [Wolf, 2021; Van Assche, 2006].

12 This algorithm is explained as follows, where A is Alice, B is Bob and the eavesdropper is Eve:

After error correction, Alice and Bob have identical copies of a key, but Eve may still have some information about it... Alice and Bob thus need to reduce Eve’s information to an arbitrarily low value using some privacy amplification protocols. These classical protocols typically work as follows. Alice again randomly chooses pairs of bits and

For error correction, there is also a step called *information reconciliation* which after the error rate has been determined, via the testing, $A$ and $B$ proceed to correcting the errors, as elaborated on in Wolf [2021]. A protocol to ensure that both parties have the same bit string, i.e. to perform “error key reconciliation” (called Cascade) using parity values on blocks of bit strings is described in Mehic et al. [2022].

We next consider the QKD protocol by Artur Ekert called the E91 protocol [Ekert, 1991] that uses entangled states (Bell states) shared among the two communicating parties to generate a shared key between them. The protocol proceeds as follows to generate an $n$-bit key shared by the two parties $A$ and $B$.

- 1. A third party is a source of $n$ entangled pairs of qubits, each in the state: $\frac{1}{\sqrt{2}}(|00\rangle + |11\rangle)$. Each of the $n$ two-qubit states is then shared by the two parties by the third party sending one qubit of each pair to each party. (We can also use other states such as the singlet state as originally done in Ekert [1991] to a similar effect.)

- 2. On receiving the qubits, for each qubit received, $A$ randomly chooses one basis from among three possibilities, denoted by $\mathbf{a}_1, \mathbf{a}_2$, and $\mathbf{a}_3$:

- $\mathbf{a}_1$: A basis based on observable $Z$, i.e. a measurement with outcome either $+1$ corresponding to $Z$’s eigenvector $|0\rangle$ or $-1$ corresponding to the other eigenvector $|1\rangle$ of $Z$,

- $\mathbf{a}_2$: A basis based on observable $(X + Z)/\sqrt{2} = H$, with outcome $+1$ corresponding to $H\)’s eigenvector $|\mathbf{x}\rangle = \cos(\frac{\pi}{8})|0\rangle + \sin(\frac{\pi}{8})|1\rangle$ or $-1\) corresponding to the other eigenvector $|\boldsymbol{-}\rangle = -\sin(\frac{\pi}{8})|0\rangle + \cos(\frac{\pi}{8})|1\rangle\)) of $H\),$^{13}$ and

computes their XOR value. But, in contrast to error correction, she does not announce this XOR value. She only announces which bits she chose (e.g. bits number 103 and 537). Alice and Bob then replace the two bits by their XOR value. In this way, they shortened their key while keeping it error free, but if Eve has only partial information on the two bits, her information on the XOR value is even less. Assume, for example, that Eve knows only the value of the first bit and nothing about the second one. Then she has no information at all about the XOR value. Also, if Eve knows the value of both bits with 60% probability, then the probability that she correctly guesses the XOR value is only $0.6^2 + 0.4^2 = 52\%$. This process would have to be repeated several times; more efficient algorithms use larger blocks ... [Gisin et al., 2002, Section C4 in Arxiv version, https://arxiv.org/pdf/quant-ph/0101098.pdf, accessed: 22/11/2022]

Roughly, the resulting key using this way of privacy amplification might be of length $(n/4)/2 = n/8$.

$^{13}$ One can check that these are the eigenvectors of $H$ via trigonometric identities (e.g. see https://sciencenotes.org/trig-identities-study-sheet) and noting that $\cos(\frac{\pi}{4}) = \frac{1}{\sqrt{2}}$.
