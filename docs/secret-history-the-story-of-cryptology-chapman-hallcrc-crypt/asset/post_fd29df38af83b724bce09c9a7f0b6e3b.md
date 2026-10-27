
Testing values, it appears that $li(n) > π(n)$ for all $n$; however, this is not true. Although it is ridiculously large, there is a point at which $li(n)$ switches from being an overestimate to being an underestimate. Stanley Skewes, a South African mathematician, investigated where this change-over occurs. He could not establish an exact value, but he did find a bound. The switch takes place somewhere before $e^{e^{e^{79}}}$. This bound assumes that the Riemann hypothesis holds.⁵ Without this assumption, Skewes found the larger bound $10^{10^{10^{963}}}$.⁶ It was learned, before Skewes made his calculations, that $li(n)$ eventually switches back to being an underestimate again. In fact, it switches between an overestimate and an underestimate infinitely many times!⁷ For many years, Skewes’s numbers held the record for being the largest numbers that ever served a useful purpose (i.e., used in a proof), but they have since been dwarfed by other values. They’ve also been diminished in another way—much smaller bounds have been found for where $li(n)$ first transitions to an underestimate.

Still the question remains, how can we find or generate large prime numbers? *Primality testing* is concerned with deciding whether or not a given number is prime. For the quickest tests, the revelation that a number is not prime is made without revealing any of the factors. They’re like existence theorems for nontrivial, proper factors.

We first look at some probabilistic tests. These tests can sometimes prove a number is composite, but they can never quite prove primality. The best they can do is suggest primality, with arbitrarily high probabilities.

## 16.2 The Fermat Test

Recall Fermat’s Little Theorem (1640):

$$\text{If } p \text{ is a prime and } a \text{ is not a multiple of } p, \text{ then } a^{p-1} \equiv 1 \pmod{p}.$$

This offers a test that may show a number to be composite, for if $(a,n)=1$ and $a^{n-1} \ne 1 \pmod n$, then $n$ cannot be prime. However, if the result is 1, we can’t conclude that $n$ is prime. Fermat’s Little Theorem is not an “if and only if” theorem.

As usual, a proof was not offered by Fermat. The first to verify this with a proof was Gottfried von Leibniz. The special case for $a=2$ was known to the Chinese as far back as 500 BCE, but they didn’t have the generalization Fermat provided.

To test a number $n$ for primality, we can use values for $a$ from the set $\{2, 3, 4, \ldots, n-1\}$. If one of these yields anything other than 1, we know $n$ is composite. The repeated squaring technique of exponentiation can be used to make these calculations go a bit quicker.

would be named after him in 1910. The first few Carmichael numbers¹⁰ are 561, 1105, 1729, 2465, 2821, 6601, 8911, 10585,…

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_496_0.png)

**Figure 16.1　Robert Carmichael (1879–1967).** (From [https://web.archive.org/web/2012003061628/http://www.maa.org/aboutmaa/carmichael.gif](https://web.archive.org/web/2012003061628/http://www.maa.org/aboutmaa/carmichael.gif)¹¹ Copyright Mathematical Association of America, 2012. All rights reserved.)

There are only 20,138,200 Carmichael numbers less than 10²¹, which is about 0.000000000002% of the total.¹² Thus, the odds that a randomly chosen number will be a Carmichael number are very small. Nevertheless, we’d like to have a primality test that isn’t fooled by these numbers.

## 16.3 The Miller–Rabin Test¹³

This is the most popular scheme for testing the large numbers needed for RSA encryption for primality. To test whether or not *n* is prime, we begin by finding the highest power of 2 that divides *n* − 1. We label this power *t* and then define *d* = (*n* − 1)/(2ᵗ). We have 2ᵗ*d* = *n* − 1. (Note that *d*

¹⁰ “A002997, Carmichael numbers: composite numbers *n* such that a^(*n* − 1) = 1 (mod *n*) for every *a* coprime to *n*.” *The On-Line Encyclopedia of Integer Sequences®*, https://oeis.org/A002997.

¹¹ This website is the result of following a link from https://web.archive.org/web/20120214210612/http://www.maa.org/aboutmaa/maapresidents.html. Other links lead to images of each of the Mathematical Association of America’s presidents from 1916 to 2010. Carmichael was president in 1923.

¹² Pinch, Richard G. E., *The Carmichael Numbers up to 10²¹*, May 15, 2007, available online at http://s369624816.websitehome.co.uk/rgep/p82.pdf.

¹³ Weisstein, Eric W., “Primality Test,” *MathWorld*, a Wolfram Web Resource, https://mathworld.wolfram.com/PrimalityTest.html refers to this as the Rabin–Miller test, as does Bruce Schneier in the second edition of *Applied Cryptography*, p. 259. Richard A. Mollin adds a name to get Miller–Rabin–Selfridge. He explains that John Selfridge deserves this recognition, as he was using the test in 1974, before it was published by Miller. See Mollin, Richard A., *An Introduction to Cryptography*, Chapman & Hall / CRC, Boca Raton, Florida, 2001, p. 191. If you want to avoid names altogether, it is also referred to as the *strong pseudoprimality test*. Whatever you choose to call it, the primary reference is Rabin, Michael O., “Probabilistic Algorithm for Testing Primality,” *Journal of Number Theory*, Vol. 12, No. 1, February 1980, pp. 128–138.

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_498_0.png)

**Figure 16.2** Michael O. Rabin (1931–). Rabin split the $1 million Dan David Prize with two others. (From SEAS, Michael O. Rabin Wins Dan David Prize: Computer Science Pioneer Shares $1 Million Prize for Outstanding Achievements in the Field [press release], Harvard School of Engineering and Applied Science, February 16, 2010.)

![](img/f6c4dca50ef84b4aba9e02fb67e5ce15_498_1.png)

**Figure 16.3** Gary L. Miller. ([http://www.cs.cmu.edu/~glmiller/](http://www.cs.cmu.edu/~glmiller/)).

ScratchPad.<sup>14</sup> Implementations such as this apply the test to a small set of bases. The composite number that squeaked by all of these was 1195068768795265792518361315725116351898245581. However, Arnault noted that after he found this exception ScratchPad was improved, and renamed Axiom, with a new primality test that isn’t just Miller–Rabin, and which recognizes the number above as composite.

<sup>14</sup> Arnault, François, “Rabin-Miller Primality Test: Composite Numbers Which Pass It,” *Mathematics of Computation*, Vol. 64, No. 209, January 1995, pp. 355–361.

It is an intriguing possibility that there may be a hybrid system that catches all composites. In other words, we may have two tests, each of which misses certain numbers, but if there is no overlap between these sets of missed numbers then passing both tests guarantees primality.

### 16.3.1 Generating Primes

The actual generation of large primes for use with RSA is usually done as follows:

- 1. Generate a random string of bits of the desired size. Make sure the first bit is 1 to guarantee the number has a minimum size, and make sure the last bit is 1, so the number isn’t even (and therefore composite).
- 2. Test the number to be sure it isn’t divisible by any small primes (less than a million, for example).
- 3. Apply the Miller–Rabin Test for a sufficient number of rounds to obtain a probability of primality that is comfortably close to 1.

We now take a look at a few tests that are guaranteed to yield a correct answer. These are known as *deterministic tests*. Unlike probabilistic tests, there is no uncertainty. The downside is that they are not as fast as the Miller–Rabin Test.

## 16.4 Deterministic Tests for Primality

An old result that leads to a deterministic test for primality is Wilson’s Theorem:

Let *n* be a positive integer. Then *n* is prime if and only if $(n−1)! \equiv −1 \pmod n$.

This result is named after British mathematician John Wilson (1741–1793), although he was not the first to find it, publish it, or prove it. Those accomplishments go to Leibniz, Waring,¹⁵ and Lagrange,¹⁶ respectively.

Wilson’s theorem is elegant, but it is not a quick way to test for primality! Probabilistic tests, while less satisfying, are more practical, when there is a huge savings in time.

Leonard Adleman, along with Carl Pomerance and Robert S. Rumely, developed a deterministic test for primality in 1983 that was the quickest algorithm of its kind for a while. It was not as fast as Miller–Rabin, but it did offer absolute certainty.¹⁷ Another deterministic test was provided by Adleman and Huang using elliptic curves, but this test also took unacceptably long compared to probabilistic tests.

### 16.4.1 The AKS Primality Test (2002)

Finally in 2002, the first deterministic polynomial time test for primality was found by Professor Manindra Agrawal, and two students, Neeraj Kayal and Nitin Saxena (Figure 16.4), at the Indian
