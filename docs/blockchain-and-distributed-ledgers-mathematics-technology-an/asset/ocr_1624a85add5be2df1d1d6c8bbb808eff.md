# Chapter 4 Essential Cryptographic Tools | 123

Parameters $a, b$ were chosen verifiably at random from the seed $S$, chosen randomly and fixed afterwards. The idea of selecting parameters from seed is simple, as its implementation is complex; we do not cover it in this book, referring the reader to Certicom Research (2009). In a nutshell, the algorithm proceeds as follows:

```
$S = c49d360886e704936a678e1139d26b7819f7e290,$
```

```
$H = h(S), \quad a = a(H), \quad b = \beta(H).$
```

where $h$ is a cryptographic hash function defined in the next section, which is easy to compute but impossible to invert. The choice of $G$ is less important. For the moment, it is sufficient to know that such a function is straightforward to compute tough to invert. The functions $a(\), \beta(\)$ are known and can be inverted.

Thus, if one were to find particular $H$, which would make the corresponding EC vulnerable, it can be written as:

```
$H = \alpha^{-1}(a) = \beta^{-1}(b).$
```

However, finding a seed $S$, such that

```
$S = h^{-1}(H),$
```

is practically impossible.

# 4.7.9 Elliptic curve digital signature algorithm

We can now collect all pieces and formally define the all-important elliptic curve signature algorithm (ECDSA), being the Bitcoin protocol's heart.

The ECDSA is similar to the ElGamal DSA described earlier. The main difference is that the former employs elliptic curves instead of discrete logarithms, as the latter. Choose the $E_T$ with parameters $T = (p, a, b, G, n, h)$, pick a random integer $k$ and compute

```
$A = k \times G.$
```

The public key (or address) is the point $A$, and the secret key is a single integer $k$. Note that Eq. (4.151) is practically impossible to invert by the existing methods because of the enormous number of points on secp256k1, or any other EC suitable for cryptographic purposes.

The ECDSA proceeds as follows. To sign a message $m$, which is an integer less than $p$, we choose a random integer $l$, which is coprime with $gcd(l,n) = 1$, so that $l^{-1} \mod n$ exists, calculate

```
$B = l \times G,$
```

and represent the signature as a pair:

```
$(r, s) = (r, (m + kr)l^{-1}),$
```

where $r = B_x$. It is worth mentioning that $B_y$ is not used by the algorithm and is not revealed, although it is trivial to calculate modulo $p$. Two points are in order: (a) one should