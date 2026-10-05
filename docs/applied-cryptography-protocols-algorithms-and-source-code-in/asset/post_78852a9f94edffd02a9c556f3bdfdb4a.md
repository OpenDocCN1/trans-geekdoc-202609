
[1191], the algorithm was recertified for another five years [1150]. Software implementations of DES were finally allowed to be certified. Anyone want to guess what will happen in 1998?

## 12.2 DESCRIPTION OF DES

DES is a block cipher; it encrypts data in 64 blocks. A 64-bit block of plaintext goes in one end of the algorithm and a 64-bit block of ciphertext comes out the other end. DES is a symmetric algorithm: the same algorithm and key are used for both encryption and decryption (except for minor differences in the key schedule).

The length is 56 bits. (The key is usually expressed as a 64-bit number, but every bit is used for parity checking and is ignored. These parity bits are the least-significant bits of the key bytes). The key can be any 56-number and can be changed at any time. A handful of numbers are considered weak keys, but they can be easily avoided. All security rests within the key.

At its simplest level, the algorithm is nothing more than a combination of the two basic techniques of encryption: confusion and diffusion. The fundamental building block of DES is a single combination of these techniques (a substitution followed by a permutation) on the text, based on the key. This is known as a round. DES has 26 rounds; it uses the same combination of techniques on the plaintext 16 times [see Figure 12.1].

The algorithm uses only arithmetic and logical operations on numbers of 64 bits at most, so it was easily implemented in late 1970s hardware technology. The repetitive nature of the algorithm makes it ideal for use on a special-purpose chip. Initial software implementations were clumsy, but current implementations are better.

### Outline of the Algorithm

DES operates on a 64-bit block of plaintext. After an initial permutation, the block is broken into a right and a left half, each 32 bits long. Then there are 16 rounds of identical operations, called f, in which the data are combined with the key. After the sixteenth round, the right and left halves are joined, and a final permutation (the inverse of the initial permutation) finishes off the algorithm.

In each round (see Figure 12.2), the key bits are shifted, and 48 bits are selected from the 56 bits of the key. The right half of the data is expanded to 48 bits via an expansion permutation, combined with 48 bits of shifted and permuted key via XOR, then 8 S-boxes producing 32 new bits, and permuted again. These four operations make f function. The output of f is combined with the left half via XOR. The result of these operations becomes the new right half; the old right half becomes the new left half. These operations are repeated 16 times, making 16 rounds of DES.

If $B_i$ is the result of the $i$th iteration, $L_i$ and $R_i$ are the left and right halves of $B_i$, $K_i$ is the 48-bit key for round $i$, and $f$ is the function that does all the substituting and permuting and XORing with the key, then a round looks like:

## 12.2 Description of DES

![](img/e08b4270295105438dabfbd9a81857bf_293_0.png)

Figure 12.1 DES.

$L_i = R_{i-1}$
$R_i = L_{i-1} \oplus f(R_{i-1}, K_i)$

### The Initial Permutation

The initial permutation occurs before round 1; it transposes the input block described in Table 12.1. This table, like all the tables in this chapter, should be read left to right, top to bottom. For example, the initial permutation moves 58 of the plaintext to bit position 1, 50 to bit position 2, 42 to bit position 3, and so forth.

The initial permutation and the corresponding final permutation do not affect DES's security. As near as anyone can tell, its primary purpose is to make it easier to load plaintext and ciphertext into a DES chip in byte-sized pieces. Remember that DES predates 16-bit or 32-bit microprocessor busses. Since this bit-wise permutation is difficult in software (although it is trivial in hardware), many soft-implementations of DES leave out both the initial and final permutations. While this new algorithm is no less secure than DES, it does not follow the DES standard and should not be called DES.

## CHAPTER 12 Data Encryption Standard (DES)

![](img/e08b4270295105438dabfbd9a81857bf_294_0.png)

Figure 12.2 One round of DES.

### The Key Transformation

Initially, the 64-bit DES key is reduced to a 56-bit key by ignoring every eighth bit. This is described in Table 12.2. These bits can be used as a parity check to ensure the key is error-free. After the 56-bit key is extracted, a 48-bit **subkey** is generated for each of the 16 rounds of DES. These subkeys, $K_i$, are determined in the following manner.

First, the 56-bit key is divided into two 28-bit halves. Then, the halves are circularly shifted by either one or two bits, depending on the round. This shift is given in Table 12.3.

### Table 12.1 Initial Permutation
58. 50. 42. 34. 26. 18. 10. 2. 60. 52. 44. 36. 28. 20. 12. 62. 54. 46. 38. 30. 22. 14. 6. 56. 48. 32. 24. 16. 8. 57. 49. 41. 33. 25. 17. 9. 1. 59. 51. 43. 35. 27. 19. 11. 3. 61. 53. 45. 37. 29. 21. 13. 5. 63. 55. 47. 39. 31. 23. 15. 7.

### Table 12.2 Key Permutation
| 57 | 49 | 41 | 33 | 25 | 17 | 9 | 1 | 58 | 50 | 42 | 34 | 26 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 18 | 10 | 2 | 59 | 51 | 43 | 35 | 27 | 19 | 11 | 3 | 60 | 52 |
| 44 | 36 | 63 | 55 | 47 | 39 | 31 | 15 | 7 | 62 | 54 | 46 | 38 |
| 30 | 22 | 14 | 6 | 61 | 53 | 45 | 37 | 29 | 21 | 13 | 5 | 63 |
(Wait, the text continues)

After being shifted, 48 of the 56 bits are selected. Table 12.4 defines the compression permutation (also called the permuted choice). For example, the bit position 33 of the shifted key moves to 35 of the output, and the bit position 18 of the shifted key is ignored. Because of the shifting, a different subset of key bits is used in each subset. Each bit is used in approximately 14 of the 16 subsets, although not all bits are used the same number of times.

### The Expansion Permutation

This operation expands the right half of the data from 32 bits to 48 bits. Because this operation changes the order of the bits as well as repeating certain bits, it is known as expansion permutation. This operation has two purposes: it makes the right half the same size as the key for the XOR operation and provides a larger result that can be compressed during the substitution operation. However, neither of those is the main cryptographic purpose. By allowing one bit to affect two substitutions, the dependency of the output bits creates an avalanche effect. DES is designed to reach the condition of every bit of the ciphertext depend on every bit of the plaintext and every bit of the key as quickly as possible.

Figure 12.5 defines the expansion permutation. This is sometimes called the E-box. For each 4-bit input, the first and fourth bits represent two bits of the output block, while the second and third bits represent one bit of the output block. Table 12.5 shows which output positions correspond to which input positions. For example, the bit in position 3 of the input block moves to position 4 of the output block, and the bit in position 21 of the input block moves to positions 30 and 32 of the output block.

Although the output block is larger than the input block, each input block generates a unique output block.

### Table 12.3 Number of Key Bits Shuffled per Round
| Round | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Number | 1 | 1 | 2 | 2 | 2 | 2 | 2 | 2 | 1 | 2 | 2 | 2 | 2 | 2 | 2 | 1 |

### Table 12.4 Compression Permutation
| 14, 17, 11, 24, 12, 1, 5, 3, 28, 15, 6, 21, 10 |
| 23, 19, 12, 4, 26, 8, 16, 7, 27, 20, 2 |
| 41, 52, 31, 37, 47, 55, 30, 40, 51, 45, 33 |
| 44, 49, 39, 56, 34, 53, 46, 42, 50, 36, 29, 32 |

### The S-Box Substitution

After the compressed key is XORed with the expanded block, the 48-bit result moves to a substitution operation. The substitutions are performed by eight substitution boxes, or S-boxes. Each S-box has a 6-bit input and a 4-bit output, and there are eight different S-boxes. [The total memory requirement for the eight S-boxes.] The 48 bits are divided into eight 6-bit sub-blocks. Each separate block is operated on a separate S-box: The first block is operated on by S-box 1, the second block is operated on by S-box 2, and so on. See Figure 12.4.

Each S-box is a table of 4 rows and 16 columns. Each entry in the box is a 4-bit number. The 6 bits of the S-box specify which row and column number to look for the output. Table 12.6 allows eight S-boxes.

The input bits specify an entry in the S-box in a very particular manner. Consider an S-box input of 6 bits, labeled $b_1, b_2, b_3, b_4, b_5, b_6$. Bits $b_1$ and $b_2$ are combined to form a 2-bit number, from 0 to 3, which correspond to a row in the table. The middle 4 bits, $b_3$ through $b_6$, are combined to form a 4-bit number, from 0 to 15, which corresponds to a column in the table.

For example, that the input to the sixth S-box (i.e., bits 31 through 36 of the XOR function) is 110011. The first and last bits combine to form 11, which cor-

![](img/e08b4270295105438dabfbd9a81857bf_296_0.png)

Figure 12.3 Expansion permutation.
