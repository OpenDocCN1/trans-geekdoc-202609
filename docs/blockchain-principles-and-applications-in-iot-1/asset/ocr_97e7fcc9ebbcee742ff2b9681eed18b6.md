# 13

# Cryptographic Foundations of Blockchain Technology

C. Tezcan
Middle East Technical University, Ankara, TURKEY

+   CONTENTS
13.1 Introduction ................................................................................ 221
13.3.1 Methodology ............................................................................ 222
13.2 Blockchain Technology ................................................................... 223
13.2.1 Blocks ..................................................................................... 225
13.2.2 Consensus Models ....................................................................... 225
13.2.3 Forking ................................................................................... 226
13.3 Cryptographic Hash Functions ........................................................ 226
13.3.1 Hash Puzzles ............................................................................ 229
13.4 Public-Key Cryptography ................................................................ 231
13.5 Post-Quantum Cryptography ....................................................... 235
13.6 Zero-Knowledge Protocols ............................................................... 236
13.7 Lightweight Cryptography ............................................................. 236
13.8 Conclusion ................................................................................. 239
References ........................................................................................ 239

# 13.1 Introduction

Many proposed cryptographic payment systems, both credit card and e-cash-based technologies, are proposed in the last 30 years and almost all of them have failed until the introduction of Bitcoin [1], the first modern cryptocurrency, in 2008. Bitcoin combined the blockchain idea with some other technologies and cryptographic primitives to provide an electronic cash that does not require central repository or authority.

Blockchains are digital ledgers composed of blocks where cryptographic hash functions provide tamper resistance and tamper resistance. Basically, they enable users in a community to record transactions in a shared ledger that once it is recorded it is not allowed to change a transaction and it is easy to detect if a malicious user modifies a recorded transaction.

Security of blockchains depends heavily on cryptographic algorithms. For instance, security of Bitcoin and similar blockchains depends on the security of the used digital signature algorithms and cryptographic hash functions. In time, new cryptographic algorithms are added to blockchains and some old algorithms are broken.