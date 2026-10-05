# 20.1 Digital Signature Algorithm (DSA)

The value $r$ is $a^k mod p$. Call that $e$. Then call

```
DSASign(p,p,1,e,b,0,r,s)
```

The value $s$ is the plaintext message, $m$.
This method will work with all implementations of DSA. Some may fix the values of $p$ and $q$, or the lengths of some of the other parameters. Still, the implementation is general enough. This is a way to encrypt using nothing more than digital signature function.

# RSA Encryption with DSA

RSA encryption is even easier. With a modulus $n$, message $m$, and public key $e$, call

```
DSASign(n,n,m,e,0,r,s)
```

The value of $r$ is returned is the ciphertext.
RSA decryption is the same thing. If $d$ is the private key, then

```
DSASign(n,n,m,d,0,r,s)
```

returns the plaintext as the value of $r$.

# Security of DSA

At 512-bits, DSA wasn't strong enough for long-term security. At 1024 bits, it is. The NSA, in its first interview on the subject, commented to Joe Aberathy of The Houston Chronicle on allegations about a trapdoor in DSA [363]:

Regarding the alleged trapdoor in the DSS. We find the term trapdoor misleading since it implies that the messages sent by the DSS are encrypted and with access a trapdoor one could decrypt [read] the message without the sender's knowledge.

The DSS does not encrypt any data. The real issue is whether the DSS is susceptible to forging a signature and discrediting the entire system. We categorize the chances of anyone—NSA—forging a signature with the DSS when it is properly used and implemented is infinitesimally small.

Furthermore, the alleged trapdoor vulnerability is true for any public key-based authentication system, including RSA. To imply that this only affects DSA [a popular argument in press] is totally misleading. The issue is one of implementation and how one goes about selecting primes. We call your attention to a recent EUROCRYPT which had a panel discussion on the issue of trapdoors in the DSS. Included on the panel was one of the Bellcore researchers who initially raised the trapdoor allegation, and our understanding is that the panel—including the person from Bellcore—concluded that the alleged trapdoor was not an issue for the DSS. Furthermore, the general consensus appeared to be that the trapdoor issue was trivial and had been overthrown in the