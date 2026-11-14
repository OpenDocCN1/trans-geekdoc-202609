# # 8.7. Exercises for application

ETL 3.-

# ## Part A: traditional cryptography

# ### 1. Use mono-alphabetic substitution to encrypt data.

+   1.1. Encrypt the text “OFPP ISTA TRI” using mono-alphabetic encryption with a shift of three characters (the encryption key is equal to 3).

| Plain-text | O | F | P | P | T | I | S | T | A | T | R | I |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Shift | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 | 3 |
| Encrypted text | | | | | | | | | | | | |

+   1.2. Encrypt the text “The Office of Vocational Training and Work Promotion” using mono-alphabetic encryption with a shift of 5 characters.

+   1.3. Decrypt the following text “PEGVCTXSKVETLMIGPEWWMUYI” knowing that it was encrypted using mono-alphabetic encryption with a shift of 4 characters (add spaces).

# ### 2. Encrypt with poly-alphabetic substitution.

+   2.1. Encrypt the text “OFPP ISTA TRI” using poly-alphabetic encryption with an offset of “132” or (bdc) (the encryption key is 132).

| Plain-text | O | F | P | P | T | I | S | T | A | T | R | I |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| Shift | 1 | 3 | 2 | 1 | 3 | 2 | 1 | 3 | 2 | 1 | 3 | 2 |
| Encrypted text | | | | | | | | | | | | |

+   2.2. Encrypt text “Office of Vocational Training and Promotion of Work” using poly-alphabetic encryption with a shift of “202”.

+   2.3. Decrypt the following text “MDGSBTURKSDTILIDOETVMRI” knowing that it was encrypted using poly-alphabetic encryption with a shift of “134” or (BDE) (add spaces).