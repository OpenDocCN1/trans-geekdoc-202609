
# Chapter 4 Essential Cryptographic Tools | 133

message is divided into chunks of 512-bit blocks, viewed as 16 32-bit words. If the need occurs, the message is padded so that its length is divisible by 512. When processing the first 512-bit input, the output is initialized to a set of eight 32-bit initial values. When processing subsequent 512-bit inputs, the output is initialized to the set of four 32-bit values obtained from the previous calculations.

Thus, it is enough to understand how 512-bit input is transferred to a 128-bit hash. The input is divided into 16 32-bit words, by $W_0, ..., W_{15}$. The set of 16 words is expanded to the set of 64 words $M_{i,j}$, $1 \leq i \leq 4, 0 \leq j \leq 15$, according to the following rule:

$M_{1,j} = W_j, M_{2,j} = W_k, k = (Sj + 1) \pmod{16},$

$W_{3,j} = W_k, k = (3j + 5) \pmod{16}, W_{4,j} = W_k, k = 7j \pmod{16}$ (4.1773)

Since there are 64 words, there are 64 rounds. The flowchart for MD5 is shown in Figure 4.18.
The transformation of a message block consists of four stages or rounds. Each round is composed of 16 similar sub-rounds using every one of 16 sub-messages; they rely on non-linear functions $F_1, ..., F_4$ operating on bits as follows:

$F_1(B, C, D) = (B \wedge C) \vee (B \wedge D), F_2(B, C, D) = (B \wedge D) \vee (C \wedge D)$ (4.1774)

$F_3(B, C, D) = B \oplus C \oplus D, F_4(B, C, D) = C \oplus (B \vee D)$

Here, $\wedge, \vee, \oplus$ are XOR, OR, NOT bitwise operations.

![](img/d52d985b4b3970b396f9b7f6d2aa3d8e_179_0.png)

**Figure 4.18** Flow chart for MD5. Own graphics. Source: Wikipedia.

The i,j-th round, i = 1, ..., 4, j = 0, ..., 15, proceeds as follows:

$A_{i,j} = D_{i,j-1}, C_{i,j} = B_{i,j-1}, D_{i,j} = C_{i,j-1},$
$B_{i,j} = B_{i,j-1} + K_j + W_j$

Here ROTL () is left rotation of W by one bit.
Some examples of MD5 hashes are shown in Eqs (4.176)-(4.178).

Mary had a little lamb.
$\downarrow$
ca964b1677d5476ea11eed1e1837c342 (4.176)

Mary had a little lamb
$\downarrow$
e946adb454299def2071880d301364d4 (4.177)

Mary had a little lamb
$\downarrow$
ecb0d9a47d9a7379d6a070fb7216ff4 (4.178)

These examples clearly show that “small” changes in the input make the output unrecognizable, intended.
At present, MD5 is broken and should not be used in practice; see Wang and Yu (2005).
Yet, it is a prototype for other, more complicated, and secure algorithms.

## 4.10.3 SHA-256

SHA-256 is a member of the SHA2 family. It converts a variable-length message into fixed-length output of 256 bits (=32 bytes). MD5 and SHA-256 operate along similar lines. Before, it is important to understand how 512-bit input is transferred to a 256-bit hash. The input is divided into 16 32-bit words, denoted by $W_0, ..., W_{15}$. The set of 16 words is extended to the set of 64 words according to rule:

$W_j = \sigma_1(W_{j-2}) + W_{j-7} + \sigma_0(W_{j-15}), 16 \le j \le 63.$ (4.179)

$\sigma_0(W) = ROTR^7(W) + ROTR^{18}(W) + SHR^3(W),$ (4.180)

$\sigma_1(W) = ROTR^{17}(W) + ROTR^{19}(W) + SHR^{10}(W),$

where ROTR () is right rotation of W by one bit, SHR () is left shift of W by one bit. Since there are 64 words, there are 64 rounds, like MD5. Given a word $W_i$ and a constant $K_i$, the flowchart for SHA-256 is shown in Figure 4.19; see e.g., Barker (2002); Sanadhya and Sarkar (2008).

![](img/d52d985b4b3970b396f9b7f6d2aa38e_181_0.png)

**Figure 4.19** Flow chart for SHA2. Own graphics. Source: Wikipedia.

The j-th round proceeds as follows:

$A_j = \Sigma_0(A_{j-1}) + F(A_{j-1}, B_{j-1}, C_{j-1}) + H_{j-1} + \Sigma_1(E_{j-1}) + G(E_{j-1}, F_{j-1}, G_{j-1}) + K_j + W_j,$
$B_j = A_{j-1}, C_j = B_{j-1}, D_j = C_{j-1},$
$E_j = D_{j-1} + H_{j-1} + \Sigma_1(E_{j-1}) + G(E_{j-1}, F_{j-1}, G_{j-1}) + K_j + W_j,$
$F_j = E_{j-1}, G_j = F_{j-1}, H_j = G_{j-1}.$ (4.181)

Here
$F(A, B, C) = (A \wedge B) \oplus (\neg A \wedge C),$
$G(A, B, C) = (A \wedge B) \oplus (B \wedge C) \oplus (C \wedge A),$
$\Sigma_0(W) = ROTR^2(W) \oplus ROTR^{13}(W) \oplus ROTR^{22}(W),$
$\Sigma_1(W) = ROTR^6(W) \oplus ROTR^{11}(W) \oplus ROTR^{25}(W)$. (4.182)

Some examples of SHA-256 are shown in Eqs (4.183)-(4.185).

Mary had a lamb.
$\downarrow$
d2fc16a1f51a653aa01964ef9c923336e10653fec195f493548b321890eb197 (4.183)

Mary had a lamb
$\downarrow$
efe473564cb63a7bf0255dd691ef0ae0ac096c03ab408375b9094e326c22ad976 (4.184)

Mary had a lamb!
$\downarrow$
72debc1ca1859dabe1c1e9547ed4734d56ef85ec87ae87ea3f63371cf4a79e (4.185)

Once again, we see that "small" changes in the input make the output unrecognizable, as intended.

It is essential to understand that, in some cases, the SHA-256 algorithm can interpret the input in two different ways: (a) as text; (b) as hexadecimal. The numbers are entirely different, of course. In Eqs (4.186) and (4.187), we show some examples of SHA-256 applied to text strings vs. hexadecimal numbers.

efe473564cb63a7bf0255dd691ef0ae0ac096c03ab408375b9094e326c22ad976
$\downarrow$
87fc72ab0790e80e19af68a3765928033de93568be02dfed04fe5 (4.186)

efe473564cb63a7bf0255dd691ef0ae0ac096c03ab408375b9094e326c22ad976
$\downarrow$
a345ea180726e235ea2aea4b16ce1019931eb897003e2a419c947619426d (4.187)

We note that in the Bitcoin protocol, and by extension, most crypto protocols, which predominantly use hexadecimal numbers rather than strings, are always hashed twice:
$x \rightarrow SHA256(x) \rightarrow z = SHA256(y)$. (4.188)

The second hashing is used as a safety mechanism against the so-called "length-extension" attack; see Ferguson et al. (2010). Length extension allows an attacker who knows the length of message $m1$ and $Hash(m1)$ to calculate $Hash(m1||m2)$ of the message $m1$ concatenated with an attacker-chosen message $m2$, without knowing $m1$. Algorithms, relying on Merkle–Damgård construction, as MD5, SHA-1, and SHA-2, can be vulnerable against such attack. The new SHA-3 algorithms are secure in this respect.

## 4.10 RIPEMD-160

RIPEMD-160 was developed in 1992 and improved in 1996 by Hans Dobbert, Antoon Bosselaars and Bart Preneel. It converts a variable-length message into a fixed-length output of 160 bits (=20 bytes). This algorithm operates on 32-bit words. The flowchart for RIPEMD-160 is shown in Figure 4.20. For details, we refer to the original paper. Again, in the Bitcoin protocol, and by extension, many other crypto protocols, inputs are hashed twice so that:
$x \rightarrow y = SHA256(x) \rightarrow z = RIPEMD160(y)$. (4.189)

Some examples of RIPEMD-160 in action applied to a SHA256 of a hexadecimal number are shown in Eqs (4.190) and (4.191). We see that a small local change of the input — the first digit changed from a to b— results in a global change in the output.

a3e45a180726e235ea2aea4b16ce1019931eb897003e2a419c947619426d0
$\downarrow$ (4.190)

c37e0858495646805bf286a58d7cd307833bf86d334e5a180726e235ea2aea4b16ce1019931eb897003e2a419c947619426d0
$\downarrow$ (4.191)

![](img/d52d985b4b3970b3969b7f6d2aa3d8e_183_0.png)

**Figure 4.20** Flow chart for RIPEMD-160. Own graphics. Source: Wikipedia.

RIPEMD stands for RACE (Research in Advanced Communications Europe) Integrity Primitives Evaluation Message Digest.

# Blockchain and Distributed Ledgers: Mathematics, Technology, Economics

These examples clearly show that “small” changes in the input make the output unrecognizable, as intended.

## 4.11 Merkle trees and hash pointers

### 4.11.1 Merkle trees

The idea of a hash, combined with padding for efficiency, is beneficial for making data simultaneously immutable and compressed. Suppose we have a set of $N$ data blocks. We can pad them to make the total number of blocks a multiple of 2, say $2^n$. Then we can hash them sequentially until we reach the root node; see Merkle (1987). These constructs are called Merkle trees and are very useful in cryptography in general and blockchains in particular. In the next chapter, we show how Bitcoin and Ethereum protocols (as examples) use Merkle trees.

A Merkle tree is shown in Figure 4.21 (a). By construction, Merkle trees are tamper-proof, in a sense that any leaf along the path to the root will change the root itself beyond recognition. This property is helpful if, for example, we wish to verify that a particular data point, say a transaction, belongs to a particular Merkle tree. Using Merkle trees, we can verify membership of a transaction in a set in $O(\ln N)$. This is illustrated in Figure 4.21 (b).
