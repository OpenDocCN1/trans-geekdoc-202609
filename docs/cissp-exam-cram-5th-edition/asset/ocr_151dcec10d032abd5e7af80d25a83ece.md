| 1 0 | 0 | 1 | 1 | 0 | 1 |
|---|---|---|---|---|---|
| 1 1 | 1 | 1 | 0 | 0 | 0 |

Stream ciphers operate at a higher speed than block ciphers and, in theory, are well suited for hardware implementation.

# Symmetric Encryption

In symmetric encryption, a single shared secret key is used for both encryption and the decryption, as shown in Figure 4.14. The key is referred to as a dual-use key because it is used to lock and unlock data. Symmetric encryption is the oldest form of encryption; scytale and Caesar's cipher are examples of it (see Chapter 5, “Communications and Network Security”). Symmetric encryption provides confidentiality by keeping individuals who do not have the key from knowing the true contents of the message.

![](bbox=[0.115, 0.463, 0.842, 0.656])

FIGURE 4.14 Symmetric Encryption

The simple diagram in Figure 4.14 shows the symmetric encryption process. Plaintext is encrypted with the single shared key, resulting in ciphertext; the ciphertext is then transmitted to the message’s recipient, who reverses the process to decrypt the message. Symmetric encryption and decryption are fast, and symmetric encryption is very hard to break if a large key is used. However, it has three significant disadvantages:

+   ▶ Distribution of the symmetric key