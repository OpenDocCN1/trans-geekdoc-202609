
![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_406_0.png)

**Figure 13.1  Horst Feistel (1915–1990).** ([http://crypto-dox.com/History_of_Cryptography](http://crypto-dox.com/History_of_Cryptography)).

Horst Feistel (Figure 13.1), an IBM employee born in Germany, is the man credited as the creator of DES (although others were involved—more on this soon). He wanted to call the system Datasal, but IBM used the term Demoncipher, which was truncated to Demon. Finally, the name was changed to Lucifer, maintaining what Feistel called “the evil atmosphere” of Demon, as well as “cifer” (cipher).⁵ DSD-1 was another name used internally for this cipher.⁶ Lucifer was used by Lloyds Bank of London for a cash dispensing system in the early 1970s.⁷

The National Bureau of Standards (NBS)⁸ held a competition for a cipher system to meet civilian needs. This system was to be called the Data Encryption Standard or DES. The call for algorithms appeared in the *Federal Register* on May 15, 1973 (Vol. 38, No. 93, p. 12763) and again on August 27, 1974 (Vol. 39, No. 167, p. 30961). Lucifer was the only algorithm deemed acceptable by NBS and their NSA advisors.

The algorithm appeared in the *Federal Register* on March 17, 1975 and again on August 1, 1975 with a request for reader comments.⁹ Thus, Lucifer was adopted as the standard on July 15, 1977, and had a final name change to DES. IBM agreed to place the relevant patents in the public domain, so anyone who desired could freely use the algorithm; however, this didn’t prevent money being made from the system by other companies that manufactured chips implementing the algorithm.¹⁰

⁵ Kahn, David, *The Codebreakers*, second edition, Scribner, New York, 1996, p. 980.

⁶ Levy, Steven, *Crypto: How the Code Rebels Beat the Government, Saving Privacy in the Digital Age*, Viking, New York, 2001.

⁷ Kinnucan, Paul, “Data Encryption Gurus: Tuchman and Meyer,” *Cryptologia*, Vol. 2, No. 4, October 1978, pp. 371–381.

⁸ NBS was founded in 1901, but renamed Bureau of Standards in 1903. It became NBS again in 1934 and then, finally, National Institute of Standards and Technology (NIST) in 1988 ([http://www100.nist.gov/directors.htm](http://www100.nist.gov/directors.htm)).

⁹ Roberts, Richard W., National Bureau of Standards, “Encryption Algorithm for Computer Data Protection: Requests for Comments,” *Federal Register*, Vol. 40, No. 52, March 17, 1975, pp. 12134–12139 and Hoffman, John D., National Bureau of Standards, “Federal Information Processing Data Encryption Proposed Standard,” *Federal Register*, Vol. 40, No. 149, August 1, 1975, pp. 32395–32414.

¹⁰ Morris, Robert, Neil J. A. Sloane, and Aaron D. Wyner, “Assessment of the National Bureau of Standards Proposed Federal Data Encryption Standard,” *Cryptologia*, Vol. 1, No. 3, July 1977, pp. 281–291, p. 284 cited here. Also see Winkel, Brian J., “There and there a department,” *Cryptologia*, Vol. 1, No. 4, 1977, pp. 396–397.

DES can be intimidating when viewed all at once, but the individual pieces it is made out of are very simple. The basic units (called *blocks*) on which the algorithm works are 64 bits (8 characters) long. One operation used in DES consists of breaking the 64-bit message block in half and switching sides, as depicted in the diagram in **Figure 13.2**.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_407_0.png)

**Figure 13.2**  _L₁_, the new left-hand side, is simply _R₀_, the old right-hand side; _R₁_, the new right-hand side, is _L₀_, the old left-hand side. (http://csrc.nist.gov/publications/fips/fips46-3/fips46-3.pdf.)

This operation is clearly its own inverse.

Another operation that is its own inverse is adding bits modulo 2. This is also known as XOR (for exclusive OR) and is often denoted by ⊕. **Figure 13.3** shows a function _f_, which takes _K₁_ (derived from the 56-bit key _K_) and _R₀_ as inputs and outputs a value that is then XORed with _L₀_ to obtain _R₁_.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_407_1.png)

**Figure 13.3**  Function _f_. (http://csrc.nist.gov/publications/fips/fips46-3/fips46-3.pdf.)

This combination of two self-inverse operations is referred to as a _round_. DES goes through 16 such rounds. The manner in which the round keys are derived from _K_ will be detailed, but first we examine the function _f_. In general, we refer to a cipher that uses rounds of the form depicted above (switching sides and applying a function to one half) as a Feistel system, or Feistel cipher.

The most natural way of combining _Rᵢ_ and _Kᵢ_ would be to XOR them, but _Rᵢ_ is 32 bits long and each of the round keys is 48 bits long. To even things up, _R_ is expanded by repeating some of the bits (their order is changed as well). This is indicated in **Figure 13.4**, and referred to as _E_ (for expansion). _E_ is given by the following:

| 32 | 1 | 2 | 3 | 4 | 5 |
|---:|---:|---:|---:|---:|---:|
| 4 | 5 | 6 | 7 | 8 | 9 |
| 8 | 9 | 10 | 11 | 12 | 13 |
| 12 | 13 | 14 | 15 | 16 | 17 |
| 16 | 17 | 18 | 19 | 20 | 21 |
| 20 | 21 | 22 | 23 | 24 | 25 |
| 24 | 25 | 26 | 27 | 28 | 29 |
| 28 | 29 | 30 | 31 | 32 | 1 |

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_408_0.png)

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

## Table 13.1  S-Boxes

### S₁

| Row No. \ Column Number | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 14 | 4 | 13 | 1 | 2 | 15 | 11 | 8 | 3 | 10 | 6 | 12 | 5 | 9 | 0 | 7 |
| 1 | 0 | 15 | 7 | 4 | 14 | 2 | 13 | 1 | 10 | 6 | 12 | 11 | 9 | 5 | 3 | 8 |
| 2 | 4 | 1 | 14 | 8 | 13 | 6 | 2 | 11 | 15 | 12 | 9 | 7 | 3 | 10 | 5 | 0 |
| 3 | 15 | 12 | 8 | 2 | 4 | 9 | 1 | 7 | 5 | 11 | 3 | 14 | 10 | 0 | 6 | 13 |

### S₂

| Row No. \ Column Number | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 15 | 1 | 8 | 14 | 6 | 11 | 3 | 4 | 9 | 7 | 2 | 13 | 12 | 0 | 5 | 10 |
| 1 | 3 | 13 | 4 | 7 | 15 | 2 | 8 | 14 | 12 | 0 | 1 | 10 | 6 | 9 | 11 | 5 |
| 2 | 0 | 14 | 7 | 11 | 10 | 4 | 13 | 1 | 5 | 8 | 12 | 6 | 9 | 3 | 2 | 15 |
| 3 | 13 | 8 | 10 | 1 | 3 | 15 | 4 | 2 | 11 | 6 | 7 | 12 | 0 | 5 | 14 | 9 |

### S₃

| Row No. \ Column Number | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 10 | 0 | 9 | 14 | 6 | 3 | 15 | 5 | 1 | 13 | 12 | 7 | 11 | 4 | 2 | 8 |
| 1 | 13 | 7 | 0 | 9 | 3 | 4 | 6 | 10 | 2 | 8 | 5 | 14 | 12 | 11 | 15 | 1 |
| 2 | 13 | 6 | 4 | 9 | 8 | 15 | 3 | 0 | 11 | 1 | 2 | 12 | 5 | 10 | 14 | 7 |
| 3 | 1 | 10 | 13 | 0 | 6 | 9 | 8 | 7 | 4 | 15 | 14 | 3 | 11 | 5 | 2 | 12 |

### S₄

| Row No. \ Column Number | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 7 | 13 | 14 | 3 | 0 | 6 | 9 | 10 | 1 | 2 | 8 | 5 | 11 | 12 | 4 | 15 |
| 1 | 13 | 8 | 11 | 5 | 6 | 15 | 0 | 3 | 4 | 7 | 2 | 12 | 1 | 10 | 14 | 9 |
| 2 | 10 | 6 | 9 | 0 | 12 | 11 | 7 | 13 | 15 | 1 | 3 | 14 | 5 | 2 | 8 | 4 |
| 3 | 3 | 15 | 0 | 6 | 10 | 1 | 13 | 8 | 9 | 4 | 5 | 11 | 12 | 7 | 2 | 14 |
