# CHAPTER 7

# PUBLIC-KEY CRYPTOGRAPHY
FOR DATA CONFIDENTIALITY

Chapter Outline

+   - Introduction
- Requirements of Public-Key Cryptography
- Data Confidentiality using Public-Key Cryptography
- RSA Algorithm
- Key Management Using Public-Key Cryptography
- ElGamal Encryption Scheme
- Elliptic Curve Cryptography (ECC)
- Exercises

# 7.1 INTRODUCTION

Public-Key Cryptography is based on the concept of two keys for each user, that is a Private Key which is kept secret by the user and a Public Key that is made available to all other users in the cryptystem. Though both keys belonging to a user are related to each other, one cannot determine the private key of another user by knowing its related public key.

# 7.2 REQUIREMENTS OF PUBLIC-KEY CRYPTOGRAPHY

+   1. Each user generates a pair of keys: for example, a user “N” may generate Public Key $PU_A$ and Private Key $PR_A$.