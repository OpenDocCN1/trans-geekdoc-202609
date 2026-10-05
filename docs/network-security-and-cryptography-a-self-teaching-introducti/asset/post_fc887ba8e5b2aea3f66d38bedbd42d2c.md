
# CONTENTS

- 2.22 Jackson Networks ................................................................................ 108
- 2.23 Exercises...................................................................................................... 109

## Chapter 3 Overview of Cryptography ............................................................ 111

- 3.1 Introduction .......................................................................................... 111
- 3.2 Basic Terms Related to Cryptography ................................................... 115
- 3.1.1 Cryptographic Primitives ................................................................ 117
- 3.1.2 Cryptographic Protocols ....................................................... 117
- 3.1.3 Encryption (at the Sender's End) ........................................ 117
- 3.1.4 Decryption (at the Recipient's End) ........................................ 117
- 3.2 Requirements of Secure Communication ................................... 117
- 3.3 OSI Security Architecture X.800 ....................................... 119
- 3.3.1 Security Attacks ....................................................... 120
- 3.3.2 Security Services ......................................................... 121
- 3.3.3 Security Mechanisms ................................................ 123
- 3.4 Categories of Cryptographic Systems ................................... 127
- 3.5 Symmetric (or Conventional) Encryption Model.............................. 128
- 3.5.1 Types of Attacks on a Conventional Encryption Scheme...................... 130
- 3.5.2 Conventional Encryption for Confidentiality ....................... 131
- 3.5.3 Link Encryption ........................................................ 132
- 3.6 Exercises ....................................................................... 136

## Chapter 4 Mathematical Foundations for Cryptography ............ 139

- 4.1 Introduction ................................................................... 140
- 4.2 Introduction to Groups, Rings, and Fields ...................... 140
- 4.2.1 Groups ................................................................ 140
- 4.2.2 Ring .................................................................... 144
- 4.2.3 Field ................................................................ 145
- 4.3 Modular Arithmetic (mod n) ................................ 146
- 4.3.1 Residue Classes (mod n) ....................................... 148
- 4.3.2 Properties of Zp ................................................ 149
- 4.3.3 Multiplication within Set Zp ................................... 151
- 4.4 Introduction to Primes and Co-Primes ........................ 154
- 4.4.1 Prime Numbers....................................................... 154
- 4.4.2 Co-Prime Numbers or Relatively Prime Numbers ........... 154
- 4.5 Euclid's Algorithm to Determine GCD ................ 155
- 4.6 Extended Euclid's Algorithm ................................ 156
- 4.7 Galois Finite Fields ................................................................................ 159
- 4.7.1 GF (p) ............................................................................................... 160
- 4.7.2 Set Z_p ................................................................................................ 160
- 4.7.3 Galois Fields of Order 2ⁿ ................................................................ 161
- 4.7.4 Arithmetic Operations within GF (2ⁿ) ........................................ 161
- 4.7.5 Addition (+) Operation within GF (2ⁿ) ................................................... 163
- 4.7.6 Addition Inverse of GF (2ⁿ) ............................................................ 163
- 4.7.7 Multiplication (x) Operation within GF (2³) Using m(x) = x³ + x² + 1 for Reducing the Polynomials .......................... 163
- 4.7.8 Multiplication Inverses within GF (2ⁿ) ................................ 164
- 4.7.9 Primitive Inverses of All Integers in GF (2ⁿ) ....................... 165
- 4.8 Fermat's Little Theorem......................................................................... 166
- 4.8.1 Corollary of Fermat's Little Theorem ............................... 167
- 4.9 Euler's Totient Function .................................................................... 168
- 4.9.1 General Formula for Computation of Totient Function ϕ(n)....... 169
- 4.10 Euler's Theorem ...................................................................... 170
- 4.10.1 A Corollary of Euler's Theorem ....................................... 172
- 4.11 Prime Numbers .......................................................................... 175
- 4.11.1 Primitive Roots ......................................................... 176
- 4.12 Discrete Logarithms ....................................................... 178
- 4.12.1 Difficulty of Computing Discrete Logarithms ................ 178
- 4.12.2 Algorithm to Determine the Primitive Roots of a Number n... 180
- 4.12.3 Another Method of Determining the Primitive Roots of a n ............................................................................................ 181
- 4.13 Primality Testing ...................................................... 182
- 4.13.1 Miller and Rabin's Method ........................................ 189
- 4.14 Remainder Theorem ....................................................... 189
- 4.14.1 Interpretation of the Chinese Remainder Theorem.................. 190
- 4.15 Exercises ....................................................................... 195

## Chapter 5 Classical Cipher Schemes...................................... 199

- 5.1 Introduction ............................................................ 199
- 5.2 Some Basic Concepts for Symmetric Ciphers................................ 220
- 5.2.1 Concept of Binary Block Substitution............................................. 220
- 5.2.2 Strength of the Substitution Cipher...................................... 222
- 5.2.3 Key Size for the Simple Substitution............................................... 223
- 5.3 Shannon's Theory of Diffusion and Confusion.................. 223
- 5.3.1 Diffusion....................................................................... 224
- 5.3.2 Confusion..................................................................... 224
- 5.4 Feistel Cipher.................................................................... 224
- 5.4.1 Strength of the Feistel Cipher....................................... 226
- 5.5 Data Encryption Standard (DES)................................................ 227
- 5.5.1 Description of the Critical Functions of Each Round of DES............................... 233
- 5.5.2 S-Box Transformation...................................................... 236
- 5.5.3 Generation of Sub-Keys ($K_1...K_{16}$)................................ 237
- 5.5.4 DES Decryption Algorithm............................................... 239
- 5.6 Avalanche Effect....................................................... 239
- 5.6.1 Strength of DES....................................................... 240
- 5.6.2 Possible Attacks on DES............................................... 241
- 5.6.3 Differential Cryptanalysis vs. Linear Cryptanalysis...... 245
- 5.7 Multiple DES..................................................... 245
- 5.7.1 Double DES....................................................... 245
- 5.7.2 Triple DES....................................................... 248
- 5.7.3 Block Cipher vs. Stream Cipher............................... 251
- 5.7.4 Block/Stream Cipher Mode of Operation..................... 252
- 5.8 International Data Encryption Algorithm (IDEA).......... 265
- 5.8.1 Description of IDEA....................................... 266
- 5.8.2 Generation of Sub-Keys in IDEA............................... 269
- 5.8.3 IDEA Modes of Operation...................................... 270
- 5.9 Advanced Encryption Standard (AES)...................... 270
- 5.9.1 Processing of Plaintext...................................... 271
- 5.3 Transposition Ciphers..................................................... 213
- 5.3.1 Rail-Fence Cipher....................................................... 213
- 5.3.2 Rectangular Transposition Cipher...................................... 214
- 5.4 Steganography................................................................ 215
- 5.4.1 Limitation of Steganography....................................................... 216
- 5.4.2 Steganography Combined with Cryptography...................................... 216
- 5.5 Exercises ....................................................................... 216

## Chapter 6 Modern Symmetric Ciphers..................................................... 219

- 6.1 Introduction ............................................................ 219
- 6.2 Some Basic Concepts for Symmetric Ciphers................................ 220
- 6.2.1 Concept of Binary Block Substitution............................................. 220
- 6.2.2 Strength of the Substitution Cipher...................................... 222
- 6.2.3 Key Size for the Simple Substitution............................................... 223
- 6.3 Shannon's Theory of Diffusion and Confusion.................. 223
- 6.3.1 Diffusion....................................................................... 224
- 6.3.2 Confusion..................................................................... 224
- 6.4 Feistel Cipher.................................................................... 224
- 6.4.1 Strength of the Feistel Cipher....................................... 226
- 6.5 Data Encryption Standard (DES)................................................ 227
- 6.5.1 Description of the Critical Functions of Each Round of DES............................... 233
- 6.5.2 S-Box Transformation...................................................... 236
- 6.5.3 Generation of Sub-Keys ($K_1...K_{16}$)................................ 237
- 6.5.4 DES Decryption Algorithm............................................... 239
- 6.6 Avalanche Effect....................................................... 239
- 6.6.1 Strength of DES....................................................... 240
- 6.6.2 Possible Attacks on DES............................................... 241
- 6.6.3 Differential Cryptanalysis vs. Linear Cryptanalysis...... 245
- 6.7 Multiple DES..................................................... 245
- 6.7.1 Double DES....................................................... 245
- 6.7.2 Triple DES....................................................... 248
- 6.7.3 Block Cipher vs. Stream Cipher............................... 251
- 6.7.4 Block/Stream Cipher Mode of Operation..................... 252
- 6.8 International Data Encryption Algorithm (IDEA).......... 265
- 6.8.1 Description of IDEA....................................... 266
- 6.8.2 Generation of Sub-Keys in IDEA............................... 269
- 6.8.3 IDEA Modes of Operation...................................... 270
- 6.9 Advanced Encryption Standard (AES)...................... 270
- 6.9.1 Processing of Plaintext...................................... 271
