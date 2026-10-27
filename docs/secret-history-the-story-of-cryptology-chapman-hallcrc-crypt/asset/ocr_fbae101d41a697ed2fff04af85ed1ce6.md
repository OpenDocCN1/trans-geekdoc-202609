![](bbox=[0.219, 0.108, 0.781, 0.42])

**Figure 13.4** The heart of DES. ([http://csrc.nist.gov/publications/fips/fips46-3/fips46-3.pdf](http://csrc.nist.gov/publications/fips/fips46-3/fips46-3.pdf))

Once the expanded right hand side and the round key have been XORed, the result is broken up into eight pieces of six bits each, each of which is fed into a substitution box (*S*-box) that returns only four bits. Finally, a permutation, *P*, is performed on the output and the round is complete. See [Figure 13.4](#) for a depiction of these steps. The permutation *P* is given by:

| 16 | 7 | 20 | 21 |
|---:|---:|---:|---:|
| 29 | 12 | 28 | 17 |
| 1 | 15 | 23 | 26 |
| 5 | 18 | 31 | 10 |
| 2 | 8 | 24 | 14 |
| 32 | 27 | 3 | 9 |
| 19 | 13 | 30 | 6 |
| 22 | 11 | 4 | 25 |

The nonlinear heart of the algorithm is the *S*-boxes. Each box converts a 6-bit number, *b*₁*b*₂*b*₃*b*₄*b*₅*b*₆, to a 4-bit number by first breaking it up into *b*₁*b*₆ and *b*₂*b*₃*b*₄*b*₅. That is, we now have a 2-bit and a 4-bit number. Converting each of these to base 10, the first is between 0 and 3 and the second is between 0 and 15. Thus, a row and column of the *S*-box is referenced. The value at that location is our 4-bit result. All eight *S*-boxes are provided in [Table 13.1](#).