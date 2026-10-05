
# MODERN SYMMETRIC CIPHERS $\cdot$ 267

* The following sequence of operations is performed in each round:
1. Multiply $X_1$ and the first sub-key
2. Add $X_2$ and the second sub-key
3. Add $X_3$ and the third sub-key
4. Multiply $X_4$ and the fourth sub-key
5. XOR the results of Steps (1) and (3)
6. XOR the results of Steps (2) and (4)
7. Multiply the result of Step (5) with the fifth sub-key
8. Add the result of Steps (6) and (7)
9. Multiply the result of Step (8) with the sixth sub-key
10. Add the results of Steps (7) and (9)
11. XOR the results of Steps (1) and (9)
12. XOR the results of Steps (3) and (9)
13. XOR the result of Steps (2) and (10)
14. XOR the result of Steps (4) and (10)

* The output of each round comprises the 4 sub-blocks output by steps (11), (12), (13), and (14).

* At the output of each round, the inner 2 blocks are swapped, except in the last round.

* After the last round (Round 8), the 4 sub-blocks go through the final output transformation, with the application of 4 sub-keys $Z_1 (9)$, $Z_2 (9)$, $Z_3 (9)$, and $Z_4 (9)$.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_292_0.png)

$X_i$: 16-bit plaintext sub-block; $Y_i$: 16-bit cipher-text sub-block;
$Z_i$: 16-bit key sub-block

- $\oplus$: Bit-by-bit XOR of two 16-bit sub-blocks
- $+$: Addition modulo $2^{16}+1$ of two 16-bit sub-blocks
- $\odot$: Multiplication modulo ($2^{16}+1$) of two 16-bit sub-blocks. All zeroes sub-block is taken as $2^{16}=-1$. Multiplicative Inverse of 0 is taken as 0.

**FIGURE 6.23** Mathematical operations performed in each round of the IDEA Encryption process.

## 6.8.2 Generation of Sub-Keys in IDEA

IDEA encryption/decryption uses 52 sub-keys: Six sub-keys are in each round, and the remaining 4 sub-keys are used in the final output transformation. The sub-keys are generated from the overall 128-bit key as follows:

1. The first 128-bit overall key is divided into 8 16-bit sub-keys. The first six are used in the first round, and the remaining two are used as the first two sub-keys of the second round.
2. The 128-bit overall key is rotated left by 25 bits and again divided into 8 16-bit sub-keys. Four are used in the second round, and the remaining 4 are used in the third round.
3. Step (2) is repeated to generate all the remaining sub-keys.

### 6.8.2.1 Decryption Algorithm in IDEA

The decryption in IDEA is exactly same as encryption, except that the sub-keys are applied as follows:

* The sub-keys applied in decryption are in reverse order vis-à-vis the sub-keys applied in encryption.
* The sub-keys applied to the addition blocks in decryption are the additive inverse of the sub-keys applied to the addition blocks in encryption.
* The sub-keys applied to the multiplication blocks in decryption are multiplicative inverses of the sub-keys applied to the multiplication blocks in encryption.

### 6.8.2.2 Why is multiplication performed modulo ($2¹⁶ + 1$)?

* The decryption algorithm uses multiplicative inverses of the sub-keys used for multiplication operations in the encryption algorithm, each sub-key must have its multiplicative inverse defined.
* $2^{16} + 1 = 65537$ is a prime number. All integers $n$ ($0 < n < 2^{16}$) will have their multiplicative inverses defined except value zero.
* To ensure integer value zero also has its multiplicative inverse, this value is taken as $2^{16} = -1$, and $(-1) \mod(2^{16}+1)$ will be congruent to $2^{16}$. Thus, zero will have its multiplicative inverse.

## 6.8.2 Speed and Strength of IDEA

IDEA implementations are considered to be twice as fast as DES. IDEA's key size is 128, which is more than twice fast as DES. For a Brute Force attack, it would require the order of $2^{127}$ encryptions. For a chip that can test billions of keys per second, it would take $10^{13}$ years (longer than the age of universe) to recover the key. An array of $10^{14}$ such chips will require a day, but sufficient silicon does not exist on the earth. So, brute force is not the way to recover the key. The designers have done their best to make the algorithm immune to Differential Cryptanalysis. IDEA is claimed to be immune to cryptanalysis after the first four rounds.

### 6.8.3 IDEA Modes of Operation

It can work with any mode of Block Cipher Operation. It is used extensively for encryption of sensitive information such as banking data. It forms part of popular Good Privacy (PGP) used for e-mails.

## 6.9 ADVANCED ENCRYPTION STANDARD (AES)

The Advanced Encryption Standard (AES) is a Symmetric Cipher Standard that was adopted by the U.S. Government in 2002 as a replacement for-DES.

**Major Parameters:**

- Plaintext Block Size: 128 bits
- Key Size: 128 bits (also 192-bit and 256-bit key-size)
- Number of Rounds: 10/12/14 (depending on key-size; 10 rounds for 128-bit key-size, 12 rounds for 192-bit key-size, and 14 rounds for 256-bit key-size)
- Round-Key Size: 128 bits

### 6.9.1 Processing of Plaintext

- The processing of input plaintext is done in terms of blocks the size of 128 bits.
- 128-bit (16 bytes) input plaintext is depicted as a $4 \times 4$ matrix.
- The input plaintext matrix is copied into a State Matrix the size of $4 \times 4$ bytes. The State Matrix is transformed at each round of processing. After the final round of processing, the State Matrix is copied into an Output Matrix of the same size.
- 128-bit key is also depicted as a matrix the size of $4 \times 4$ bytes. The key is expanded into an array of 44 words of 32 bits each. Let the array of 44 expanded keywords be denoted as $W[0],...,W[43]$.
- The 44 keywords form 11 round keys, each round key comprising 44 words.
- Unlike its predecessor, the Decryption Algorithm in AES is different from the Encryption Algorithm. For each transformation algorithm used in encryption, an inverse algorithm exists is to be used in decryption to make encryption reversible. Also, the round keys in decryption are input in reverse order vis-à-vis encryption.
- There are 10 rounds of processing in encryption and decryption, as shown in Figure 6.24.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_296_0.png)

# MODERN SYMMETRIC CIPHERS • 273

128-bit Plaintext block output

![](img/d3b56042c756fbcc011ff06f1b9f53f0_297_0.png)

FIGURE 6.24 The 10 rounds of processing in encryption and decryption for AES of 128-bit.

## 128-Bit Cipher-Text Output

Each round comprises four stages of transformation except Round 10, which comprises 3 stages of transformation.

Thus, there are four kinds of transformations performed:

* Substitute Bytes
* Shift Rows
* Mix Columns
* Add Round-Key

Each of these four kinds of transformations have two algorithms: Forward and Inverse. The Forward Algorithm is used for encryption and the Inverse Algorithm is used for decryption. Various kinds of transformations are explained as follows:

### 1. Substitute Bytes:

It uses an S-Box to perform byte substitution. AES defines a $16 \times 16$ byte S-Box. It contains a permutation of all 256 possible 8-bit values. There are two types of transformations: (a) Forward Substitute Byte Transformation (b) Inverse Substitute Byte Transformation. The S-Box for Forward Substitute Byte Transformation is constructed as follows:

* Initialize the 256 bytes of the S-Box, with 8-bit values starting from 00, in an ascending sequence row by. The first row will contain 00, 01,.., 0F, the second row will contain 20, 21,.., 2F, and so on. The byte at row $x$ and column $y$ will contain $xy$.
* Transform the value of each byte to its multiplicative inverse in the finite field $GF(2^8)$ using the irreducible polynomial $m(x) = x^8 + x^4 + x^3 + x + 1$. The byte with value 00 is transformed to 0 itself.
* Let $\{b_0, b_1, b_2, b_3, b_4, b_5, b_6, b_7\}$ denote the 8 bits of a byte. Now, bits of each byte of the S-Box are substituted as follows:
b_i = b_i \oplus b_{(i+4)\mod 8} \oplus b_{(i+5)\mod 8} \oplus b_{(i+6)\mod 8} \oplus b_{(i+7)\mod 8} \oplus c_i$.
