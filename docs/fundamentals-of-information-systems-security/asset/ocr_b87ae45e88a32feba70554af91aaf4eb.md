> **Technical TIP**
> 
> Not all cryptographic ciphers require keys. Some newer types of cryptographic algorithms derive their keys from other information. This approach is similar to access controls that use inputs other than passwords. For example, **identity-based encryption (IBE)** uses the encryptor's identity to derive a key. **Attribute-based encryption (ABE)** uses descriptive attributes to encrypt and decrypt data.

Most common encryption ciphers require plaintext and at least one key as input. The encryption cipher uses the cryptographic key to vary its output so that the intended correspondents can protect their information from anyone else who has the same cipher. By changing the key, you change the output of the cryptographic function, even if the plaintext remains the same.

Encryption ciphers fall into two general categories:

+   - Those that use the same key to encrypt and decrypt are **private (symmetric) key ciphers**.
+   - Those that use different keys to encrypt and decrypt are **public (asymmetric) key ciphers**.

Sometimes, the terms *public key* and *private key* refer to the two different keys in asymmetric ciphers. Together they are a key pair. To avoid confusion, the *symmetric* and *asymmetric* naming convention for ciphers is used here. Note, however, that many sources interchange these terms freely.

> **TIP**
> 
> **Key-stretching** techniques can make a weak key more resistant to brute-force attacks. A key-stretching function takes a key (generally a weak key) as input and generates an enhanced key that can withstand a more determined attack.

# Basic Cryptographic Principles

A perfect cipher does not exist. Given sufficient time and resources, an attacker can eventually decrypt any ciphertext. The goal of cryptography is to make the cost or the time required to decrypt ciphertext without the key exceed the value of the protected information. Thus, you could effectively protect information that is worth no more than $100 with a cipher that costs $1,000 to break. This is an important concept. It provides one of

the basic rationales for selecting cryptographic tools and ciphers.

The number of possible keys to a cipher is a **keyspace**. Without any knowledge of the key, an attacker with access to an encrypted message and the decryption cipher could try every possible key to decode the message. This is a brute-force attack. By making the keyspace large enough, you make the cost of a brute-force attack too high. Assuming that the cipher has no mathematical weaknesses, a larger keyspace usually means more security.

There are public (open-source) ciphers and hidden (closed-source or proprietary) ciphers. **Open ciphers** make it possible for experts around the world to examine the ciphers for weaknesses. Experts subject open-source ciphers to extensive analysis. They find flaws and weaknesses that could diminish the cipher's strength. Any cipher is far more secure if it withstands public scrutiny without anyone identifying major flaws. The most scrutinized cipher in history is the **Data Encryption Standard (DES)**, published in 1977 as Federal Information Processing Standard (FIPS) 46. Modern computing has searched its keyspace of 72 quadrillion keys without finding a single mathematical weakness.