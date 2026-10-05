# CHAPTER 22 Key-Exchange Algorithms

# Patents

The Diffie-Hellman key-exchange algorithm is patented in the United States [718] and Canada [719]. A group called Public Key Partners (PKP) licenses the patent, along with other public-key cryptography patents (see Section 25.5). The U.S. patent will expire on April 29, 1997.

# 22.2 STATION-TO-STATION PROTOCOL

Diffie-Hellman key exchange is vulnerable to a man-in-the-middle attack. One way to prevent this problem is to have Alice and Bob send their messages to each other [500]. This protocol assumes that Alice has a certificate with Bob's public key and Bob has Bob with Alice's public key. These certificates have been signed by some trusted authority outside this protocol. Here's how Alice and Bob generate a secret key, k.

+   (1) Alice generates a random number, x, and sends it to Bob.
(2) Bob generates a random number, y. Using the Diffie-Hellman protocol he computes their shared key based on x and y; k. He signs x and y, and then sends that, along with y, to Alice. Alice signs the signature using k. E_A(S_B(x,y))
(3) Alice also computes k. She decrypts the rest of Bob's message and verifies her signature. She sends Bob a signed message consisting of x and y, encrypted in their shared key.
$E_B(S_A(x,y))
(4) Bob decrypts the message and verifies Alice's signature.

# 22.3 SHAMIR'S THREE-PASS PROTOCOL

This protocol, invented by Adi Shamir but never published, enables Alice and Bob to communicate securely without any advance exchange of secret keys or public keys [1008].nThis assumes the existence of a symmetric cipher that is commutative, that is:

```
$E_A(E_B[P]) = E_B(E_A[P])$
```

Alice's secret key is A. Bob's secret key is B. Alice wants to send a message, M, to Bob. Here's the protocol.

+   (1) Alice encrypts M with her key and sends Bob
$C_1 = E_A(M)$
(2) Bob encrypts C_1 with his key and sends Alice
$C_2 = E_B(E_A[M])$