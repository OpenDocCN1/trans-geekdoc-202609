To authenticate the ciphertext, GCM uses a Wegman–Carter MAC (see Chapter 7), which XORs the value AES(K, N || 0) with the output of the universal hash function GHASH. In Figure 8-2, GHASH corresponds to the series of operations “⊗_H” followed by the XOR with len(A) || len(C), or the bit length of A (the associated data) followed by the bit length of C (the ciphertext).

You can thus express the authentication tag’s value as T = GHASH (H, A, C) ⊕ AES(K, N || 0), where H is the hash key, or authentication key. This key is determined as H = AES(K, 0), which is the encryption of the block equal to a sequence of null bytes (I didn’t include this step in Figure 8-2 for clarity).

> In GCM, GHASH doesn’t use K directly in order to ensure that if GHASH’s key is compromised, the master key K remains secret. Given K, you can get H by computing AES(K, 0), but you can’t recover K from that value, since K acts here as AES’s key.

GHASH uses polynomial notation to multiply each ciphertext block with the authentication key H. This use of polynomial multiplication makes GHASH fast in hardware and software, thanks, to a special polynomial multiplication instruction available in many common microprocessors (CLMUL, for carry-less multiplication).

Alas, GHASH is far from ideal. For one thing, its speed is suboptimal. Even when using the CLMUL instruction, the AES-CTR layer that encrypts the plaintext remains faster than the GHASH MAC. Second, GHASH is painful to implement correctly. In fact, even the experienced developers of the OpenSSL project, by far the most-used cryptographic piece of software in the world, got AES-GCM’s GHASH wrong. One commit had a bug in a gcm_ghash_clmul function that allowed attackers to forge valid MACs for the AES-GCM. (Fortunately, Intel engineers spotted the error before the bug entered the next OpenSSL release.)

# POLYNOMIAL MULTIPLICATION

While more complicated than classic integer arithmetic, polynomial multiplication is simpler for computers because there are no carries. Specifically, you can compute modular multiplication of polynomials, in a structure defined by a given polynomial (such structures are called quotient rings). For example, say you want to compute the product of the polynomials (1 + X + X²) and (1 + X²) modulo (1 +X + X³). You first multiply the two polynomials (1 + X + X²) and (1 + X²) as though you’re doing normal polynomial multiplication, thus giving the following (the two terms X² cancel each other out because you work with Boolean polynomials, a world wherein 1 + 1 = 0):

```
(1 + X + X²) ⊗ (1 + X²) = 1 + X + X³ + X⁴
```