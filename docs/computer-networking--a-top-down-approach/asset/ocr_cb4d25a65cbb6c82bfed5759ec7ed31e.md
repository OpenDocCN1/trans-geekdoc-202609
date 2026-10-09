the session key, K s . Bob now knows the session key that Alice will use for her encrypted data transfer.

# Why Does RSA Work?

RSA encryption/decryption appears rather magical. Why should it be that by applying the encryption algorithm and then the decryption algorithm, one recovers the original message? In order to understand why RSA works, again denote $n=pq$, where $p$ and $q$ are the large prime numbers used in the RSA algorithm.

Recall that, under RSA encryption, a message (uniquely represented by an integer), $m$, is exponentiated to the power $e$ using modulo-$n$ arithmetic, that is,

```
$c=m^{e} \mathrm{~mod} n$

```

Decryption is performed by raising this value to the power $d$, again using modulo-$n$ arithmetic. The result of an encryption step followed by a decryption step is thus $\left(m^{e} \mathrm{~mod} n\right)^{d} \mathrm{~mod} n$. Let’s now see what we can say about this quantity. As mentioned earlier, one important property of modulo arithmetic is $(a \mathrm{~mod} n)^{d} \mathrm{mod} n=a^{d} \mathrm{mod} n$ for any values $a, n$, and $d$. Thus, using $a=m^{e}$ in this property, we have

```
$\left(m^{e} \mathrm{~mod} n\right)^{d} \mathrm{mod} n=m^{e d} \mathrm{mod} n$

```

It therefore remains to show that $m^{e d} \mathrm{mod} n=m$. Although we’re trying to remove some of the magic about why RSA works, to establish this, we’ll need to use a rather magical result from number theory here. Specifically, we’ll need the result that says if $p$ and $q$ are prime, $n=p q$, and $z=(p-1)(q-1)$, then $x^{\mathrm{v}} \mathrm{mod} n$ is the same as $x^{(y \bmod z)} \mathrm{mod} n$ [Kaufman 2002]. Applying this result with $x=m$ and $y=e d$ we have

```
$m^{e d} \mathrm{mod} n=m^{(e d \bmod z)} \mathrm{mod} n$

```

But remember that we have chosen $e$ and $d$ such that $e d \bmod z=1$. This gives us

```
$m^{e d} \mathrm{mod} n=m^{1} \mathrm{mod} n=m$

```

which is exactly the result we are looking for! By first exponentiating to the power of $e$ (that is, encrypting) and then exponentiating to the power of $d$ (that is, decrypting), we obtain the original value, $m$. Even more wonderful is the fact that if we first exponentiate to the power of $d$ and then exponentiate to the power of $e$-that is, we reverse the order of encryption and decryption, performing the decryption operation first and then applying the encryption operation-we also obtain the original value, $m$. This wonderful result follows immediately from the modular arithmetic:

```
$\left(m^{d} \mathrm{~mod} n\right)^{e} \mathrm{mod} n=m^{d e} \mathrm{mod} n=m^{e d} \mathrm{mod} n=\left(m^{e} \mathrm{~mod} n\right)^{d} \mathrm{mod} n$

```