N = p q with p and q both close to some 2^b, when N = p q and some bits of p or q are known, or when N is of the form N = p^r q^r and r is greater than log p. However, detailing the reasons for these weaknesses is too technical for this book.

The upshot is that the RSA encryption and signature algorithms (see Chapter 10) need to work with a value of N = p q, where p and q are carefully chosen, to avoid easy factorization of N, which can result in a security disaster.

# Small Hard Problems Aren’t Hard

Computationally hard problems, and even exponential-time algorithms, become practical when they’re small enough. A symmetric cipher may be secure in the sense that there’s no faster attack than the 2^n-time brute force, but if the key length is n = 32, you’ll break the cipher in minutes. This sounds obvious, and you’d think that no one would be naive enough to use small keys, but in reality, there are plenty of reasons why this could happen. The following are two true stories.

Say you’re a developer who knows nothing about crypto but has some API to encrypt with RSA and has been told to encrypt with 128-bit security. What RSA key size would you pick? I’ve seen real cases of 128-bit RSA, or RSA based on a 128-bit number N = p q. However, although factoring is impractical hard for an N thousands of bits long, factoring a 128-bit number is easy. Using the SageMath software, the commands in Listing 9-2 complete instantaneously.

```
sage: p = random_prime(2**64)
sage: print(p)
6822485253121677229
sage: q = random_prime(2**64)
sage: print(q)
17596998848870549923
Sage: N = p*q
sage: factor(N)
6822485253121677229 * 17596998848870549923
```

Listing 9-2: Generating an RSA modulus by picking two random prime numbers and factoring it instantaneously

Listing 9-2 shows that you can easily factor a 128-bit number taken randomly as the product of two 64-bit prime numbers on a typical laptop. However, if I chose 1,024-bit prime numbers instead by using p = random_prime(2**1024), the command factor(p*q) would never complete, at least not in my lifetime.

To be fair, the tools available don’t help prevent the naive use of insecurely short parameters. For example, the OpenSSL toolkit used to let you generate RSA keys as short as 31 bits without any warning; such short keys are totally insecure, as Listing 9-3 shows. OpenSSL has since been fixed, and its version 1.1.1t (from February 2023) returns an error “key size too small” if you request a key shorter than 512 bits.