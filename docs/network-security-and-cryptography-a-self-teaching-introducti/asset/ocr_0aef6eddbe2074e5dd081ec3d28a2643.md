If no match is found, then go back to Step 4 and repeat Steps 4 to Steps 6 with the next value of key $K_2$

# 6.7.1.5 Effort Required for “Meet-in-the-Middle” Attack on Double DES

The effort required for the “Meet-in-the-Middle” attack can be divided into two parts:

+   1. Creation of $K_1$ vs. $X$ Table: The attacker needs to try all possible values of the 56-bit key $K_1$, so the effort required will be the order of $2^{56}$

+   2. Decryption of cipher-text using $K_2$ and finding a match with $X$ values stored in the table: On the average, the attacker may need to half the possible values of $K_2$ This requires an effort of order $rac{2^{56}}{2} = 2^{55}$

The total effort required will be of the order of $2^{56} + 2^{55}$ that is, the order of $2 	imes 2^{56} = 2^{57}$

This effort is slightly more than the effort required for breaking a Single DES by Brute Force Attack (i.e., $2^{55}$). Thus, Double DES is almost as insecure as Single DES.

# 6.7.2 Triple DES

It makes use of three blocks of DES with two 56-bit keys, $K_1$ and $K_2$ It is a relatively popular alternative to DES, and it has been adopted for the key management standards.

# 6.7.2.1 Encryption

For encryption, it makes use of both the Encrypt $(E)$ and Decrypt $(D)$ functions. For the same key value, the function $D$ is the inverse of function $E$ Figure 6.13 illustrates the three blocks of DES with two 56-bit keys $K_1$ and $K_2$ used for encryption.