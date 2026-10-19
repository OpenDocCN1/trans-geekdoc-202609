| Plaintext | H | I | K | E | B | A | C | K |
| Key | F | I | C | K | L | E | F | I |
| Ciphertext | M | Q | M | O | M | E | H | S |

The ciphertext is found by finding where the H of the plaintext – the top row of the table – intersects with the F row of the ciphertext. Again, one sees the power of a polyalphabetic system where repeated values in the plaintext do not necessarily give the same ciphertext values, and repeated ciphertext values correspond to different plaintext inputs.

# Modular Mathematics and the Running Key Cipher

The use of modular mathematics and the representation of each letter by its numerical place in the alphabet are the key to many modern ciphers:

| A | B | C | D | E | F | G | H | I | J | K | L | M | N | O | P | Q | ... | Z |
| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | ... | 25 |

The English alphabet would be calculated as "mod 26" because there are 26 letters in the English alphabet. The use of mod 26 means that whenever the result of a mathematical operation is equal to or greater than 26, 26 is subtracted from the total as often as needed until it is less than 26.

Using the above values, the cryptographic operation operates as follows:

```
Ciphertext = plaintext + key (mod 26).
This is written as C = P + K (mod 26).
Ciphertext is the value of the plaintext + the value of the key (mod 26).
```

For example, the plaintext letter N has a value of 13 (it is the 13th letter in the alphabet using the table above). If the key to be used to encrypt the plaintext is a Q with a value of 16, the ciphertext would be 13 + 16, or the 29th letter of the alphabet. Because there is no 29th letter in the English alphabet, 26 is subtracted (hence the term mod 26) and the ciphertext becomes the letter corresponding to the number 3, a D.

# Running Key Cipher