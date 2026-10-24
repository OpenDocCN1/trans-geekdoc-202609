TLS-protected connections that use RC4 because you need to trick the server into encrypting the same plaintext to many different recipients, or many times to the same recipient with different keys.

# Salsa20

Salsa20 is a simple, software-oriented cipher optimized for modern CPUs that has been implemented in numerous protocols and libraries, along with its variant, ChaCha. Its designer, respected cryptographer Daniel J. Bernstein, submitted Salsa20 to the eSTREAM competition in 2005 and won a place in eSTREAM’s software portfolio. Salsa20’s simplicity and speed have made it popular among developers.

Salsa20 is a counter-based stream cipher—it generates its keystream by repeatedly processing a counter incremented for each block. As Figure 5-10 shows, the Salsa20 core algorithm transforms a 512-bit block using a key (K), a nonce (N), and a counter value (Ctr). Salsa20 then adds the result to the original value of the block to produce a keystream block. (If the algorithm were to return the core’s permutation directly as an output, Salsa20 would be totally insecure because it could be inverted. The final addition of the initial secret state K || N || Ctr makes the transform key-to-keystream-block noninvertible.)

![](bbox=[0.25, 0.48, 0.35, 0.65])

Figure 5-10: Salsa20’s encryption scheme for a 512-bit plaintext block

# Using the Quarter-Round Function

Salsa20’s core permutation uses a function called quarter-round (QR), which transforms four 32-bit words (a, b, c, and d) as follows:

```
b = b ⊕ [(a + d) <<< 7]
c = c ⊕ [(b + a) <<< 9]
d = d ⊕ [(c + b) <<< 13]
a = a ⊕ [(d + c) <<< 18]
```