# 22.4 COMSET

[3] Alice decrypts $C_2$ with her key and sends Bob

$C_3 = D_A(E_B(E_A(M))) = D_A(E_A(E_B(M))) = E_B(M)$

(4) Bob decrypts $C_5$ with his key to recover $M$.

One-time pads are commutative and have perfect secrecy, but they will not work with this protocol. With a one-time pad, the three ciphertext messages would be:

```
$C_1 = P \oplus A
C_2 = P \oplus A \oplus B
C_3 = P \oplus B$
```

Eve, who can read the three messages as they pass between Alice and Bob, simply XORs them to retrieve the message:

```
$C_1 \oplus C_2 \oplus C_3 = (P \oplus A) \oplus (P \oplus B) \oplus (P \oplus B) = P$
```

This clearly wont.
Shamir (and Jim Omura) described an encryption algorithm that will work with this protocol, similar to RSA. Let $p$ be a large prime for which $p-1$ has a large prime factor. Choose an encryption key, $e$, such that $e$ is relatively prime to $p-1$. Calculate $d$ such that $de = 1 \pmod{p-1}$.
To encrypt a message, calculate

```
$C = M^e \pmod p$
```

To decrypt a message, calculate
nM = C^d \pmod p$

There seems to be no way for Eve to recover $M$ without solving the discrete logarithm problem, but this has never been proved.
Diffie-Hellman protocol allows Alice to initiate secure communication with Bob without knowing any of his keys. For Alice to use a public-key algorithm, she must know his public key. With Shamir's three-pass protocol, she just sends him a ciphertext message. The same thing with a public-key algorithm looks like:

+   [1] Alice asks Bob (or a KDC) for his public key.
[2] Bob (or the KDC) sends Alice his public key.
[3] Alice encrypts $M$ with Bob's public key and sends it to Bob.

Shamir's three-pass protocol will fall to a man-in-the-middle attack.

# 22.4 COMSET

COMSET (Communications SEUp) is a mutual identification and key exchange protocol developed for the RIPE project [1305] [see Section 25.7]. Using public-key