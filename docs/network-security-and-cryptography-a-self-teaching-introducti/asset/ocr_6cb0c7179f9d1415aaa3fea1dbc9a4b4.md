# MODERN SYMMETRIC CIPHERS · 245

+   If the result of the equation is 0 most of the time, then we assume that the value of $K[\gamma_1, \gamma_2, \dots, \gamma_e] = 0$; if the result is 1 most of the time, then we assume that the $K[\gamma_1, \gamma_2, \dots, \gamma_e] = 1$

+   By getting many such equations, we can deduce the bits of all sub-keys. For example, the cryptanalyst is able to establish the following: $K[3,17,23]=0$ and $K[3,23]=1$

From these equations, it can be deduced that bit-17 is likely to be 1.

+   The number of known plaintexts required to break the cipher complete is of the order of $2^{43}$

# 6.6.3 Differential Cryptanalysis vs. Linear Cryptanalysis

+   Differential Cryptanalysis requires plaintexts of the order of $2^{47}$ as Linear Cryptanalysis requires plaintexts of the order of $2^{43}$ to break the cipher. Therefore, Linear Cryptanalysis requires slightly less effort than a Differential Cryptanalysis Attack.

+   Differential Cryptanalysis requires Chosen Plaintexts whereas Linear Cryptanalysis requires Known Plaintexts. Obtaining Known Plaintexts is considered to be much easier than obtaining Chosen Plaintexts.

# 6.7 MULTIPLE DES

The Single DES was cracked in 1998 by the use of a special machine known as a “DES Cracker.” The attack took just three days to break the cipher. Since then, the single DES became virtually useless, so the designers came out with some solutions involving multiple blocks of DES used for encryption and decryption.

# 6.7.1 Double DES

The simplest form of multiple encryption/decryption has two encryption/decryption stages and two keys. Two blocks of DES with two 56-bit keys are used for encryption/decryption as follows:

# 6.7.1.1 Encryption

Figure 6.11 illustrates the two blocks of DES with two 56-bit keys that are used for encryption.