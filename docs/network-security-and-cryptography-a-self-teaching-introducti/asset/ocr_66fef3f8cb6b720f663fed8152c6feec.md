# TABLE 6.2 Comparison between DES and AES

| Parameter | DES | AES |
| --- | --- | --- |
| Input Data Size | 64-bit | 128-bit |
| Key Size | 56-bit | 128-bit/192-bit/512-bit |
| Number of Rounds | 16 rounds (Feistel Network) | 10/12 rounds, depending on key-size (not a Feistel Network) |
| Round-Key Size | 48-bit | 128-bit |
| Number of Rounds Keys | 16 | 44/52/60; depending on key-size |
| Symmetry of Encryption and Decryption Algorithms | Yes, the only rounds in input in reverse order vis-a-vis encryption | No, the encryption and decryption algorithms are different. For each kind of transformation used in encryption, there exists an inverse transformation algorithm to be used for decryption. Also, the round keys decryption are in reverse order vis-a-vis encryption |

# 6.10 KEY MANAGEMENT: SYMMETRIC ENCRYPTION

The main issues concerning any Key Management are:

+   - Secure Distribution of Keys
- Generation of Keys

# 6.10.1 Secure Distribution of Keys

Key distribution refers to the function of delivering a secret key to two concerned parties without compromising the key. The strength of a cryptographic system lies in a foolproof Key-Distribution Technique. For Symmetric Encryption, two parties exchanging information will share a Secret Key, which must not be known to others. Also, it is advisable to change the keys frequently so to limit the amount of data that will be compromised in case of a key leak.

The Key distribution to two parties (“A” and “B”) can be achieved by any of the following techniques:

+   - “A” selects a Key and delivers it to “B” physically.
- A trusted third party can select the Key and physically deliver to “A” and “B”.
- “A” and “B” have previously exchanged a master key, a key can be exchanged that is encrypted by the master key. In this case, the issue is “how to exchange the master key securely.” Also, if an attacker gets hold of the master key, then all future keys will be compromised.