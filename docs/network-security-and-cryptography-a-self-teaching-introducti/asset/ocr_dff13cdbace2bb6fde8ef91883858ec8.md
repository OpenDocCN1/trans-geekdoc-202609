# Solution

1. Row Number $n = (01) = 1$
Column Number $m = (1101) = 13$
The Decimal Number stored at location (1, 13) is 11.
Therefore, the 4-bit output of the S-Box will be: 1011

2. The concatenation of 4-bit outputs from 8 S-Boxes will generate a 32-bit
output.
**Permutation (P):** The 32-bit information is permuted in accordance
with the Permutation P shown in Table 6.8. The bit from the 16th
position is shifted to the 1st position; the bit from 07th is shifted to
position 2, and so on.

TABLE 6.8 Permutation Table

| 16 | 07 | 20 | 21 | 29 | 12 | 28 | 17 |
|---|---|---|---|---|---|---|--|
| 01 | 15 | 23 | 26 | 05 | 18 | 31 | 10 |
| 02 | 08 | 24 | 14 | 32 | 27 | 03 | 09 |
| 19 | 13 | 30 | 06 | 22 | 11 | 04 | 25 |

# 6.5.3 Generation of Sub-Keys (...$K_w$)

A total of 16 sub-keys (one per round) are computed starting from key
size 64. The generation of 16 sub-keys is achieved through the following
steps:

+   1. First the 64-bit input is compressed to 56 bits by ignoring every 8th bit of
t input as shown in Table 6.9. Then, the 56-bit key is permuted accord-
ing to Table PC-1 (Permutation-Choice) as shown in Table 6.10.

TABLE 6.9 Input 64-Bit Key

| 01 | 02 | 03 | 04 | 05 | 06 | 07 | 08 |
|---|---|---|---|---|---|---|--|
| 09 | 10 | 11 | 12 | 13 | 14 | 15 | 16 |
| 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 |
| 25 | 26 | 27 | 28 | 29 | 30 | 31 | 32 |
| 33 | 34 | 35 | 36 | 37 | 38 | 39 | 40 |
| 41 | 42 | 43 | 44 | 45 | 46 | 47 | 48 |
| 49 | 50 | 51 | 52 | 53 | 54 | 55 | 56 |
| 57 | 58 | 59 | 60 | 61 | 62 | 63 | 64 |