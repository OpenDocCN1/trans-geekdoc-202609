
# 认证协议

An `authentication protocol` is a set of rules that exchanges authentication data between two or more entities, allowing them to operate securely with minimal effort. A simple example of Point-to-Point Protocol (PPP) authentication protocol goes like this:

> Bob sends Alice his password in a packet. Alice checks Bob’s received password against the one saved in her database. If the password is correct, she sends a packet with an acknowledgment of successful authentication; if not, Bob is denied.

Common authentication protocols include PPP, Extensible Authentication Protocol (EAP), Kerberos, Challenge-handshake authentication protocol (CHAP), Password Authentication Protocol (PAP), Secure Shell protocol (SSH), and Shiva Password Authentication Protocol (SPAP).

## 6.6 Modern Encryption

As we discussed earlier, cryptographic techniques have been used for thousands of years for secure communication. The need for people to exchange data easily and securely became more important with the introduction of computers. Encryption is one of the most effective ways to protect data by scrambling data into secret codes, called ciphers, as they travel across the Internet.

Complex encryption algorithms have been developed that are hard to break. The summary below describes a general understanding of modern encryption methods that can protect `data at rest`, `data in transit`, and `data in use`. It can also keep data safe from lost and stolen computers. However, encryption can also be used by cybercriminals to encrypt data after a ransomware attack, making it almost impossible to retrieve and use. Encryption can be good or evil, protecting us or used as a weapon against us.

### 6.6.1 Symmetric Encryption or Secret Key Cryptography (SKC)

Symmetric encryption method, also referred to as symmetric key cryptography, secret key, or shared secret, is a method that uses the same key to both encrypt and then decrypt a message. A simple example of symmetric encryption is the Caesar cipher, described earlier, which shifts each letter a fixed number of places. Another example occurred in 1586 when Blaise de Vigenère used an entire word as the shift key.^([^(333)](#fn333))

Since the device uses only one key for both encryption and decryption, symmetric encryption may be vulnerable. Another drawback to symmetric encryption is that all parties must exchange the key (key sharing), to encrypt and decrypt data, and this is not always convenient. To solve this problem, another type of encryption, asymmetric encryption, creates a pair of keys, one public and one secret. The following is a simple example of symmetric encryption.

Bob and Alice need the same secret key for decryption and encryption. Bob and Alice must first exchange the secret key so that they can communicate privately. When Bob and Alice would like to store private information, they always store it in an encrypted form, using their secret key. If the server or cloud is compromised by someone else, no one can read their messages because the data is encrypted.

In other words, a cryptographic algorithm converts data into an unreadable form like `qJ4#j!UFO&Cps3#6@tc#Rb50`. Returning it to its original form by decrypting it requires a key or a password.

A symmetric key cipher can be Block Cipher or Stream Cipher. Block Cipher is used to encrypt blocks of data, frequently 64 or 128 bits. For example, the cipher may encrypt a 64-bit block and will return the blocks of cipher text in the same size.^([^(334)](#fn334))

![FIGURE 6.22 The length of the AES encryption.](images/fig6.22.jpg)

**FIGURE 6.22** The length of the AES encryption.

*   Data Encryption Standard (DES) (uses 56-bit key length)
*   Advance Encryption Standards (AES) (uses 128-bit, 192-bit, or 256-bit keys)
*   Blowfish (key lengths vary from 32 to 448-bits length)
*   RC4 (Rivest Cipher 4) (key can be any length up to 2048 bits)
*   RC5 (Rivest Cipher 5) key size up to 2040 bits)
*   RC6 (Rivest Cipher 6) (key sizes of 128, 192, and 256 bits up to 2040 bits)
*   3DES (uses key length 56, 112, or 168 bits)
*   IDEA (International Data Encryption Algorithm) (encrypts 64-bit blocks using 128-bit key) and ChaCha20 (Google has replaced RC4 with ChaCha20 stream cipher) algorithms. ^([^(335)](#fn335))
*   Another stream cipher the Salsa20, which is related to ChaCha20, takes a 256-bit key. So far, researchers have not found any vulnerabilities in ChaCha20 algorithm.^([^(336)](#fn336))

The key lengths indicate the number of bits in a solution used by a cryptographic algorithm. We can’t cover all the different types of encryption algorithms, but we will look at the most common.

In 1970s, IBM developed its DES, which was the first major symmetric algorithm developed for computers in the United States.^([^(337)](#fn337))

The AES is one of the most widely used symmetric encryption ciphers. It uses 128-bit, 192-bit, or 256-bit keys. [Figure 6.22](#c6.xhtml#f6.22) demonstrates the length of its encryption.

If a computer tries `2^(40)` (1,099,511,627,7760) solutions per day, it will take approximately about 848 sextillion years to brute-force the solution to a 128-bit key.

The IDEA was developed in 1991. It works with 64-bit block of data and uses a 128-bit key.^([^(338)](#fn338))

![FIGURE 6.23 Symmetric encryption.](images/fig6.23.jpg)

**FIGURE 6.23** Symmetric encryption.

### 6.6.2 Asymmetric Encryption or Public Key Cryptography or Asymmetric Cryptography

We have used cipher systems or symmetric encryption for thousands of years. In 1976, a revolutionary paper by Whitfield Diffie and Martin Hellman titled “New Directions in Cryptography” proposed a major change.^([^(339)](#fn339))

This type of encryption uses two mathematically different but connected cryptographic keys. Instead of a single key as in symmetric encryption, the public key encryption system uses a pair of keys. One key is public, and the other is a private or secret key. The public key may be accessed by anyone, and the private key only by the owner.

The sender encrypts a message using the receiver’s public key; however, the receiver can only decrypt this encrypted message with his or her private key. One key will not reveal the other.

The keys are linked mathematically so that anything encrypted with key “A” can only be decrypted with key “B.”

*   A sender can use a recipient’s public key to encrypt the message; then, only the recipient can decrypt using his or her private key.
*   Or, the message can be encrypted using both the sender’s private key and the recipient’s public key.
*   If the sender encrypts a message with his private key, it can be decrypted by anyone that has the matching public key.
*   A recipient with the sender’s public key can verify that it was the sender who created the message. This is called a digital signature. In other words, the sender and the recipient only need to exchange public keys, which can be done over open communication lines. Because the public key is available to everyone, other parties can use it to encrypt messages. As a result, every user must generate a pair of public and private keys. The mathematics behind the asymmetric encryption is extraordinarily complex and beyond the scope of this chapter.

The public and private keys are associated with each other via a mathematical relationship. It is not feasible to calculate the private key from the public key because the mathematical relationship cannot work backward. In comparison with symmetric encryption, asymmetric encryption is much slower but offers better security because of the two different keys. [Figure 6.24](#c6.xhtml#f6.24) demonstrates the Asymmetric Encryption or Public Key Cryptography (PKC).
