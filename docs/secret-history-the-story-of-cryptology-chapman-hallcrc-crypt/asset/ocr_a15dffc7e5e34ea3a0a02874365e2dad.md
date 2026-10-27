$$(71 \cdot 101)^2 = (2 \cdot 5 \cdot 9)^2 \pmod{5,141}$$

$$(7,171)^2 = (90)^2 \pmod{5,141}$$

$$(2,030)^2 = (90)^2 \pmod{5,141}$$

$$2,030 - 90 = 1,940$$

$$\gcd(1940, 5141) = 97$$

We may then divide 5,141/97 = 53 to get the complete factorization: 5,141 = (97)(53). If the gcd had been 1, we would have gone on to try the second, and possibly the third solution.

Although the method detailed here is named after Dixon, Dixon himself humbly pointed out that

> > …the method goes back much further than my paper in 1981. References to my paper sometimes do not seem to appreciate this fact. For example, the entry in Wikipedia seems to credit the idea to me. The fact is the idea in one form or another had been around for a much longer time, but no-one had been able to give a rigorous analysis of the time complexity of the versions which were used. What I did in my paper was to show that a randomized version of the method can be analyzed and that (at least qualitatively and asymptotically) it is faster than other known methods (in particular, subexponential in log $N$). As far as I know, except for improved constants, this is still true…

I did not suggest that the randomized version which I described would be competitive in practice with algorithms which were currently in use (but most of which still have no rigorous analysis). I do not think anyone has seriously tried to factor a large number using random squares.

Dixon didn’t know the whole history when he published his 1981 paper, but he did include it in a later paper. In what seems to be a theme with important work in cryptology in recent decades, Dixon’s 1981 paper was rejected by the first journal to which he submitted it.

# ### 15.7.1 The Quadratic Sieve

When using Dixon’s algorithm, much time may be wasted in factoring numbers that end up not being $B$-smooth, and are therefore discarded prior to the matrix step. The quadratic sieve eliminates much of this inefficiency by quickly discarding numbers that aren’t $B$-smooth by using the Sieve of Eratosthenes with a twist. When running through the numbers, instead of crossing them out if they are divisible by a prime, we divide them by the highest power of the particular prime that goes into them. After sieving through in this manner with all of the primes in the factor