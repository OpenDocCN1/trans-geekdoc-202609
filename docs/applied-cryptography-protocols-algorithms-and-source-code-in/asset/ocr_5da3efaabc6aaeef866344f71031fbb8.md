# 494 CHAPTER 20 Public-Key Digital Signature Algorithms

... NIST addressed the possible patent infringement claims, and has con-
cluded that there are no valid claims.
The standard is official, lawsuits are threatened, and no one knows what to do.
IST has said it would help defend people used for patent infringement, if they
were using DSA to satisfy a government contract. Everyone else, it seems, on
own. ANSI was a drafting standard that uses DSA [60]. NIST is working
to standardize DSA within the government. Shell Oil has made DSA their interna-
tionional standard. I know of no other proposed DSA standards.

# 20.2 DSA VARIANTS

This variant makes computation easier on the singer by not forcing him to compute
k$^{-1}$ [1135]. All the parameters are as in DSA. To sign a message, $m$, Alice generates
two random numbers, $k$ and $d$, less than $q$. The signature is

```
$t = [g^k \mod p] q
s = [H(m) + xr] \cdot d \mod q
t = kd \mod q$
```

Bob verifies signature by computing

```
$w = t/s \mod q\nu u_1 = [H(m) \cdot w] \mod q\nu u_2 = [rw] \mod q$
```

If $r = [(g^k \cdot y^x \mod p] q$, then the signature is verified.
This variant makes computation easier on the verifier [1040,1629]. All the
parameters are as in DSA. To sign a message, $m$, Alice generates a random number,
k$, less than $q$. The signature is

```
$t = [g^k \mod p] q\ns = k \cdot [H(m) + xr]^{-1} \mod q$
```

Bob verifies signature by computing

```
$u_1 = [H(m) \cdot s] \mod q\nu u_2 = [sr] \mod q$
```

If $r = [(g^k \cdot y^x \mod p] q$, then the signature is verified.
Another DSA variant allows for batch verification, Bob can verify signatures in
[1135]. If they are all valid, he is fine. If one isn't valid, he still has to
find it. Unfortunately, it is not secure; either the signer or the verifier can easily cre-
ate a set of bogus signatures that satisfy the batch criteria [974].
 is also a variant for DSA prime generation, one that embeds $q$ and the
parameters used to generate the primes within $p$. Whether this scheme reduces
t security of DSA is still unknown.