
choose another base $a$ and try again. Once $n$ is factored, Mallet can easily generate all of the private keys.

Like the Miller–Rabin primality test, this is a probabilistic attack, but DeLaurentis went on to show that assuming the Riemann hypothesis makes his attack deterministic. He also presented a second attack that allows Mallet to read and sign messages without factoring $n$.

## 17.2.3 Attack 15. Insider's Nonfactoring Attack

Mallet knows that his public key $e_M$ must be relatively prime to $\varphi(n)$, so that a private key may be found that satisfies $e_M d_M = 1 \pmod{\varphi(n)}$. This latter equation is equivalent to

$e_M d_M - 1 = k\varphi(n)$ for some positive integer $k$

Now $e_M d_M - 1$ needn't be relatively prime to Alice's public key $e_A$.

Let $f$ be the greatest common divisor of $e_M d_M - 1$ and $e_A$. The value of $f$ may be found rapidly using the Euclidean algorithm. We define $r = (e_M d_M - 1)/f = (k\varphi(n))/f$ and note that $r$ is relatively prime to $e_A$. Because $f$ is a divisor of $e_A$ and $e_A$ is relatively prime to $\varphi(n)$, $f$ must also be relatively prime to $\varphi(n)$. We now have two very useful facts:

- 1. $f$ is a factor of $k\varphi(n)$.
- 2. $f$ is relatively prime to $\varphi(n)$.

From this we may conclude that $f$ is a factor of $k$. In other words, $r$ is a multiple of $\varphi(n)$. That is, $r = (k/f)(\varphi(n))$.

Because $r$ is relatively prime to $\varphi(n)$, we may use the extended Euclidean algorithm to find integers $x$ and $y$ such that $xr + ye_A = 1$. In particular, we can find a pair $x$ and $y$ such that $y$ is positive. Because $r$ is a multiple of $\varphi(n)$, when we reduce this last equality modulo $\varphi(n)$, the $xr$ term drops out to leave $ye_A = 1 \pmod{\varphi(n)}$.

Thus, $y$ fits the definition of a multiplicative inverse of $e_A \pmod{\varphi(n)}$. It might not be the inverse that Alice actually uses, but it will work just as well. Mallet's use of this value will result in encipherments and signatures that are identical to those produced by Alice.

## 17.2.4 Elgamal Signatures

Like RSA, Elgamal can also be used to sign messages. Unlike RSA, the user needs an extra key component to do so. Recall that for regular Elgamal encryption, Alice only needs a large prime $p$, an element $g$ of maximal order in the multiplicative group of integers modulo $p$, and a private key $a$. She computes $A = g^a \pmod p$ and then publishes $g$, $p$, and $A$. Only $a$ is kept secret.

Let $s$ denote Alice's second secret key. She must compute $v = g^s \pmod p$. Then to sign a message $M$, she selects a random enciphering key $e$ and computes

$S_1 = g^e \pmod p$ and $S_2 = (M - s S_1) e^{-1} \pmod {p - 1}$.

Thus, like Bob's Elgamal-enciphered message to Alice (Section 16.8), Alice's signed message consists of two values, $S_1$ and $S_2$. These would be sent along with the message.

Alice makes v, g, and p public. From these, her signature may be verified by computing v^{S1} S1^{S2} (mod p) and g^{M} (mod p). If the signature is valid, both values will be the same. A few simple steps show why these two values must match:

v^{S1} S1^{S2} = g^{S1} g^{e S2} = g^{S1 + e S2} = g^{S1 + e(M - S1) e^{-1}} = g^{S1 + (M - S1)} = g^{M}

## 17.3 Hash Functions: Speeding Things Up

Just as RSA is slow for enciphering an entire message, and is therefore typically used only to encipher keys, we also don’t want to have to apply RSA to an entire message, in order to sign it. One way of approaching this problem is to somehow condense the message to something much smaller and then sign this representation of the original. The compressed message, or *message digest*, is often referred to as the *hash* of the message. The process of generating this, called *hashing*, should have certain characteristics:

- 1. The same message must always yield the same hash. That is, we have a hash *function*. This will be important when it comes to verifying signatures based on the hash. We denote the hash function by h(x).
- 2. Hashing should be fast. After all, speed is the drawback of using the methods previously described.
- 3. It should be difficult (computationally infeasible) to find two messages that hash to the same value. That is, we should not be able to find distinct x and x′ such that h(x) = h(x′). If this happens, we say that a *collision* has been found. It would be very bad if a legitimately signed document could have a portion replaced (with the new text having some other meaning) and hash to the same value as the original. This would make the altered document appear to be signed as well. However, any collision is seen as a serious threat, even if it is found using two messages that look more like random text than meaningful messages. This is a very interesting condition, as no hash function can be one to one—the whole idea is to create a shorter message! Thus, collisions must exist, even for the best hash functions. Yet finding them should be very difficult!
- 4. Computing any preimage should be difficult. That is, given the hash of a message, h(x), we should not be able to recover the message or any other text y such that h(y) = h(x).

Hash functions came about in the 1950s, but they were not then intended to serve cryptographic purposes.⁴ The idea of these functions was simply to map values in a dataset to smaller values. In this manner, comparisons could be made more easily and searches could be accelerated. In 1974, researchers who may not have been aware of hash functions, recognized that “hard-to-invert” functions offered a way to check if a message had been changed.⁵ They credited the idea to Gus Simmons, who had presented the idea to them “in connection with monitoring the production of certain materials in the interest of arms limitation.⁶ The cryptographic connection was described formally in 1981 by Mark N. Wegman and Larry Carter, a pair of researchers who did non-cryptographic work with hash functions in the late 1970s.⁷

⁴ Knuth, Donald, *The Art of Computer Programming – Sorting and Searching*, Vol. 3, Addison-Wesley, Reading, Massachusetts, 1973. See pp. 506–549.

⁵ Gilbert, Edgar N., Florence J. MacWilliams and Neil J. A. Sloane, “Codes Which Detect Deception,” *The Bell System Technical Journal*, Vol. 53, No. 3, March 1974, pp. 405–424.

### 17.3.1 Rivest’s MD5 and NIST’s SHA-1, SHA-2, and SHA-3

Message-Digest algorithm 5 (MD5) condenses messages of arbitrary length down to 128 bits.⁸ It’s not especially encouraging that we’re on 5 already.⁹ Cipher systems that went through many insecure versions, such as matrix encryption and knapsack encryption, are not viewed with much enthusiasm, when new versions appear, yet MD5 is popular. All of the MD hash functions were designed by Ron Rivest (the R in RSA). Version 5 came out in 1991. Since then, researchers have found quicker and quicker methods of finding collisions. In 2009, Tao Xie and Dengguo Feng reduced the time required to mere seconds, so there’s not much point to further reductions.¹⁰ We now look at an alternative.

> MD5 was obviously used as the model for SHA-1, since they share many common features.
> 
> —Mark Stamp and Richard M. Low¹¹

The Secure Hash Algorithm (SHA) offers another series of hash functions. The first, now called SHA-0, was designed by the National Security Agency (NSA) in 1993. It was followed by NSA’s SHA-1 in 1995. Both produced a 160-bit hash. In fact, there is only a very small difference between the two and NSA claimed the modification improved security, but they didn’t provide an explanation as to how.

Although much cryptanalysis went before, it wasn’t until 2004 that a collision was actually found for SHA-0. It took the equivalent of 13 days’ work on a supercomputer.¹² The following year, a flaw was found in SHA-1. When the National Security Agency announced their “NSA Suite B Cryptography” in 2005, the recommendations for hashing were SHA-256 and SHA-384, which are two algorithms taken from a set of six that are collectively called SHA-2.¹³ Like its predecessors, the SHA-2 algorithms were designed by NSA. Despite the weaknesses of SHA-1 and NSA’s recommendation, the first edition of this book, published in 2013, included the following:

> SHA-1 forms part of several widely used security applications and protocols, including TLS and SSL, PGP, SSH, S/MIME, and IPsec. Those applications can also use

⁶ Gilbert, Edgar N., Florence J. MacWilliams, and Neil J. A. Sloane, “Codes Which Detect Deception,” The Bell System Technical Journal, Vol. 53, No. 3, March 1974, pp. 405–424, p. 406 quoted from here.
⁷ Wegman, Mark N., and J. Lawrence Carter, “New Hash Functions and Their Use in Authentication and Set Equality,” Journal of Computer and System Sciences, Vol. 22, No. 3, June 1981, pp. 265–279.
⁸ http://en.wikipedia.org/wiki/MD5 has a clear (but brief) explanation of the algorithm. A more detailed explanation can be found at http://www.freesoft.org/CIE/RFC/1321/3.htm.
⁹ A meaningful collision for MD4 was presented in Dobbertin, Hans, “Cryptanalysis of MD4,” Journal of Cryptology, Vol. 11, No. 4, Fall 1998, pp. 253–271.
¹⁰ Xie, Tao and Dengguo Feng, How To Find Weak Input Differences For MD5 Collision Attacks, May 30, 2009. http://eprint.iacr.org/2009/223.pdf.
¹¹ Stamp, Mark and Richard M. Low, Applied Cryptanalysis: Breaking Ciphers in the Real World, Wiley-Interscience, Hoboken, New Jersey, 2007, p. 225.
¹² Biham, Eli, Rafi Chen, Antoine Joux, Patrick Carribault, William Jalby, and Christophe Lemuet, “Collisions of SHA-0 and Reduced SHA-1,” in Cramer, Ronald, editor, Advances in Cryptology – EUROCRYPT 2005 Proceedings, Lecture Notes in Computer Science, Vol. 3494, Springer, Berlin, Germany, 2005, pp. 36–57.
¹³ https://web.archive.org/web/20090117004931/http://www.nsa.gov/ia/programs/suiteb_cryptography/index.shtml.
