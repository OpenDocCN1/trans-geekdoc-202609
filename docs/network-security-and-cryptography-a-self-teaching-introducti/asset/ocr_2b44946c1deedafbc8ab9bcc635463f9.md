# 7.8 EXERCISES

+   1. What is the strength of RSA? If the modulus used in RSA has very small prime factors, will the RSA implementation be secure? Justify your answer.

+   2. What are the different kinds of attacks possible against RSA? Explain the Common Modulus Attack on RSA.

+   3. In RSA, if repeated encryption using public key $e$ results in decryption of the message, what is the likely cause?

+   4. In RSA, suppose private key $d$ is leaked out; is it safe to generate the new keys without changing the modulus $n$?

+   5. Suppose more than one block of RSA cipher-text are available to an adversary. Suppose it is known that one of the blocks has a common factor with modulus $n=pq$. Does it help the adversary in breaking the cipher in any way?

+   6. Given a prime number $p$, its primitive root $g$, and integer $x$ ($1 < x < \Phi(p)$), why is it easier to compute $y = g^x \pmod p$, but difficult to compute discrete logarithm $x = \log_g y \pmod p$

+   7. What is the strength of the Diffie-Hellman Key Exchange Algorithm? If the prime modulus used in the algorithm is very small, will the key exchange be secure?

+   8. What is a Clogging Attack on a Diffie-Hellman Key Exchange? Suggest a suitable countermeasure.

+   9. What is the strength of the ECC-based Encryption Scheme? Explain how to increase the major security level.

+   10. What is the major advantage offered by ECC-based cryptography visà-vis existing Public Key Schemes?