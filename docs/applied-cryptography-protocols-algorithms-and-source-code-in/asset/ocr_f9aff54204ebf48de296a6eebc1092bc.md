# CHAPTER 12 Data Encryption Standard (DES)

# Table 12.4
Compression Permutation

|14, 17, 11, 24, 12, 1, 5, 3, 28, 15, 6, 21, 10,|
|23, 19, 12, 4, 26, 8, 16, 7, 27, 20, 2,|
|41, 52, 31, 37, 47, 55, 30, 40, 51, 45, 33, 48,|
|44, 49, 39, 56, 34, 53, 46, 42, 50, 36, 29, 32|

# The S-Box Substitution

After the compressed key is XORed with the expanded block, the 48-bit result moves to a substitution operation. The substitutions are performed by eight substitution boxes, or S-boxes. Each S-box has a 6-bit input and a 4-bit output, and there are eight different S-boxes. [The total memory requirement for the eight DES S-boxes.] The 48 bits are divided into eight 6-bit sub-blocks. Each separate block is operated on a separate S-box: The first block is operated on by S-box 1, the second block is operated on by S-box 2, and so on. See Figure 12.4.

Each S-box is a table of 4 rows and 16 columns. Each entry in the box is a 4-bit number. The 6 bits of the S-box specify which row and column number to look for the output. Table 12.6 allows eight S-boxes.

The input bits specify an entry in the S-box in a very particular manner. Consider an S-box input of 6 bits, labeled $b_1, b_2, b_3, b_4, b_5, b_6$. Bits $b_1$ and $b_2$ are combined to form a 2-bit number, from 0 to 3, which correspond to a row in the table. The middle 4 bits, $b_3$ through $b_6$, are combined to form a 4-bit number, from 0 to 15, which corresponds to a column in the table.

For example, that the input to the sixth S-box (i.e., bits 31 through 36 of the XOR function) is 110011. The first and last bits combine to form 11, which cor-

![](bbox=[0.17, 0.635, 0.75, 0.873])

Figure 12.3 Expansion permutation.