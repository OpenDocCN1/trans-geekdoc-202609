# 19.6 ElGamal

and use the extended Euclidean algorithm to solve for $b$ in the following equation:

$M = (xa + kb) \mod (p - 1)$

The signature is the pair: $a$ and $b$. The random value, $k$, must be kept secret.
To verify a signature, confirm that

$y = g^x \mod p = g^k \mod p$

Each ElGamal signature or encryption requires a new value of $k$, and that value
be chosen randomly. If Eve ever recovers a $k$ that Alice used, she can recover
Alice's private key, $x$. If Eve gets two messages signed or encrypted using the
same $k$, even if she doesn't know what it is, she can recover $x$.
This is summarized in Table 19.5.

For example, choose $p = 11$ and $g = 2$. Choose private key $x = 8$. Calculate

$y = g^x \mod p = 2^8 \mod 11 = 3$

The public key is $y = 3, g = 2$, and $p = 11$.
Authenticate $M = 5$, first choose a random number $k = 9$. Confirm that $gcd[9,10]
= 1$. Compute

$a = g^k \mod p = 2^9 \mod 11 = 6$

and use the extended Euclidean algorithm to solve for $b$:

$M = (ax + kb) \mod (p - 1)$
$5 = (8 \cdot 6 \cdot 9) \mod 10$

The solution is $b = 3$, and the signature is the pair: $a = 6$ and $b = 3$.

| Table 19.5 |
| ElGamal Signatures |
| Public Key: |
| p prime (can be shared among a group of users) |
| g < p (can be shared among a group of users) |
| y = $g^x \mod p$ |
| Private Key: |
| x < p |
| Signing: |
| k choose at random, relatively prime to $p-1$ |
| a (signature) = $g^k \mod p$ |
| b (signature) such that $M = (xa + kb) \mod (p - 1)$ |
| Verifying: |
| Accept as valid if $y^a b^M \mod p = g^M$ |