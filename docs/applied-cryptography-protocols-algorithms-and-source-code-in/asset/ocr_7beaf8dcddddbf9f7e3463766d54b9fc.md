# CHAPTER 1 Foundations

![](bbox=[0.172, 0.125, 0.653, 0.233])

Figure 1.3 Encryption and decryption with two different keys.

eavesdropper knows your algorithm, if she doesn't know your particular key, she can't read your messages.
A cryptystem is an algorithm, plus all possible plaintexts, ciphtexts, and keys.

# Symmetric Algorithms

There are two general types of key-based algorithms: symmetric and public-key.
Symmetric algorithms, sometimes called conventional algorithms, are algorithms where the encryption key can be calculated from the decryption key and vice versa. In most symmetric algorithms, the encryption key and the decryption key are the same. These, also called secret-key algorithms, single-key, or one-key algorithms, require that the sender and receiver agree on a key before they can communicate securely. The security of a symmetric algorithm rests in the key; divulging the key means that anyone could encrypt and decrypt messages. As long as the communication remains secret, the key must remain secret.
Encryption and decryption with symmetric algorithm are denoted by:

```
E(M) = C
D(C) = M
```

Symmetric algorithms can be divided into two categories. Some operate on the plaintext a single bit (or sometimes byte) at a time; these are stream algorithms or stream ciphers. Others operate on the plaintext in groups of bits. The groups of bits are called blocks, and the algorithms are called block algorithms or block ciphers. For modern computers, a typical block size is 64 bits—large enough to preclude analysis and small enough to be workable.(Before computers, algorithms generally operated on one character at a time. You can think of this as a symmetric algorithm operating on a stream of characters.)

# Public-Key Algorithms

Public-key algorithms (also called asymmetric algorithms) are designed so that the key used for encryption is different from the key used for decryption. Furthermore, the decryption key cannot (at least in reasonable amount of time) be calculated from the encryption key. The algorithms are called "public-key" because the encryption key can be made public: A complete stranger can use the encryption key to encrypt a message, but only a specific person with the corresponding decryp