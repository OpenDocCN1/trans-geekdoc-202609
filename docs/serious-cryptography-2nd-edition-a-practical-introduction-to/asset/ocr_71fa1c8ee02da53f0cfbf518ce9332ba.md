repetition of *rounds*, a short sequence of operations that’s weak on its own but strong in number. There are two main techniques to construct a round: substitution–permutation networks (as in AES) and Feistel schemes (as in DES). In this section, you’ll look at these techniques after viewing an attack that works when all rounds are identical to each other.

# A Block Cipher’s Rounds

Computing a block cipher boils down to computing a sequence of rounds. In a block cipher, a round is a basic transformation that’s simple to specify and to implement and is iterated several times to form the block cipher’s algorithm. This construction, consisting of a small component repeated many times, is simpler to implement and to analyze than a construction that consists of a single huge algorithm.

For example, a block cipher with three rounds encrypts a plaintext by computing *C* = **R**₃(**R**₂(**R**₁(*P*))), where the rounds are **R**₁, **R**₂, and **R**₃, and *P* is a plaintext. Each round should also have an inverse so it’s possible for a recipient to compute back to plaintext. Specifically, *P* = **iR**₁(**iR**₂(**iR**₃(*C*))), where **iR**₁ is the inverse of **R**₁, and so on.

The round functions—**R**₁, **R**₂, and so forth—are usually identical algorithms, but they are parameterized by a value we call the *round key*. Two round functions with two distinct round keys will behave differently and will therefore produce distinct outputs if fed with the same input.

We derive round keys from the main key, *K*, using a *key schedule* algorithm. For example, **R**₁ takes the round key **K**₁, **R**₂ takes the round key **K**₂, and so on.

Round keys should be different from each other in every round. For that matter, not all round keys should be equal to the key *K*; otherwise, all the rounds would be identical, and the block cipher would be less secure, as I’ll describe next.

# The Slide Attack and Round Keys

In a block cipher, no round should be identical to another round in order to avoid a *slide attack*. As Figure 4-1 shows, slide attacks look for two plaintext/ciphertext pairs (*P*₁, *C*₁) and (*P*₂, *C*₂), where *P*₂ = **R**(*P*₁) if **R** is the cipher’s round. When rounds are identical, the relation between the two plaintexts, *P*₂ = **R**(*P*₁), implies the relation *C*₂ = **R**(*C*₁) between their respective ciphertexts. Figure 4-1 shows three rounds, but the relation *C*₂ = **R**(*C*₁) will hold no matter the number of rounds, be it 3, 10, or 100. The problem is that knowing the input and output of a single round often helps recover the key. (For details, read the 1999 paper “Advanced Slide Attacks” by Alex Biryukov and David Wagner, available at *https://www.iacr.org/archive/eurocrypt2000/1807/18070595-new.pdf.*)