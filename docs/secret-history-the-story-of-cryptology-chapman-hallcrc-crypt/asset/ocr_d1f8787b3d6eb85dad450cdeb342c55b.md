As an example, suppose that just prior to heading into the *S*-boxes, you have the following string of 48 bits:

```
01010000011010110011101000110110011000011110101.
```

The first six bits, \(b_1b_2b_3b_4b_5b_6 = 010100\), will be substituted for using the first *S*-box, \(S_1\). We have \(b_1b_6 = 00\) and \(b_2b_3b_4b_5 = 1010\). Converting these to base 10, we get 0 and 10, so we look in row 0 and column 10 of \(S_1\), where we find 6. Converting 6 to base 2 gives 0110. Thus, the first 6 bits of the 48-bit string above are replaced by 0110.

We then move on to the next 6 bits of our original 48-bit string, 000110. If we now label these as \(b_1b_2b_3b_4b_5b_6\), we have \(b_1b_6 = 00\) and \(b_2b_3b_4b_5 = 0011\). Converting these to base 10, we get 0 and 3, so we look in row 0 and column 3 of \(S_2\), where we find 14. Converting 14 to base 2 gives 1110. Thus, the second 6 bits of the 48-bit string above are replaced by 1110. We continue in this manner, 6 bits at a time, until all 48 bits have been replaced by using each of the 8 *S*-boxes, in order. The final result is a 32-bit string.

It might seem that the particular values that fill the substitution boxes aren’t important. One substitution is as good as another, right? Wrong! The official description for DES stated, “The choice of the primitive functions *KS*, \(S_1,\ldots,S_8\) and *P* is critical to the strength of the encipherment resulting from the algorithm.”

Much more will be said about these *S*-boxes in this chapter, but for now, we continue the discussion of how DES works. We are now ready to look at the big picture.

*Figure 13.5* illustrates the 16 rounds that were discussed above. Notice that there is no swapping of right and left sides after the last round. This is so that encryption and decryption follow the same steps with the only difference being that the round keys must be used in the opposite order for decryption. It is important to note that the composition of rounds is not a round; that is, in general, two rounds with different keys cannot be realized by a single round using some third key. If this were the case, 16 rounds would be no better than one; they’d only take longer!

The only new elements here are the initial permutation and, at the end, the inverse initial permutation.

The initial permutation is given by:

|  |  |  |  |  |  |  |  |
|---:|---:|---:|---:|---:|---:|---:|---:|
| 58 | 50 | 42 | 34 | 26 | 18 | 10 | 2 |
| 60 | 52 | 44 | 36 | 28 | 20 | 12 | 4 |
| 62 | 54 | 46 | 38 | 30 | 22 | 14 | 6 |
| 64 | 56 | 48 | 40 | 32 | 24 | 16 | 8 |
| 57 | 49 | 41 | 33 | 25 | 17 | 9 | 1 |
| 59 | 51 | 43 | 35 | 27 | 19 | 11 | 3 |
| 61 | 53 | 45 | 37 | 29 | 21 | 13 | 5 |
| 63 | 55 | 47 | 39 | 31 | 23 | 15 | 7 |

Nobody seems to know why the designers bothered to rearrange the bits of the plaintext—it has no cryptographic effect—but that’s how DES is defined.

—Bruce Schneier