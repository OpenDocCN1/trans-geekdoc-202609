g^{ba} mod p

Similarly, with his private value, b, Bob can calculate (y^a)^b from the received A-nonce:

g^{ab} mod p

But guess what: Mathematically, g^{ba} mod p and g^{ab} mod p are equivalent. So, in fact, Bob and Alice have just, securely, exchanged a new secret key.

Diffie-Hellman is vulnerable to man-in-the-middle attacks because the key exchange does not authenticate the participants. To prove authenticity, digital signatures and digital certificates—by accepting someone's public key in advance, sometimes within a PKI—should be used. Diffie-Hellman is used in conjunction with several authentication methods, including the Internet Key Exchange (IKE) component of IPsec.

The following are some important facts you should know about Diffie-Hellman:

+   It was the first asymmetric algorithm.

+   It provides key-exchange services.

+   It is considered a key agreement protocol.

+   It operates by means of discrete logarithms.

# RSA

RSA was developed in 1977 by Ron Rivest, Adi Shamir, and Len Adleman at MIT. The cipher's name is based on their initials. Although RSA is much slower than symmetric encryption cryptosystems, it offers symmetric key exchange and is considered very secure. RSA is based on factoring prime numbers, but to be secure, it has to use prime numbers whose product is much larger than 129 digits. Decimal numbers less than 130 digits have been factored using a number field sieve algorithm. You do not need to know the inner workings of RSA public and private key generation for the CISSP exam, but the information in this section will be useful for you as a security professional.

Typically, the plaintext is broken into equal-length blocks, each with fewer