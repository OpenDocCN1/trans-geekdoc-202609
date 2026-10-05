# CHAPTER 13 Other Block Ciphers

(2) Add $X_2$ and the second subkey.

(3) Add $X_3$ and the third subkey.

(4) Multiply $X_4$ and the fourth subkey.

Finally, the four sub-blocks are reattached to produce the ciphertext.

Creating the subkeys is also easy. The algorithm uses 52 them [six for each of the eight rounds and four more for the output transformation]. First, the 128-bit key is divided into 16-bit subkeys. The first eight subkeys for the algorithm [six for the first round, and the first two for the second round]. Then, the key is rotated 25 bits to the left and again into eight subkeys. The first four are used in round 2, the last four are used in round 3. The key is rotated 25 bits to the left for the next eight subkeys, and so on until the end of the encryption.

Decryption is exactly the same, except the subkeys are reversed and slightly different. The decryption subkeys are either additive or multiplicative inverses of the encryption subkeys. [For purposes of IDEA, the all-zero subkey is considered to represent $2^6-1$ for modulo $2^6+1$, thus the multiplicative inverse of 0 is 1] Calculating these takes some time, but you only have to do it once for each decryption key. Table 13.4 shows the encryption subkeys and the corresponding decryption subkeys.

# Speed of it

Current implementations of IDEA are twice as fast as DES. IDEA on a 33 megahertz machine produces 80 kilobits per second, and 2400 kilobits per second on a 66 megahertz 486 machine. You might think IDEA should be faster, but multiplications aren't cheap. To multiply two 32-bit numbers on a 486 requires 40 cycles (10 on a Pentium).

A VLSI implementation of PES encrypt at 55 megabits per second at 25 megahertz [208,399]. Another VLSI chip developed at ETH Zurich, consisting of 251,000 transistors on a chip 107.8 square millimeters, encrypt data uses the

Table 13.4

# IDEA Encryption and Decryption Subkeys

| Round | Encryption Subkeys | Decryption Subkeys |
|---|---||
| 1st | $Z_1^{(1)} Z_2^{(1)} Z_3^{(1)} Z_4^{(1)}$ | $Z_9^{(9)} Z_8^{(9)} Z_7^{(9)} Z_8^{(8)}$ |
| 2nd | $Z_5^{(2)} Z_6^{(2)} Z_7^{(2)} Z_8^{(2)}$ | $Z_1^{(8)} Z_2^{(8)} Z_3^{(7)} Z_4^{(7)}$ |
| 3rd | $Z_1^{(3)} Z_2^{(3)} Z_3^{(3)} Z_4^{(3)}$ | $Z_5^{(7)} Z_6^{(7)} Z_7^{(6)} Z_8^{(6)}$ |
| 4th | $Z_5^{(4)} Z_6^{(4)} Z_7^{(4)} Z_8^{(4)}$ | $Z_1^{(6)} Z_2^{(6)} Z_3^{(5)} Z_4^{(5)}$ |
| 5th | $Z_1^{(5)} Z_2^{(5)} Z_3^{(5)} Z_4^{(5)}$ | $Z_5^{(5)} Z_6^{(5)} Z_7^{(4)} Z_8^{(4)}$ |
| 6th | $Z_5^{(6)} Z_6^{(6)} Z_7^{(6)} Z_8^{(6)}$ | $Z_1^{(4)} Z_2^{(4)} Z_3^{(4)} Z_4^{(3)}$ |
| 7th | $Z_1^{(7)} Z_2^{(7)} Z_3^{(7)} Z_4^{(7)}$ | $Z_5^{(3)} Z_6^{(3)} Z_7^{(3)} Z_8^{(2)}$ |
| 8th | $Z_1^{(8)} Z_2^{(8)} Z_3^{(8)} Z_4^{(8)}$ | $Z_1^{(2)} Z_2^{(2)} Z_3^{(1)} Z_1^{(1)}$ |
| output transformation | $Z_1^{(9)} Z_2^{(9)} Z_3^{(9)} Z_4^{(9)}$ | $Z_1^{(1)} - Z_1^{(1)} - Z_1^{(1)} - 1$