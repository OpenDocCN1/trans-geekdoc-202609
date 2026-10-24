# Dedicated MAC Designs

You’ve seen how to recycle hash functions and block ciphers to build PRFs that are secure as long as their underlying hash or cipher is secure. Schemes such as HMAC and CMAC simply combine available hash functions or block ciphers to yield a secure PRF or MAC. Reusing available algorithms is convenient, but is it the most efficient approach?

Intuitively, PRFs and MACs should require less work to be secure than unkeyed hash functions—their use of a secret key prevents attackers from playing with the algorithm because they don’t have the key. Also, PRFs and MACs expose only a short tag to attackers, unlike block ciphers, which expose a ciphertext as long as the message. Hence, PRFs and MACs shouldn’t need the maximum power of hash functions or block ciphers—this is the point of dedicated design, that is, algorithms created solely to serve as PRFs or MACs.

The sections that follow focus on two such algorithms: Poly1305 and SipHash. I’ll explain their design principles and why they’re (most likely) secure.

# Poly1305

The Poly1305 algorithm (pronounced poly-thirteen-o-five) was designed in 2005 by Daniel J. Bernstein (creator of the Salsa20 stream cipher from Chapter 5 and the ChaCha cipher that inspired the BLAKE and BLAKE2 hash functions from Chapter 6). Poly1305 is optimized to be superfast on modern CPUs, and as I write this, it’s one of the algorithms supported in TLS 1.3 and in OpenSSH, among many other applications. Unlike Salsa20, the design of Poly1305 is built on techniques dating back to the 1970s—namely, universal hash functions and the Wegman–Carter construction.

# Universal Hash Functions

The Poly1305 MAC uses a universal hash function. Such a hash function is weaker than a cryptographic hash function but much faster. Universal hash functions don’t have to be collision resistant, for example.

Like a PRF, a universal hash is parameterized by a secret key: given a message, M, and key, K, we’ll write UH(K, M) for the output of a universal hash function denoted UH. A universal hash function has only one security requirement: for any two messages M1 and M2, and a random key K, the probability that UH(K, M1) equals UH(K, M2) must be negligible. Unlike a PRF, a universal hash doesn’t need to be pseudorandom; there simply should be no pair (M1, M2) that gives the same hash for many different keys. Because their security requirements are easier to satisfy, universal hash functions require fewer operations and are considerably faster than PRFs.

You can use a universal hash as a MAC to authenticate no more than one message, however. For example, consider the universal polynomial-evaluation hash used in Poly1305. (See the seminal 1974 article “Codes Which Detect Deception” by Edgar Gilbert, Jessie MacWilliams, and Neil