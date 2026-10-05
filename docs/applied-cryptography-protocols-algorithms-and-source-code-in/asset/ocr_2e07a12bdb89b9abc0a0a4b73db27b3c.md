# 19.3 RSA

also the most popular. Named after the three inventors—Ron Rivest, Adi Shamir, and Leonard Adleman—it has withstood years of extensive cryptanalysis. Although the cryptanalysis proved nor disproved RSA's security, it suggests a confidence level in the algorithm.

RSA gets its security from the difficulty of factoring large numbers. The public and private keys are functions of a pair of large [100 to 200 digits or even larger] prime numbers. Recovering the plaintext from the public key and the ciphertext is conjectured to be equivalent to factoring the product of the two primes.

To generate the two keys, choose two random prime numbers, $p$ and $q$ of equal length. Compute the product:

```
$n = pq$
```

Then randomly choose the encryption key, $e$, such that $e$ and $(p-1)(q-1)$ are relatively prime. Finally, using the extended Euclidean algorithm to compute the decryption key, $d$, such that

```
$ed = 1 \pmod{(p-1)(q-1)}$
```

In other words,

```
$d = e^{-1} \pmod{(p-1)(q-1)}$
```

Note that $d$ and $n$ are also relatively prime. The numbers $e$ and $n$ are the public key, the number $d$ is the private key. The two primes, $p$ and $q$, are no longer needed. They should be discarded, but never revealed.

To encrypt a message $m$, divide it into numerical blocks smaller than $n$ (with binary data, choose the largest power of 2 less than $n$). That is, if both $p$ and $q$ are 100-digit primes, then $n$ will have under 200 digits and each message block, $m_i$, should be under 200 digits (If you need to encrypt a fixed number of blocks, you can pad them with zeros on the left to ensure that they will always be less than $n$). The encrypted message, $c$, will be made up of similarly sized blocks, $c_i$, of about the same length. The encryption formula is simply

```
$c_i = m_i^e \pmod{n$
```

To decrypt a message, take each encrypted block $c_i$ and compute

```
$m_i = c_i^d \pmod{n}$
```

Since

```
$c_i^d = [m_i^e]^d = m_i^{ed} = m_i^{kp(p-1)(q-1)+1} = m_i \cdot m_i^{kp(p-1)(q-1)} = m_i \pmod \pmod{n}$
```

the formula is summarized in Table 19.2.

The message could just easily have been encrypted with $d$ and decrypted with $e$; the choice is arbitrary. I will spare you the number that proves why this works; most current texts on cryptography cover it in detail.

A short example will probably go a long way to making this clearer. If $p = 47$ and then