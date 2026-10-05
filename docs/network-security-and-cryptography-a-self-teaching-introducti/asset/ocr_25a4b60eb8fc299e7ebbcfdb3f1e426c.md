Column 8 from the key input is eliminated, and the remaining 56 bits are permuted in accordance with the permutation table in Table 6.10. The bit from position 57 is shifted to bit position 1 and the bit from position 49 is shifted to position 2, and so on.

# Table 6.10 Permutation for Permuted Choice-1 (PC-1)

| 57 | 49 | 41 | 33 | 25 | 17 | 09 |
| 01 | 58 | 50 | 42 | 34 | 26 | 18 |
| 10 | 02 | 59 | 51 | 43 | 35 | 27 |
| 19 | 11 | 03 | 60 | 52 | 44 | 36 |
| 63 | 55 | 47 | 39 | 31 | 23 | 15 |
| 07 | 62 | 54 | 46 | 38 | 30 | 22 |
| 14 | 06 | 61 | 53 | 45 | 37 | 29 |
| 21 | 13 | 05 | 28 | 20 | 12 | 04 |

+   2. The output of PC-1 is divided into two halves of 28 bits each, which are fed to the Left Shifters. The Left Shifters rotate the two halves left by 1 or 2 bits, depending on the rotation. The rotation left is by 1 bit in rounds 1, 2, and 9, and the rotation is by 2 in the remaining 13 rounds.

+   3. The outputs of the Two Left-Shifters are concatenated and fed to the Permutation/Concentration Block. This block permutes the input and reduces it to 48 bits according to Table Permuted Choice-2 (PC-2) as shown in Table 6.11, by ignoring 8 bits of the 56-bit input. The 48-bit output forms the Key $K_1$ for the first Round. The bit from position 14 is shifted to position 1, the bit bit from position 17 is shifted to position 2, and so on.

# Table 6.11 Permutation for Permuted Choice-2 (PC-2)

| 14 | 17 | 11 | 24 | 01 | 05 | 03 | 28 |
| 15 | 06 | 21 | 10 | 23 | 19 | 12 | 04 |
| 26 | 08 | 16 | 07 | 27 | 20 | 13 | 02 |
| 41 | 52 | 31 | 37 | 47 | 55 | 30 | 40 |
| 51 | 45 | 33 | 48 | 44 | 49 | 39 | 56 |
| 34 | 53 | 46 | 42 | 50 | 36 | 29 | 32 |

+   4. The 28-bit outputs of the two left-shifters form inputs for the generation of the next round.