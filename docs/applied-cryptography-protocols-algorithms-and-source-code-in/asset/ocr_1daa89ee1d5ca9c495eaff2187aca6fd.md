The future of IDEA is not yet clear. There has been no rush to adopt it as a replacement to DES, partly because it is patented and must be licensed for commercial applications, and partly because people are still waiting to see how well the algorithm fares during the coming years of cryptanalysis. Its current claim to fame is that it is part of PGP [see Section 24.12].

# Overview of IDEA

IDEA is a block cipher, it operates on 64-bit plaintext blocks. The key is 128 bits long. The algorithm is used for both encryption and decryption.

As with all other ciphers we've seen, IDEA uses both confusion and diffusion. The design philosophy behind the algorithm is one of "mixing operations from different algebraic groups." Three algebraic groups are being mixed, and they are all easily implemented in hardware and software:

+   - XOR
- Addition modulo $2^{16}$
- Multiplication modulo $2^{16} + 1$. (This operation can be viewed as IDEA's S-box).

All these operations (and these are the only operations in the algorithm—there are no bit-level permutations) operate on 16-bit sub-blocks. This algorithm is efficient on 16-bit processors.

# Description of IDEA

Figure 13.9 is an overview of IDEA. The 64-bit data block is divided into four 16-bit sub-blocks: $X_1, X_2, X_3$, and $X_4$. These four sub-blocks become the input to the first round of the algorithm. There are eight rounds total. In each round the four sub-blocks are XORed, added, and multiplied with one another and with six 16-bit keys. Between rounds, the second and third sub-blocks are swapped. Finally, the four sub-blocks are combined with four subkeys in an output transformation. In each round, the sequence of events is as follows:

+   (1) Multiply $X_1$ and the first subkey.
(2) Add $X_2$ and the second subkey.
(3) Add $X_3$ and the third subkey.
(4) Multiply $X_4$ and the fourth subkey.
(5) XOR the results of the steps [1] and [4].
(6) XOR the results of the steps [2] and [4].
(7) Multiply the results of step [5] with the fifth subkey.
(8) Add the results of steps [6] and [7].
(9) Multiply the results of step [8] with the sixth subkey.
(10) Add the results of steps (7) and (9).