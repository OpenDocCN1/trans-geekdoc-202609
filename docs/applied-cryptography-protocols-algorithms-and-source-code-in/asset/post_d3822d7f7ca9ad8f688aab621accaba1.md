
## 14.3 BLOWFISH

Blowfish is an algorithm of my design, intended for implementation on large microprocessors [1388,1389]. The algorithm is unpatented, and the C code in the back of this book is in the public domain. I designed Blowfish to meet the following criteria.

- 1. Fast. Blowfish encrypts data on 32-bit microprocessors at a rate of 26 clock cycles per byte.
- 2. Compact. Blowfish can run in less than 5K of memory.
- 3. Simple. Blowfish uses only simple operations: addition, XORs, and table lookups on 32-bit operands. Its design is easy to analyze which makes it resistant to implementation errors [1391].
- 4. Variably Secure. Blowfish's key length is variable and can be as long as 448 bits.

Blowfish is optimized for applications where the key does not change often, like a communications link or an automatic file encryption. It is significantly faster than DES implemented on 32-bit microprocessors with large data caches, such as the Pentium and the PowerPC. Blowfish is not suitable for applications, such as packet switching, with frequent key changes, or as a one-way hash function. Large memory requirement makes it infeasible for smart card applications.

## Description of Blowfish

Blowfish is a 64-bit block cipher with a variable-length key. The algorithm consists of two parts: key expansion and decryption. Key expansion converts a key of up to 448 bits into several subkey arrays totaling 4168 bytes.

Data encryption consists of a simple function iterated 16 times. Each round consists of a key-dependent permutation, and a key-data-dependent substitution. All operations are additions and XORs on 32-bit words. The only additional operations are four indexed array lookups per round.

Blowfish uses a large number of subkeys. The subkeys must be precomputed before any encryption or decryption.

$P_1, P_2, \dots, P_{18}$

Four 32-bit S-boxes have 256 entries each:

$S_{1,0}, S_{1,1}, \dots, S_{1,255}$
$S_{2,0}, S_{2,1}, \dots, S_{2,255}$
$S_{3,0}, S_{3,1}, \dots, S_{3,255}$
$S_{4,0}, S_{4,1}, \dots, S_{4,255}$

The exact method used to calculate these subkeys will be described later in this section.

![](img/e08b4270295105438dabfbd9a81857bf_359_0.png)

Blowfish is Feistel network [see Section 14.10] consisting of 16 rounds. The input is a 64-bit data element, x. To encrypt:

- Divide x into two 32-bit halves: $x_L, x_R$
- For $i = 1$ to 16:
  - $x_L = x_L \oplus P_i$
  - $x_R = F[x_L] \oplus x_R$
  - Swap $x_L$ and $x_R$
  - Swap $x_L$ and $x_R$ [Undo the last swap].
  - $x_R = x_R \oplus P_{17}$
  - $x_L = x_L \oplus P_{18}$
- Recombine $x_L$ and $x_R$

## CHAPTER 14 Still Other Block Ciphers

![](img/e08b4270295105438dabfbd9a81857bf_360_0.png)

Figure 14.3 Function F.

Function F is as follows (see Figure 14.3):
Divide $x_i$ into four eight-bit quaternaries:
$a, b, c,$ and $d$
$F(x_i) = ((S_{ia} + S_{jb}) \oplus S_{kc}) + S_{kd} \bmod 2^{32}$

Decryption is exactly as the encryption, except that $P_1, P_2, \dots, P_{18}$ are used in the reverse order.
Implementations of Blowfish that require the fastest speeds should unroll the loop and ensure that all subkeys are stored in cache. See [568] for details.
The subkeys are calculated using the Blowfish algorithm. The exact method follows.

- (1) Initialize first the P-array and then the four S-boxes, in order, with a fixed string. This string consists of the hexadecimal digits of $\pi$.
- (2) XOR $P_1$ with the first 32 bits of the key, XOR $P_2$ with the second 32-bits of the key, and so on for all subkeys of the key [up to $P_{18}$]. Repeatedly cycle through the key bits until the entire P-array has XORed with key.
- (3) Encrypt the all-zero string with the Blowfish algorithm, using the subkeys described in steps [1] and [2].
- (4) Replace $P_1$ and $P_2$ with the output of step (3).
- (5) Encrypt the output of step (3) using the Blowfish algorithm with the modified subkeys.
- (6) Replace $P_4$ and $P_5$ with the output of step (5).
- (7) Continue the process, replacing all elements of P-array, and then all S-boxes, with the output of step (6).

## 14.4 SAFER

In total, 521 iterations are required to generate all subkeys. Applications can store the subkeys—there is no need to execute this derivation multiple times.

## Security of Blowfish

Sergio Vaud examined Blowfish with known S-boxes and r rounds; a differential attack can recover the P-array with $2^{47}$ plaintexts. For certain weak keys that generate identical S-boxes (the odds of getting them randomly are 1 in $2^{64}$), the same attack requires only $2^{21}$ plaintexts to recover the array. With unknown S-boxes this attack can detect whether a weak key is used but cannot determine what (neither the S-boxes nor the P-array). This attack only works against reduced-round variants; is completely against 16-round Blowfish. Of course, the discovery of weak keys is significant, even though they seem impossible to exploit. To be safe, do not implement Blowfish with a reduced number of rounds. I don't think this is necessary, though I know of no successful cryptanalysis against Blowfish. Kent has incorporated Blowfish in Windows and PGP.

## 14.4 SAFER

SAFER-64 stands for Secure And Fast Encryption Routine with a Key of 64 bits. James Massey produced this proprietary algorithm for Singapore. The government is planning to use this algorithm—with a 128-bit key—for a variety of applications. There are no patent, copyright or other restrictions on its use. The algorithm has a key size of 64 bits. It is not a Feistel network like DES (see 14.10), but an iterated block cipher: the function is applied for some number of rounds. Each round uses 64-bit subkeys, and the algorithm operates on bytes.

## Description of SAFER K-64

The plaintext is divided into eight byte-length subblocks: $B_1, B_2, \dots, B_8$. Then subblocks go through $r$ rounds. Finally, an output transformation is applied to the subblocks. Each round uses two subkeys: $K_{2i-1}$ and $K_{2i}$.

Figure 14.4 shows one round of SAFER K64. First, subblocks are either XORed and added with bytes of subkey $K_{2i-1}$. Then the eight subblocks are subjected to one of two nonlinear transformations:

$y = 3x \pmod{257}. (\text{If } x = 128, \text{ then } y = 0)$
$y = \log_3 x. (\text{If } x = 0, \text{ then } y = 128)$

These are operations in the finite field GF(257), and 3 is a primitive element in that field. In practical implementations of SAFER-K-64, it is quicker to implement this in a lookup table to calculate results all the time. The subblocks are either XORed or added with bytes of subkey $K_i$. The results of this operation are fed through three layers of linear operations designed to increase the avalanche effect. Each operation is called a Pseudo-Hadamard Transform (PHT). If the inputs to a PHT are $a_i$ and $a_j$, then the outputs are:

$b_i = (2a_i + a_j) \pmod{256}$
$b_j = (a_i + a_j) \pmod{256}$

After $r$ rounds, there is a final output transformation. This is the same as the first of each round. $B_1, B_3, B_5,$ and $B_7$ are XORed with the corresponding bytes of the last subkey, $B_2, B_4, B_6,$ and $B_8$ are added to the corresponding bytes of the subkey. The result is the ciphertext.

| Round Input (8 Bytes) | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---|---|---|---|---|---|---|---|---|
| xor | add | add | xor | xor | add | add | xor | $K_{2i-1}$ |
| $3^{(l)}$ | $\log_3$ | $\log_3$ | $3^{(l)}$ | $3^{(l)}$ | $\log_3$ | $\log_3$ | $3^{(l)}$ | |
| add | xor | xor | add | add | xor | xor | add | $K_{2i}$ |
| | 2-PHT | | 2-PHT | | 2-PHT | | 2-PHT | |
| | | 2-PHT | | 2-PHT | | 2-PHT | | |
| | | | 2-PHT | | | 2-PHT | | |
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
| Round Output (8 Bytes) | | | | | | | | |

Figure 14.4 One round of SAFER.
