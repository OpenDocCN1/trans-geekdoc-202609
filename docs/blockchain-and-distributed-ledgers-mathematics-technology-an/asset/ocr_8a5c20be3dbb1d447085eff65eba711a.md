# 280 | Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

| True RNG | |
| --- | --- |
| Generates E | C |
| SHA256(E) | 0100 | Ignored |
| 0010110100 | ... | |
| N | | N/32 |
| word list | | |
| index | word | |
| 0 | abandon |
| 1 | ability |
| 360 | code |
| 2047 | code |
| | m0 | m1 | m2 |
| | 0010110100 | ... | ... |
| | 11 bits | | |
| | "code" | "desk" | "settle" |
| | Seed S PRKDF2HMAC-SHA512(...,salt="mnemonic", Iterations=2048) | |

**Figure 9.9** RNG to mnemonic to seeding BIP39 specification. Own graphics.

enough that it can be brute-forced. Quoting the authors, "BIP39 is meant to be a way to transport computer-generated randomness with a human readable transcription." It makes manipulation and storage of a large number easier and less prone to errors while guaranteeing entropy for the generation of ECDSA secret keys, in particular in the context of a hierarchical deterministic key derivation algorithm such as BIP32. Figure 9.9 illustrates the combination of BIP39 and BIP32 that the master extended key is derived from a seed, computed from a mnemonic code: the mnemonic is sufficient to recover the complete hierarchy of keys and therefore to demonstrate ownership of any of the derived accounts.

We describe the algorithms below:

+   (1) An initial entropy $E$ of $N$ bits is generated, where $N \in \{128, 160, 192, 224, 256\}$.
(2) A checksum $C$ is set to the first $N/32$ bits of SHA256(E).\n(3) The concatenation $E|C$ of initial entropy and the checksum is split into sequences of 11 bits, respectively $m_0, m_1, \dots, m_{N+N/32-1}$.

+   (4) Integers $(m_i)$, each encoding a number from 0 to 2047, serve as a sequence of indices into a wordlist to construct the mnemonic code.

+   (5) The 512-bit seed $S$ is the output of the Password-Based Key Derivation Function 2 (PBKDF2) using mnemonic as input, and salt to constant string "mnemonic" (optionally augmented with secret passphrase). The iteration count is set to 2048 and HMAC-SHA512 is used as the pseudo-random function.

The wordlist, or dictionary, proposed by the authors of BIP39 is a careful selection of natural language words satisfying the following:

+   * smart selection of words: the wordlist is created in such way that first four letters unambiguously identify a complete word