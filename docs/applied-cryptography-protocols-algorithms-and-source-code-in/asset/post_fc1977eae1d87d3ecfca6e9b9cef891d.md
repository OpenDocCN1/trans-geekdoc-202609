
## 20.6 ESIGN

The pair, $S_1$ and $S_2$, is the signature. To verify a signature, confirm that

```
$S_1^2 + h \cdot S_2^2 = M \pmod n$
```

The version of the scheme described here is based on quadratic polynomials. When it was first proposed in [1217], a $100 reward was offered for successful crypt-analysis. It was proved insecure [1255,18], but its authors were not deterred. They proposed a modification of the algorithm based on cubic polynomials, which is also insecure [1255]. The authors then proposed a quartic version, which was also broken [524,125]. A variant which fixes these problems is in [1134].

## 20.6 ESIGN

ESIGN is a digital signature scheme from NTT Japan [1205,583]. It is touted as being at least secure and considerably faster than either RSA or DSA, with similar key and signature lengths.

The private key is a pair of prime numbers, $p$ and $q$. The public key is $n$, which is

```
$n = p \cdot q$
```

$H$ is a hash function that operates on a message, $m$, such that $H(m)$ is between 0 and $n-1$. There is also a security parameter, $k$, which will be discussed shortly.

- (1) Alice picks a random number $x$, where $x$ is less than $pq$.
- (2) Alice computes:
```
w, the least integer that is larger or equal to H(m) - x^k \pmod{pq}
s = x + \lfloor w/x^k - 1 \rfloor s \pmod p
```
- (3) Alice sends to Bob.
- (4) To verify the signature, Bob computes $s^k \pmod n$. He also computes $a$, which is the least integer larger or equal to twice the number of bits of $n$ divided by 3. If $H(m)$ is less or equal to $s^k \pmod n$, and if $s^k \pmod n$ is less than $H(m)+2$, then the signature is valid.

This algorithm works faster with precomputation. This precomputation can be done at any time and has nothing to do with the message being signed. After picking $x$, Alice breaks into two partial steps. The first can be precomputed:

- (2a) Alice computes:
```
u = x^k \pmod n
v = 1/x^k - 1 \pmod p
```
- (2b) Alice computes:
```
w = the least integer that is larger or equal to |H(m) - u|/pq
s = x + w pq
```

For the size of numbers generally used, this precomputation speeds the signature process by a factor of 10. Almost all the hard work is done in precomputation. A discussion of modular arithmetic operations to speed ESIGN can be found in [1625,1624]. This algorithm can also be extended to elliptic curves in [1206].

## Security of ESIGN

When this algorithm was originally proposed, $k$ was set to 2 [1215]. This was quickly broken by Ernie Brickell and John Laurent [261], who extended their attack to $k = 3$. A modified version of this algorithm [1203] was broken by Shamir [1204]. The variant ESIGN is the current incarnation of this family of algorithms. Another new attack [963] does not work against ESIGN. The authors currently recommend these values for $k$: 8, 16, 32, 64, 128, 256, 512, and 1024. They also recommend that $p$ and $q$ be each of at least 192 bits, making $n$ at least 576 bits long. With these parameters, the authors conjecture that ESIGN is secure as RSA or Rabin. Their analysis shows favorable speed comparison to RSA, ElGamal, and DSA [582].

## Patents

ESIGN is patented in the United States [1208], Canada, England, Germany, and Italy. Anyone who wishes to license the algorithm should contact Intellectual Property Department, NTT, 1-6 Uchisai-cho, 1-chome, Chiyada-ku, Tokyo, Japan.

## 20.7 CELLULAR AUTOMATA

A new and old idea, suggested by Papua Guam [665], is the use of cellular automata in public-key cryptystems. This system is far too new to have been extensively examined, but a preliminary examination suggests that it may have a cryptographic weakness similar to one seen in other cases [562]. This is a promising area of research. Cellular automata have the property that, even if they are invertible, it is impossible to calculate the predecessor of an arbitrary state by reversing the rule for finding the successor. This sounds a whole lot like a trapdoor one-way function.

## 20.8 OTHER PUBLIC-KEY ALGORITHMS

Many other public-key algorithms have been proposed and broken over the years. The Matsumoto-Imai algorithm [1021] was broken in [450]. The Cade algorithm was first proposed in 1985, broken in 1986 [774], and then strengthened in the same year [286]. In addition to these attacks, there are general attacks for decomposing polynomials over finite fields [605]. Any algorithm that gets its security from the composition of polynomials over a finite field should be looked upon with skepticism, if not outright suspicion.

The Yagisawa algorithm combines exponentiation mod $p$ with arithmetic mod $q = 1 [263]; it was broken in [256]. Another public-key algorithm, Tsujii-Kurosawa-Itoh-Fujimoto-Matsumoto [1548] is secure [948]. A third system, Luccio-Mazzone [993], is insecure [717]. A signature scheme based on birational permutations [1425] was broken the day after it was presented [381]. Tatsuti Okamoto has several schemes: one is as secure as the Discrete Logarithm Problem, and another is as secure as the Discrete Logarithm Problem and the Factoring Problem [1206]. Similar schemes are in [709].

Gustav Simmons introduced J-algebras as a basis for public-key algorithms [145,145]. After this was abandoned, efficient methods for factoring polynomials were invented [1951]. Special polynomial semigroups have also been studied in [1619,992], but so far nothing has come of it. Harald Niederreiter proposed a public-key algorithm based on shift-register sequences [1166]. Another is based on Lyndon words [146] and on propositional calculus [817]. And a recent public-key algorithm gets its security from the matrix cover problem [82]. Tatsuti Okamoto and Keizo Ohara compare a number of digital signature schemes in [1212].

Prospects for creating new and different public-key cryptography algorithms seem dim. In 1988, Whitfield Diffie noted that most public-key algorithms are based on three hard problems [492,494]:

- 1. Knapsack: Given a set of unique numbers according to [492,494], the Discrete Logarithm Problem was suggested by J. Gill, the Factoring Problem by Knuth, and the knapsack problem by Diffie. This narrowness in the mathematical foundations of public-key cryptography is worrisome. A breakthrough in either the problem of factoring or calculating discrete logarithms could render whole classes of public-key algorithms insecure. Diffie points out [492,494] that this risk is mitigated by two factors:
- The operations on exponentiation, and on factoring—are all fundamental arithmetic phenomena. They have been the subject of intense mathematical scrutiny for centuries and the increased attention that has resulted from their use in public key systems has on balance enhanced rather than diminished our confidence.
- 2. Our ability to carry out large arithmetic computations has grown steadily and now permits us to implement our systems with numbers sufficient in size to be vulnerable only to a breakthrough in factoring, logarithms, or root extraction.
