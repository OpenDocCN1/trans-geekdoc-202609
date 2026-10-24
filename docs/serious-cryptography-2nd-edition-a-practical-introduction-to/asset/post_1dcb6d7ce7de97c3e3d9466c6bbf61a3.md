
plaintext block. Then CMAC sets K1 to (L << 1) if L’s most significant bit (MSB) is 0 and to (L << 1) ⊕ 87 if L’s MSB is 1. (The hexadecimal number 87, or 135 in decimal, is chosen for its mathematical properties when data blocks are 128 bits; a different value is needed when blocks aren’t 128 bits.) The key K2 is set to (K1 << 1) if K1’s MSB is 0 and to (K1 << 1) ⊕ 87 otherwise.

Given K1 and K2, CMAC works like CBC-MAC, except for the last block. If the final message chunk Mn is exactly the size of a block, CMAC returns E(K, Mn ⊕ Cn−1 ⊕ K1) as a tag, as Figure 7-3 illustrates.

![](img/ace4de942d037de8ea5835bc9fbe57cd_174_0.png)

Figure 7-3: The CMAC block cipher–based MAC construction when the message is a sequence of integral blocks

If Mn has fewer bits than a block, CMAC pads it with a 1 bit and 0s and returns E(K, Mn ⊕ Cn−1 ⊕ K2) as a tag, as in Figure 7-4.

![](img/ace4de942d037de8ea5835bc9fbe57cd_174_1.png)

Figure 7-4: The CMAC block cipher–based MAC construction when the last block of the message has to be padded with 1 bit and zeros to fill a block

The first case uses only K1 and the second only K2, but both use the main key K to process the message chunks that precede the final one.

Unlike the CBC encryption mode, CMAC doesn’t take an IV as a parameter and is deterministic: for the same key, CMAC always returns the same tag for a given message, M, because the computation of CMAC(M) isn’t randomized—and that’s fine because unlike encryption, MAC computation doesn’t have to be randomized to be secure, which eliminates the burden of having to choose random IV.

## Dedicated MAC Designs

You’ve seen how to recycle hash functions and block ciphers to build PRFs that are secure as long as their underlying hash or cipher is secure. Schemes such as HMAC and CMAC simply combine available hash functions or block ciphers to yield a secure PRF or MAC. Reusing available algorithms is convenient, but is it the most efficient approach?

Intuitively, PRFs and MACs should require less work to be secure than unkeyed hash functions—their use of a secret key prevents attackers from playing with the algorithm because they don’t have the key. Also, PRFs and MACs expose only a short tag to attackers, unlike block ciphers, which expose a ciphertext as long as the message. Hence, PRFs and MACs shouldn’t need the maximum power of hash functions or block ciphers—this is the point of dedicated design, that is, algorithms created solely to serve as PRFs or MACs.

The sections that follow focus on two such algorithms: Poly1305 and SipHash. I’ll explain their design principles and why they’re (most likely) secure.

## Poly1305

The Poly1305 algorithm (pronounced poly-thirteen-o-five) was designed in 2005 by Daniel J. Bernstein (creator of the Salsa20 stream cipher from Chapter 5 and the ChaCha cipher that inspired the BLAKE and BLAKE2 hash functions from Chapter 6). Poly1305 is optimized to be superfast on modern CPUs, and as I write this, it’s one of the algorithms supported in TLS 1.3 and in OpenSSH, among many other applications. Unlike Salsa20, the design of Poly1305 is built on techniques dating back to the 1970s—namely, universal hash functions and the Wegman–Carter construction.

## Universal Hash Functions

The Poly1305 MAC uses a universal hash function. Such a hash function is weaker than a cryptographic hash function but much faster. Universal hash functions don’t have to be collision resistant, for example.

Like a PRF, a universal hash is parameterized by a secret key: given a message, M, and key, K, we’ll write UH(K, M) for the output of a universal hash function denoted UH. A universal hash function has only one security requirement: for any two messages M1 and M2, and a random key K, the probability that UH(K, M1) equals UH(K, M2) must be negligible. Unlike a PRF, a universal hash doesn’t need to be pseudorandom; there simply should be no pair (M1, M2) that gives the same hash for many different keys. Because their security requirements are easier to satisfy, universal hash functions require fewer operations and are considerably faster than PRFs.

You can use a universal hash as a MAC to authenticate no more than one message, however. For example, consider the universal polynomial-evaluation hash used in Poly1305. (See the seminal 1974 article “Codes Which Detect Deception” by Edgar Gilbert, Jessie MacWilliams, and Neil Sloane for more on this notion.) This kind of polynomial-evaluation hash is parameterized by a prime number, p, and takes as input a key consisting of two numbers, R and K, in the range [1, p) and a message, M, consisting of n blocks (M₁, M₂, . . . , Mₙ). You then compute the output of the universal hash as follows:

**UH**(R, K, M) = R + M₁K + M₂K² + M₃K³ + . . . + MₙKⁿ mod p

In this equation, the plus sign (+) denotes the addition of positive integers, Kⁱ is the number K raised to the power i, and “mod p” denotes the reduction modulo p of the result (that is, the remainder of the division of the result by p; for example, 12 mod 10 = 2, 10 mod 10 = 0, 8 mod 10 = 8, and so on).

Because you want the hashing operation to be as fast as possible, universal hash-based MACs often work with message blocks of 128 bits and with a prime number, p, that’s slightly larger than 2¹²⁸, such as 2¹²⁸ + 51. The 128-bit width allows for very fast implementations by efficiently using the 32- and 64-bit arithmetic units of common CPUs.

## Security Limitations

Universal hashes have one weakness: because a universal hash securely authenticates only one message, an attacker could break the preceding polynomial-evaluation MAC by requesting the tags of only two messages. Specifically, they could request the tag for a message where all blocks are zero—M₁ = M₂ = . . . = 0—to obtain the tag UH(R, K, 0) = R, thus finding the secret value R. Alternatively, they could request the tags for a message where M₁ = 1 and where M₂ = M₃ = . . . = 0 (whose tag is T = R + K), which allows them to find K by subtracting R from T. Now the attacker knows the whole key (R, K) and can forge MACs for any message.

Fortunately, there’s a way to go from single-message security to multi-message security.

## Wegman–Carter MACs

The trick to authenticating multiple messages using a universal hash function arrived thanks to IBM researchers Mark Wegman and Lawrence Carter and their 1981 paper “New Hash Functions and Their Use in Authentication and Set Equality.” The Wegman–Carter construction builds a MAC from a universal hash function and a PRF, using two keys, K₁ and K₂, and it returns

**MAC**(K₁, K₂, N, M) = **UH**(K₁, M) + **PRF**(K₂, N)

where N is a nonce that must be used at most once for each key, K₂, and where PRF’s output is as large as that of the universal hash function UH. By adding these two values, PRF’s strong pseudorandom output masks the cryptographic weakness of UH. You can see this as the encryption of the universal hash’s result, where the PRF acts as a stream cipher and prevents the preceding attack by making it possible to authenticate multiple messages with the same key, $K_1$.

To recap, the Wegman–Carter construction **UH**($K_1$, $M$) + **PRF**($K_2$, $N$) gives a secure MAC if you assume the following:

- **UH** is a secure universal hash.
- **PRF** is a secure PRF.
- Each nonce $N$ is used only once for each key $K_2$.
- The output values of **UH** and **PRF** are long enough to ensure high enough security.

Now let’s see how Poly1305 leverages the Wegman–Carter construction to build a secure and fast MAC.

## Poly1305-AES

Poly1305 was initially proposed as Poly1305-AES, combining the Poly1305 universal hash with the AES block cipher. Poly1305-AES is much faster than HMAC-based MACs, or even than CMACs, since it computes only one block of AES and processes the message in parallel through a series of simple arithmetic operations.

Given 128-bit $K_1$, $K_2$, and $N$ and the message $M$, Poly1305-AES returns the following:

$$\mathbf{Poly1305}(K_1, M) + \mathbf{AES}(K_2, N) \bmod 2^{128}$$

The mod $2^{128}$ reduction ensures that the result fits in 128 bits. Poly1305 parses the message $M$ as a sequence of 128-bit blocks ($M_1$, $M_2$, …, $M_n$) and appends a 129th bit to each block’s most significant bit to make all blocks 129 bits long. (If the last block is smaller than 16 bytes, it’s padded with a 1 bit followed by 0 bits before the final 129th bit.) Next, Poly1305 evaluates the polynomial to compute the following:

$$\mathbf{Poly1305}(K_1, M) = M_1K_1^n + M_2K_1^{n-1} + \cdots + M_nK_1 \bmod 2^{130} - 5$$

The result of this expression is an integer that’s at most 129 bits long. When you add this to the 128-bit value **AES**($K_2$, $N$), the result is reduced modulo $2^{128}$ to produce a 128-bit MAC.

> > **NOTE**  *I described the Wegman–Carter as using a PRF, but AES isn’t a PRF, it’s a pseudorandom permutation (PRP). However, that doesn’t matter because the Wegman–Carter construction works well with PRPs and PRFs. This is because if you’re given a function that’s either a PRF or a PRP, it’s hard to determine whether it’s a PRF of a PRP just by looking at the function’s output values. In other words, distinguishing a PRP from a PRF is computationally hard.*

The security analysis of Poly1305-AES (see “The Poly1305-AES Message-Authentication Code” at https://cryp.to/mac/poly1305-20050329.pdf) shows
