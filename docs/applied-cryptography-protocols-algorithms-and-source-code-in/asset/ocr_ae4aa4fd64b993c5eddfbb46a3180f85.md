# 13.6 LOKI

# 315

![](bbox=[0.137, 0.105, 0.646, 0.513])

Figure 13.8 Table 13.2.

$P$, is given in Table 13.2. Then the four 8-bit outputs are recombined to form a single 32-bit number and sent through the permutation described in Table 13.3. Finally, the right half XORed with the left half to become the new left half, and the left half becomes the new right half. After 16 rounds, the block is XORed with the key to produce the ciphertext. The subkeys are generated from the key in a straightforward manner. The 64-bit key is split into a left half and a right half. In each round, the subkey is the left half. This left half is then rotated 12 or 13 bits to the left, and every two rounds the left and right halves are exchanged. As DES, the same algorithm can be used for both encryption and decryption, with some modification in how the subkeys are used.

# Table 13.1
Expansion Permutation

| 4 | 3 | 2 | 1 | 32 | 31 | 20 | 29 | 28 | 27 | 26 | 25 | |
| 28 | 27 | 26 | 25 | 24 | 23 | 22 | 21 | 20 | 19 | 18 | 17 | |
| 20 | 19 | 18 | 17 | 16 | 15 | 14 | 13 | 12 | 11 | 10 | 9 | |
| 12 | 11 | 10 | 9 | 8 | 7 | 6 | 5 | 4 | 3 | 2 | 1 |