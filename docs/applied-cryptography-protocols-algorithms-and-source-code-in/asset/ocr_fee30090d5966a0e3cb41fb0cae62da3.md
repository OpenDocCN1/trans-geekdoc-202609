# 21.3 Schnorr 511

choose two primes, $p$ and $q$, such that $q$ is a prime factor of $p - 1$. Then, choose an $a$ not equal to 1, such that $a^q \equiv 1 \pmod p$. All these numbers can be common to a group of users and can be freely published.

To generate a particular public-key/private-key pair, choose a random number less than $q$. This is the private key, $s$. Then calculate $v = a^s \pmod p$. This is the public key.

# Authentication Protocol

+   [1] Peggy picks a random number, $r$, less than $q$, and computes $x = a^r \pmod p$. This is the preprocessing stage and can be done long before Victor is present.

+   [2] Peggy sends $x$ to Victor.

+   [3] Victor sends a random number, $e$, between 0 and $2' - 1$. [I'll discuss $t$ in a moment.]

+   [4] Peggy computes $y = (r + se) \pmod q$ and sends $y$ to Victor.

+   [5] Victor verifies that $x = a^v \pmod p$.

The security is based on the parameter $t$. The difficulty of breaking the algorithm is about $2^t$. Schnorr recommended $p$ to be about 512 bits, $q$ be about 140 bits, and $t$ be 72.

# Digital Signature Protocol

Schnorr can also be used as a digital signature protocol on a message, $M$. The public-key/private-key pair is the same, but we're now adding a one-way hash function, $H[M]$.

+   [1] Alice picks a random number, $r$, less than $q$, and computes $x = a^r \pmod p$.
This computation is the preprocessing stage.

+   [2] Alice concatenates $M$ and $x$, and hashes the result:

```
$e = H[M,x]$
```

+   [3] Alice computes $x' = a^{v'} \pmod p$. The signature is $e$ and $y$; she sends $y$ to Bob.

+   [4] Bob computes $x' = y^v \pmod p$. He then confirms that the concatenation of $M$ and $x'$ hashes to $e$.

```
$e = H[M,x']$
```

If it does, he accepts the signature as valid.

In his paper, Schnorr cites these novel features of his algorithm:

Most of the computation for signature generation can be completed in a preprocessing stage, independent of the message being signed. Hence, it can be done dur