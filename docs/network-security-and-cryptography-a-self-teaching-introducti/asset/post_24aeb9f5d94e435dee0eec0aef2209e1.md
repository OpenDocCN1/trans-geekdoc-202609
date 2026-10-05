
# 7.8 EXERCISES

- 1. What is the strength of RSA? If the modulus used in RSA has very small prime factors, will the RSA implementation be secure? Justify your answer.

- 2. What are the different kinds of attacks possible against RSA? Explain the Common Modulus Attack on RSA.

- 3. In RSA, if repeated encryption using public key $e$ results in decryption of the message, what is the likely cause?

- 4. In RSA, suppose private key $d$ is leaked out; is it safe to generate the new keys without changing the modulus $n$?

- 5. Suppose more than one block of RSA cipher-text are available to an adversary. Suppose it is known that one of the blocks has a common factor with modulus $n=pq$. Does it help the adversary in breaking the cipher in any way?

- 6. Given a prime number $p$, its primitive root $g$, and integer $x$ ($1 < x < \Phi(p)$), why is it easier to compute $y = g^x \pmod p$, but difficult to compute discrete logarithm $x = \log_g y \pmod p$?

- 7. What is the strength of the Diffie-Hellman Key Exchange Algorithm? If the prime modulus used in the algorithm is very small, will the key exchange be secure?

- 8. What is a Clogging Attack on a Diffie-Hellman Key Exchange? Suggest a suitable countermeasure.

- 9. What is the strength of the ECC-based Encryption Scheme? Explain how to increase the major security level.

- 10. What is the major advantage offered by ECC-based cryptography vis-à-vis existing Public Key Schemes?

- 11. Explain RSA for Data Confidentiality. Perform RSA Encryption Decryption for the following set of data:

    - A. $p=3; q=11; e=7; M=5$
    - B. $p=5; q=11; e=3; M=9$
    - C. $p=7; q=11; e=17; M=B$
    - D. $p=11; q=13; e=11; M=7$
    - E. $p=17; q=31; e=7; M=2$

- 12. In RSA, if cipher-text $C=10$, $e=5$ and $n=35$, determine private key $d$.

- 13. In RSA, if $e=31$ and $n=3599$, determine private key $d$.

- 14. A plaintext is encrypted using $(e, n)$ and $(f, n)$ public keys, generating cipher-texts $C$ and $C'$, respectively, where $GCD(e, f)=1$. Is it possible to determine $M$ without determining $q > (n)$? If yes, how? If no, why not?

- 15. Explain the Diffie-Hellman Key-Exchange Algorithm. Let $p=353$ be the prime number and $\alpha=3$ be its primitive root. Let the secret keys of $A$ and $B$ be $X_a=97$ and $X_b=233$. Compute the following:

    - A. Public keys of $A$ and $B$
    - B. Common Secret Key

- 16. Users $A$ and $B$ use a Diffie-Hellman key exchange using prime $q=71$ and primitive root $\alpha=7$.

    - A. User $A$ has private key $X_a=5$; what is $A$'s public key $Y_a$?
    - B. User $B$ has private key $X_b=12$; what is $B$'s public key $Y_b$?
    - C. What is the shared secret key?

- 17. Consider a Diffie-Hellman scheme with a common prime $q=11$ and primitive root $\alpha=2$.

    - A. Verify that 2 is a primitive root of 11.
    - B. If user $A$ has Public Key $Y_a=9$, what is $A$'s private key $X_a$?
    - C. If user $B$ has Public Key $Y_b=3$, what is $B$'s private key $X_b$?
    - D. What is the shared secret key of $A$ and $B$?

- 18. Explain the “Man-in-the-Middle Attack” on a Diffie-Hellman Key-Exchange Algorithm.

- 19. With the following parameters, implement the ElGamal Encryption/Decryption scheme:
  Prime Number = 19
  Primitive Root of $p = g = 3$
  Suppose user “A” chooses private key $x = 7$
  And message to be sent by User “B” to User “A” $M = 12$
  Random number chosen by user “B” for encryption $= k = 3$
  Determine:

    i. Public Key $y$ of “A”
    ii. Cipher-text created by the sender “B”
    iii. Show how the plaintext is extracted from the cipher-text by User “A.” 

- 20. What is Elliptic Curve Cryptography? Explain Encryption/Decryption in this context.

- 21. With the following parameters, design an ECC Key Exchange Scheme:
  Elliptic Curve Set: $E_{11}$ (1, 1)
  Base Point: $G = (1, 6)$
  Order of Base Point: $n = 14$
  Suppose user “A” chooses private key $x = 3$
  And User “B” chooses private key $y = 5$
  Determine:

    i. Public keys of $A$ and $B$
    ii. Shared secret key
