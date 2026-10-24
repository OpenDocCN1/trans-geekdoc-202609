
## 10 RSA 205

- RSA Implementations .................................... 205
- A Fast Exponentiation Algorithm ............................. 206
- Small Exponents for Faster Public-Key Operations ............ 208
- The Chinese Remainder Theorem ............................... 210
- How Things Can Go Wrong ................................... 211
  - The Bellcore Attack on RSA-CRT .............................. 211
  - Shared Private Exponents or Moduli .......................... 212
- Further Reading ........................................... 213

## 11 Diffie-Hellman 215

- The Diffie–Hellman Function ................................ 216
- The Diffie–Hellman Problems ................................ 218
  - The Computational Problem .................................. 218
  - The Decisional Problem ..................................... 218
- Variants of Diffie–Hellman ................................. 219
- Key Agreement Protocols .................................... 219
  - Non-DH Key Agreement ....................................... 219
  - Attack Models for Key Agreement Protocols ................... 221
  - Performance ............................................... 222
- Diffie–Hellman Protocols ................................... 223
  - Anonymous Diffie–Hellman ................................... 223
  - Authenticated Diffie–Hellman ............................... 224
  - Menezes–Qu–Vanstone ....................................... 227
- How Things Can Go Wrong .................................... 228
  - Not Hashing the Shared Secret ............................... 228
  - Anonymous Diffie–Hellman from TLS 1.0 ....................... 229
  - Unsafe Group Parameters .................................... 229
- Further Reading ............................................ 230

## 12 Elliptic Curves 231

- What Is an Elliptic Curve? ................................. 232
- Elliptic Curves Over Integers ............................... 233
- The Addition Law ........................................... 235
- Elliptic Curve Groups ...................................... 239
- The ECDLP Problem .......................................... 240
- Diffie–Hellman Key Agreement over Elliptic Curves ........... 241
- Signing with Elliptic Curves ............................... 241
  - ECDSA Signature Generation ................................. 242
  - ECDSA Signature Verification ............................... 242
  - ECDSA vs. RSA Signatures ................................... 243
  - EdDSA and Ed25519 .......................................... 244
- Encrypting with Elliptic Curves ............................. 246
- Choosing a Curve ........................................... 246
  - NIST Curves ............................................... 247
  - Curve25519 ................................................ 248
  - Other Curves .............................................. 248
- How Things Can Go Wrong ........................................ 249
  - ECDSA with Bad Randomness ...................................... 249
  - Invalid Curve Attacks ........................................... 249
  - Incompatible Ed25519 Validation Rules .......................... 250
- Further Reading ................................................... 251

## Part IV: Applications ........................................... 253

## 13 TLS ............................................................ 255

- Target Applications and Requirements ........................... 256
- The TLS Protocol Suite ........................................... 256
  - The TLS and SSL Families of Protocols .......................... 257
  - TLS in a Nutshell .............................................. 257
  - Certificates and Certificate Authorities ....................... 258
  - The Record Protocol ............................................. 262
  - The TLS Handshake Protocol ..................................... 263
  - TLS 1.3 Cryptographic Algorithms ............................... 265
- TLS 1.3 Improvements over TLS 1.2 ................................. 266
  - Downgrade Protection ............................................ 266
  - Single Round-Trip Handshake .................................... 267
  - Session Resumption .............................................. 267
- The Strengths of TLS Security ..................................... 268
  - Authentication .................................................. 268
  - Forward Secrecy ................................................. 268
- How Things Can Go Wrong ............................................ 269
  - Compromised Certificate Authority ............................... 269
  - Compromised Server .............................................. 269
  - Compromised Client .............................................. 270
  - Bugs in Implementations ......................................... 270
- Further Reading .................................................... 271

## 14 Quantum and Post-Quantum ........................................ 273

- How Quantum Computers Work ...................................... 274
  - Quantum Bits ................................................... 274
  - Quantum Gates ................................................... 277
- Quantum Speedup ................................................... 279
  - Exponential Speedup and Simon’s Problem ......................... 280
  - The Threat of Shor’s Algorithm .................................. 281
  - Grover’s Algorithm .............................................. 282
- Why Is It So Hard to Build a Quantum Computer? .................... 284
- Post-Quantum Cryptographic Algorithms ............................. 285
  - Code-Based Cryptography ......................................... 285
  - Lattice-Based Cryptography ...................................... 286
  - Multivariate Cryptography ....................................... 287
  - Hash-Based Cryptography ......................................... 288
- The NIST Standards ................................................. 289
- How Things Can Go Wrong ............................................ 291
  - Unclear Security Level ............................................ 291
  - The Eventual Existence of Large Quantum Computers ................ 291
  - Implementation Issues ............................................. 292
- Further Reading .................................................... 293

## 15 Cryptocurrency Cryptography

- Hashing Applications .......................................... 296
  - Merkle Trees ................................................ 297
  - Proof of Work ................................................ 300
  - Hierarchical Key Derivation ................................ 301
  - Algebraic Hash Functions .................................... 302
  - How Things Can Go Wrong ...................................... 304
- Multisignature Protocols ..................................... 306
  - Multiple Multiparty Signatures .............................. 306
  - Schnorr Signature Protocols .................................. 307
  - How Things Can Go Wrong ...................................... 309
  - Safer Schnorr Multisignatures ................................ 310
- Aggregate Signature Protocols ................................ 311
  - Pairings .................................................... 312
  - BLS Signatures .............................................. 312
  - How Things Can Go Wrong ...................................... 314
- Threshold Signature Protocols ............................... 316
  - Use Cases ................................................... 316
  - Security Model .............................................. 317
  - Secret-Sharing Techniques ................................... 319
  - The Trivial Case ............................................. 320
  - The Simple Case .............................................. 320
  - The Hard Case ................................................ 321
  - How Things Can Go Wrong ...................................... 321
- Zero-Knowledge Proofs ........................................ 323
  - Security Model .............................................. 324
  - Schnorr’s Protocol ........................................... 325
  - Noninteractive Proofs ........................................ 326
  - zkSNARKs ..................................................... 327
  - From Statements to Proofs ................................... 328
  - How Things Can Go Wrong ...................................... 329
- Really Serious Crypto ........................................ 330

## Index ........................................................ 333
