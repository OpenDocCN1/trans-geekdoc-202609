# 1.1 Terminology

tion key can decrypt the message. In these systems, the encryption key is often called the **public key**, and the decryption key is often called the **private key**. The private key is sometimes called the secret key, but to avoid confusion with symmetric algorithms, that tag won't be used here.
Encryption using public key $K$ is denoted by:

```
$E_K(M) = C$
```

Even though the public key and private key are different, decryption with the corresponding private key is denoted by:

```
$D_K(C) = M$
```

Sometimes, messages will be encrypted with the private key and decrypted with the public key; this is used in digital signatures (see Section 2.6). Despite the possibility, these operations are denoted by, respectively:

```
$E_K(M) = C$
D_K(C) = M$
```

# Cryptanalysis

The whole point of cryptography is to keep the plaintext [or the key, or both] secret from eavesdroppers [also called adversaries, attackers, interceptors, interlopers, intruders, opponents, or simply the enemy]. Eavesdroppers are assumed to have complete access to the communications between the sender and receiver.

Cryptanalysis is the science of recovering the plaintext of a message without access to the key. Successful cryptanalysis may recover the plaintext or the key. It also results in weaknesses in a cryptographic system [The loss of a key through noncryptanalysis is called a **compromise**].

An attempted cryptanalysis is called an attack. A fundamental assumption in cryptanalysis, first encountered by the Dutch A Kerckhoffs in the nineteenth century, is that the secrecy reside entirely in the key [794]. Kerckhoffs assumes that the cryptyst has complete details of the cryptographic algorithm and implementation. Of course, one would assume that the CIA does not make a hit of telling Mossad about its cryptographic algorithms, but Mossad probably finds out. While real-world cryptanalysts don't always have such detailed information, it is a good assumption to make. If others can't break an algorithm, even with knowledge of how it works, they certainly won't be able to break it without knowledge.

There are four general types of cryptanalytic attacks. Each of them assumes that the cryptanalyst has complete knowledge of the encryption algorithm used:

+   1. **Ciphertext-only attack**. The cryptanalyst has the ciphertext of several messages, all of which have been encrypted using the same encryption algorithm. The cryptanalyst's job is to recover the plaintext of as many messages as possible, or better yet to deduce the key [or keys] used to