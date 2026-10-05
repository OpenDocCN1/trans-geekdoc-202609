B. Then each group $i$ is expanded to 6 bits by appending a copy of the last bit of the previous group $i-1$ to the beginning of group $i$, and appending a copy of the first bit of the next group $i+1$ to the end of group $i$. For this purpose, the last group is taken as before the first group and the first group is taken as the next to last group. Table 6.6 shows the Expansion Permutation (E):

# TABLE 6.6 Expansion Permutation (E)

| 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|n| 5 | 6 | 7 | 8 | 9 |
| 8 | 10 | 11 | 12 | 13 |
| 12 | 13 | 14 | 15 | 16 |
| 17 | 17 | 18 | 19 | 20 |
| 21 | 21 | 22 | 23 | 24 |
| 24 | 25 | 26 | 27 | 29 |
| 28 | 29 | 30 | 31 | 1 |

# Example 6.2

Input ... 0010 1010 1100 ....
The middle group (1010) will be expanded to (010101) and so on.

**2. Substitution/Choice (by Use S-Boxes):** DES uses 8 specially designed S-Boxes as non-linear components. Each box has 4 rows indexed $(0 \dots 3)$ and 16 columns indexed $(0 \dots 15)$ of decimal numbers $(0 \dots 15)$. The numbers are distributed in each row in a random manner and none of the digits is repeated in a row; that is, each of the 16 digits $(0 \dots 15)$ appears precisely in a row.
A Sample S-box is appended in Table 6.7:

# TABLE 6.7 A Sample S-Box

| 10 | 00 | 09 | 14 | 06 | 03 | 15 | 05 | 01 | 13 | 12 | 07 | 11 | 04 | 02 | 08 |
| 13 | 07 | 00 | 09 | 03 | 04 | 06 | 10 | 02 | 08 | 05 | 14 | 12 | 11 | 15 | 01 |
| 03 | 06 | 04 | 09 | 08 | 15 | 03 | 00 | 11 | 01 | 02 | 12 | 05 | 10 | 14 | 07 |
| 01 | 10 | 13 | 00 | 06 | 09 | 08 | 07 | 04 | 15 | 14 | 03 | 11 | |002 | 12 |