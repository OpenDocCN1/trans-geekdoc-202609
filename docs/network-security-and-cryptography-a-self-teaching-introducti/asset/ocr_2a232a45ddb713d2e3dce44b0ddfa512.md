Cipher-text: It refers to the encrypted form of a message. Prior to transmission, a plaintext M is encrypted so that it does not remain readily legible. The message travels from the sender to the intended recipients in cipher-text form. The cipher-text should be such that adversaries should find it extremely difficult to decipher it. The intended recipients will have the necessary keys to decipher it easily.

Encryption Algorithm: The Algorithm used for transforming plaintext to cipher-text is called an "Encryption (or Enciphering) Algorithm.\ It performs complex substitutions andor permutations over the plaintext using an encryption key to produce the resulting cipher-text.

```
$C = f(M, K_i) = E_{K_i}[M]$
```

where C is Cipher-text, M is Plaintext, $K_i$ is the Encryption Key, and E is the Encryption algorithm.

The encryption process must be reversible so as to enable deciphering of the cipher-text by the intended recipients.

+   * Decryption Algorithm: It transforms cipher-text C back to the original plaintext M. The decryption process is the reverse of the Encryption process. The intended recipients of cipher-text C will perform the decryption process using Decryption Key $K_d$ and recover plaintext M from the received cipher-text C.

```
$M = f(C, K_d) = D_{K_d}[C]$
```

where D is the Decryption algorithm.

The Key Distribution mechanism should be so secure that only the intended recipients get the decryption key and no adversary is able to lay hands on it. The authorized recipients of the key must keep it highly secure.

Since Decryption is reverse of Encryption, the following holds true:

```
$D_{K_d}[C] = D_{K_d}[E_{K_i}[M]] = (E_{K_i})^{-1}[E_{K_i}[M]] = M$
```

In the case of Symmetric Cryptography, the Decryption Key is the same as the Encryption Key. However, in the case of Asymmetric or Public Cryptography, the Decryption Key is different from the Encryption Key; the Decryption Key is related to the Encryption Key, but knowing the