Apparently, back in the 1970s, this permutation made it easier to load the chip, when DES encryption is carried out by hardware, rather than software. Hardware implementations of DES work really well, but software implementations aren’t very efficient, because software doesn’t deal well with permutations of bits. On the other hand, permuting bytes could be done more efficiently. This approach is taken in portions of AES, an algorithm examined in Section 20.3.

The inverse of the Initial Permutation is:

| 40 | 8 | 48 | 16 | 56 | 24 | 64 | 32 |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 39 | 7 | 47 | 15 | 55 | 23 | 63 | 31 |
| 38 | 6 | 46 | 14 | 54 | 22 | 62 | 30 |
| 37 | 5 | 45 | 13 | 53 | 21 | 61 | 29 |
| 36 | 4 | 44 | 12 | 52 | 20 | 60 | 28 |
| 35 | 3 | 43 | 11 | 51 | 19 | 59 | 27 |
| 34 | 2 | 42 | 10 | 50 | 18 | 58 | 26 |
| 33 | 1 | 41 | 9 | 49 | 17 | 57 | 25 |

These permutations are always as above. They are not part of the key and add nothing to the security of DES. The cipher would be just as strong (or weak) without them, but it wouldn’t be DES.

Now, to complete the description of DES, we need to examine how the round keys are obtained from K. It is accurate to refer to the key K as being 56 bits, but an extra 8 bits were used for error detection. These check bits are inserted in positions 8, 16, 24, 32, 40, 48, 56, and 64 in order to make the parity of each byte even. So, when selecting key bits from this 64-bit string, to use as a round key, the positions holding the check digits should be ignored. The relevant 56 bits are selected and permuted as follows.

# PC-1 (Permuted Choice 1)

| 57 | 49 | 41 | 33 | 25 | 17 | 9 |
|---:|---:|---:|---:|---:|---:|---:|
| 1 | 58 | 50 | 42 | 34 | 26 | 18 |
| 10 | 2 | 59 | 51 | 43 | 35 | 27 |
| 19 | 11 | 3 | 60 | 52 | 44 | 36 |

| 63 | 55 | 47 | 39 | 31 | 23 | 15 |
|---:|---:|---:|---:|---:|---:|---:|
| 7 | 62 | 54 | 46 | 38 | 30 | 22 |
| 14 | 6 | 61 | 53 | 45 | 37 | 29 |
| 21 | 13 | 5 | 28 | 20 | 12 | 4 |

There is more work to be done before we obtain a round key, though. A blank line was placed in the middle of the 56 bits to indicate that it is split in half, just like the message blocks. To avoid the confusion with L and R, we label these halves C and D.