|  | Key (Part 1) |  |  |
|---|---|---|---|
| Key (Part 2) | 1 | 3 | 2 |
| 2 | n | o | w |
| 3 | i | s | t |
| 1 | h | e | t |

Figure 3-3 Transposition Cipher

# Substitution and Transposition Ciphers

The specific mathematical processes in ciphers today are extremely complex. However, most use variations of two basic mathematical processes—substitution and transposition.

# Substitution Ciphers

In **substitution ciphers**, one character is substituted for another, but the order of characters is not changed. If this sounds like the cipher discussed in Figure 3-2, it should. The example cipher is a very simple substitution cipher. Each letter is substituted for another letter in the alphabet. However, the position of each letter is the same. So, *n-o-w* becomes *r-w-l*.

> In substitution ciphers, one character is substituted for another.

# Transposition Ciphers

In **transposition ciphers**, in turn, the letters are moved around within a message, based on their initial positions in the message. The letters themselves are not changed, as they are in substitution ciphers, but their position in the message does.

> Transposition ciphers move letters around within a message but characters are not substituted.

Figure 3-3 shows a simple transposition cipher. First, the plaintext (*nowisthet*) is written in a three-by-three matrix—or as much of the message as will fit in the matrix. The key has six numbers (132231). The first part of the key (132) consists of a number on each column and the second part (231) a number on each row.

The cipher determines how the letters are taken out of the transposition box. The first letter out will have column key value 1 and row key value 1. This is the first column and the third row. The letter there is *h*. So, *h* is the first ciphertext character.

The second letter out will have column key value 1 and row key value 2. This is the first column and the first row. The letter there is *n*. So, *n* is the second ciphertext character. We now have *hn* at the beginning of the ciphertext. The rest of the ciphertext can be determined by taking letters from the transposition box in similar column-row order.

# Real-World Encryption

In substitution ciphers, letters are changed but their position is not. In transposition ciphers, the letters are not changed, but their position in the ciphertext is changed. Real ciphers are much more complex than our examples have indicated. First, encryption is done on bits, not on letters of the alphabet. In addition, real-world ciphers

# Test Your Understanding

+   3. a. Which leaves letters unchanged—transposition or substitution ciphers?
+      b. Which leaves letters in their original positions—transposition or substitution ciphers?
+   4. Complete the enciphering in Figure 3-3.