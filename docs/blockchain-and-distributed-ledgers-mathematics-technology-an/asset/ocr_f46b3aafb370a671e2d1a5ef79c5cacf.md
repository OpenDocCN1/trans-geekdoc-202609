# Chapter 4 Essential Cryptographic Tools | 87

![](bbox=[0.127, 0.078, 0.863, 0.477])

**Figure 4.3** Conceptual framework for asymmetric cryptography, which relies on two linked keys: (a) public key is used to encrypt text; secret key is used to decrypt ciphertext; (b) secret key is used to sign a message; public key is used to verify the signature; (c) both public and secret keys are used to create a common secret. Own graphics.

for encryption and decryption. The realization that this is possible and, in many instances, desirable, opens a new chapter in cryptography — the so-called public-key cryptography relying on public-key infrastructure (PKI). In Figure 4.3 (a), we graphically represent the corresponding encryption — decryption paradigm; in Figure 4.3 (c), we show the digital signature algorithm; while in how two parties can create a common secret.

As we have two protagonists Alice and Bob and an antagonist, Charlie. In Figure 4.3 (a), Alice uses Bob’s public key that is readily available to encrypt a message, which only Bob can decrypt using his secret key that is known only to her. Charlie tries to decrypt the message intended for Bob and replace it with a forged one. In Figure 4.3 (b), Alice uses her secret key to sign a message or its hash. What is hashing? It is an algorithm for creating a unique digest of fixed length out of message of an arbitrary length. We shall discuss hashing algorithms later in this chapter since they are created by Bitcoin and all other blockchain protocols. Her signature can be checked by Bob (anyone for that matter). Charlie tries to create a forged message and proves that Alice

> Typically, a hash function is 166–250 bit and provides as half as much, i.e., 80–128 “bits” of security due to the Birthday Paradox, which we discuss below.