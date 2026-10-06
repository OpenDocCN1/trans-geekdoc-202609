# 4.2.7 A one-time pad

A one-time pad (OTP) is the only theoretically secure cipher. It was discovered by Frank Miller in 1882, and rediscovered by Gilbert Vernam and Joseph Mauborg in 1918; see Kahn (1996); Miller (1882). In simple terms, the OTP generates a Vigenere sequence with a randomly chosen key as long as the message. The one-time pad has perfect security in the sense that

```
H(M|C) = H(M),
```

where H() is the so-called Shannon entropy and H(.) is the conditional entropy. Thus, M and C are statistically independent. In other words, for every message M and ciphertext C, we can find at least one K that binds them as a one-time pad.

The intuition behind OTP security is relatively simple. Assume that we have complete statistics for every possible plaintext of the length L. For a given cryptogram and a plaintext M, there is a corresponding key K encrypting M into the cryptogram. Since every key is as likely as another, there is no clue to prove which plaintext is more likely one.

In binary notation, OTP operates with XOR (exclusive or) bitwise arithmetic, so that

```
0 ⊕ 0 = 0, 1 ⊕ 0 = 1, 0 ⊕ 1 = 1, 1 ⊕ 1 = 0.
```

For instance, if

```
m = (1111000000), k = (0011000101),
```

then

```
c = m + k = (1100101011), m = c + k = (1111000000).
```

Despite its theoretical appeal, there is a problem with OTPs — to use the OTP, we must generate a truly random key sequence, which is as long as the message we want to encode. Transferring the key is as hard as the message itself. If you wish to encrypt a computer drive, you need another drive of the same length — obviously an issue! In practice, we can use a stream cipher, which we describe.

# 4.2.8 A stream cipher

To succeed with an application of OTP, we need to have a perfectly random key. What if, instead, we try to generate a pseudo-random (but not random) “keystream” from a seed? We call the seed “real key,” the advantage that it is much shorter than the full “keystream” added to the message. Still, the set of “real keys” or seeds has to be so large, to make an exhaustive search of the search space practically impossible. If this approach is used, pseudo-randomness (rather than full randomness) is a prerequisite, since both sender and receiver must receive the same key from the seed. The very nature of pseudo-random generators, their output is periodic, which is a problem in theory, but less so in practice, provided that the period is long enough. In this case, if the key is unknown, every output bit is unpredictable.