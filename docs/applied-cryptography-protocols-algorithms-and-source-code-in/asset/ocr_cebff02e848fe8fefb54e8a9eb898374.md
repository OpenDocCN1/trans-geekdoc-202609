# CHAPTER 20 Public-Digital Signature Algorithms

Table 20.1
DSA Signatures

Public Key:
p 512-bit to 1024-bit prime [can be shared among a group of users]
q 160-bit prime factor of $p-1$ [can be shared among a group of users]
g = h^{(p-1)/q} mod p$, where $h$ is less than $p-1$ and $h^{(p-1)/q} mod p > 1$ (can be shared among a group of users)
y = g^k mod p (a p-bit number)

Private Key:
x $< q$ (a 160-bit number)

Signing:
k choose at random, less than $q$
r (signature) = [g^k mod p] mod q
s (signature) = [k^{-1}(H(m) + xr)] mod q

Verifying:
w = s^{-1} mod q
u1 = (H(m) \cdot w) mod q
u2 = (rw) mod q
v = ||g^u y^v| mod q
If $v = r$, then the signature is verified.

# DSA Prime Generation
Lenstra and Haber pointed out that certain moduli are much easier to crack than others [950]. If someone forced a network to use one of these “cooked” moduli, then their signatures would be easier to forge. ThisThis is not a problem for two reasons: moduli are easy to detect and they are so rare that the chances of using one when choosing a modulus randomly are almost negligible—smaller, in fact, the chances of accidentally generating a composite number using a probabilistic generation routine.
[1154] NIST recommended a specific method for generating the two primes, $p$ and $q$, where $q$ divides $p-1$. The prime $p$ is bits long, between 512 and 1024 bits

# Table 20.2
DSA Speeds for Different Modulus Lengths
with a 160-bit Exponent (on a SPARC II)

| | 512 bits | 768 bits | 1024 bits |
|---|---|---|--|
| Sign | 0.20 sec | 0.43 sec | 0.57 sec |
| Verify | 0.35 sec | 0.80 sec | 1.27 sec |