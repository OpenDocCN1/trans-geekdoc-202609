It is an intriguing possibility that there may be a hybrid system that catches all composites. In other words, we may have two tests, each of which misses certain numbers, but if there is no overlap between these sets of missed numbers then passing both tests guarantees primality.

# 16.3.1 Generating Primes

The actual generation of large primes for use with RSA is usually done as follows:

+   1. Generate a random string of bits of the desired size. Make sure the first bit is 1 to guarantee the number has a minimum size, and make sure the last bit is 1, so the number isn’t even (and therefore composite).
+   2. Test the number to be sure it isn’t divisible by any small primes (less than a million, for example).
+   3. Apply the Miller–Rabin Test for a sufficient number of rounds to obtain a probability of primality that is comfortably close to 1.

We now take a look at a few tests that are guaranteed to yield a correct answer. These are known as *deterministic tests*. Unlike probabilistic tests, there is no uncertainty. The downside is that they are not as fast as the Miller–Rabin Test.

# 16.4 Deterministic Tests for Primality

An old result that leads to a deterministic test for primality is Wilson’s Theorem:

Let *n* be a positive integer. Then *n* is prime if and only if $(n−1)! \equiv −1 \pmod n$.

This result is named after British mathematician John Wilson (1741–1793), although he was not the first to find it, publish it, or prove it. Those accomplishments go to Leibniz, Waring,¹⁵ and Lagrange,¹⁶ respectively.

Wilson’s theorem is elegant, but it is not a quick way to test for primality! Probabilistic tests, while less satisfying, are more practical, when there is a huge savings in time.

Leonard Adleman, along with Carl Pomerance and, Robert S. Rumely, developed a deterministic test for primality in 1983 that was the quickest algorithm of its kind for a while. It was not as fast as Miller–Rabin, but it did offer absolute certainty.¹⁷ Another deterministic test was provided by Adleman and Huang using elliptic curves, but this test also took unacceptably long compared to probabilistic tests.

# 16.4.1 The AKS Primality Test (2002)

Finally in 2002, the first deterministic polynomial time test for primality was found by Professor Manindra Agrawal, and two students, Neeraj Kayal and Nitin Saxena (Figure 16.4), at the Indian