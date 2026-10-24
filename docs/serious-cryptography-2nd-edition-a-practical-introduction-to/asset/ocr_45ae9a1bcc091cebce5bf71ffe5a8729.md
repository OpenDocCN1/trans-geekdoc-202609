# RSA Key Generation and Security

Key generation is the process by which an RSA key pair is created, namely, a public key (modulus n and public exponent e) and its private key (secret exponent d). As the numbers p and q (such that n = pq) and the order φ(n) should also be secret, you will often include them as part of the private key.

To generate an RSA key pair, first pick two random prime numbers, p and q, and compute φ(n) from them. Then compute d as the inverse of e. Listing 10-1 shows how this works using SageMath (https://www.sagemath.org), an open source Python-esque environment that includes many mathematical packages.

```
sage: p = random_prime(2^32); p
1103222539
sage: q = random_prime(2^32); q
17870599
sage: n = p*q; n
19715247602230861
sage: phi = (p-1)*(q-1); phi
1971524681137724
sage: e = random_prime(phi); e
13771927877214701
sage: d = xgcd(e, phi); d
15417970063428857
sage: mod(d*e, phi)
1
```

Listing 10-1: Generating RSA parameters using SageMath

Here you use the random_prime() function to pick random primes p and q, which are lower than a given argument. Next, you multiply p and q to get the modulus n and φ(n), which is the phi variable. You then generate a random public exponent, e, by picking a random prime less than phi to ensure that e has an inverse modulo phi.

You use the xgcd() function from Sage to generate the associated private exponent d. This function computes the numbers s and t given two numbers, a and b, with the extended Euclidean algorithm such that as + bt = GCD(a, b). Finally, you check that ed mod φ(n) = 1 to ensure that d correctly inverts the RSA permutation.

NOTE I've used a 64-bit modulus n in Listing 10-1 to avoid multiple pages of output, but in practice an RSA modulus should be at least 2,048 bits to be secure.

Now you can apply the trapdoor permutation, as Listing 10-2 shows.