the preceding attack by making it possible to authenticate multiple messages with the same key, $K_1$.

To recap, the Wegman–Carter construction **UH**($K_1$, $M$) + **PRF**($K_2$, $N$) gives a secure MAC if you assume the following:

+   - **UH** is a secure universal hash.
+   - **PRF** is a secure PRF.
+   - Each nonce $N$ is used only once for each key $K_2$.
+   - The output values of **UH** and **PRF** are long enough to ensure high enough security.

Now let’s see how Poly1305 leverages the Wegman–Carter construction to build a secure and fast MAC.

# Poly1305-AES

Poly1305 was initially proposed as Poly1305-AES, combining the Poly1305 universal hash with the AES block cipher. Poly1305-AES is much faster than HMAC-based MACs, or even than CMACs, since it computes only one block of AES and processes the message in parallel through a series of simple arithmetic operations.

Given 128-bit $K_1$, $K_2$, and $N$ and the message $M$, Poly1305-AES returns the following:

$$\mathbf{Poly1305}(K_1, M) + \mathbf{AES}(K_2, N) \bmod 2^{128}$$

The mod $2^{128}$ reduction ensures that the result fits in 128 bits. Poly1305 parses the message $M$ as a sequence of 128-bit blocks ($M_1$, $M_2$, …, $M_n$) and appends a 129th bit to each block’s most significant bit to make all blocks 129 bits long. (If the last block is smaller than 16 bytes, it’s padded with a 1 bit followed by 0 bits before the final 129th bit.) Next, Poly1305 evaluates the polynomial to compute the following:

$$\mathbf{Poly1305}(K_1, M) = M_1K_1^n + M_2K_1^{n-1} + \cdots + M_nK_1 \bmod 2^{130} - 5$$

The result of this expression is an integer that’s at most 129 bits long. When you add this to the 128-bit value **AES**($K_2$, $N$), the result is reduced modulo $2^{128}$ to produce a 128-bit MAC.

> > **NOTE**  *I described the Wegman–Carter as using a PRF, but AES isn’t a PRF, it’s a pseudorandom permutation (PRP). However, that doesn’t matter because the Wegman–Carter construction works well with PRPs and PRFs. This is because if you’re given a function that’s either a PRF or a PRP, it’s hard to determine whether it’s a PRF of a PRP just by looking at the function’s output values. In other words, distinguishing a PRP from a PRF is computationally hard.*

The security analysis of Poly1305-AES (see “The Poly1305-AES Message-Authentication Code” at https://cryp.to/mac/poly1305-20050329.pdf) shows