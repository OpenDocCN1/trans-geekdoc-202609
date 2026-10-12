
$$C\left\lbrack X \right\rbrack = A\left\lbrack X \right\rbrack - B\left\lbrack X \right\rbrack = {\sum\limits_{i = 0}^{m - 1}{c_{i}x^{i}}},\ where~c_{i} = \left( a_{i} - b_{i} \right)mod2$$

(1.15)

For example, `A[X] = x² + x + 1` and `B[X] = x² + 1`. `A[X] + B[X] = (2 mod 2)x² + x + 2 mod 2 = x` and `A[X] − B[X] = x`.

Note that the addition and subtraction in `GF(2^m)` are the same operation.

For the multiplication operation it seems like multiplying two polynomials will return the correct result, i.e. `C'[X] = A[X]B[X] = (x²+x+1)(x²+1) = x⁴ + x³ + x + 1 ∉ GF(2^m)`. However, it is not true; the resulting element does not belong to the field under consideration. Now recall prime fields: `GF(7) = {0,1,…6}`, multiply the following two elements: `3.4 = 12 mod 7 = 5 ∈ GF(7)`. The correct result is obtained by computing the modulo operation. The same is the case with extension fields, we have to divide the multiplication result by a polynomial, i.e. reduce `C'[X]` by a polynomial that behaves like a prime called an irreducible polynomial. Find the irreducible polynomial $P\left\lbrack X \right\rbrack = {\sum_{i = 0}^{m}{p_{i}x^{i}}},\ $ where `p[i] ∈ GF(2)`. For `GF(2³)`: `P[X] = x³ + x + 1`. Therefore, the correct method of multiplication in extensions fields is: `C[X] = A[X]B[X] mod P[X]`. For every field there exists several irreducible polynomials.

For the inversion operation in `GF(2^m)` the extended Euclidean algorithm can be used. For example, to find the multiplication inverse of `(x³+x+1) modulo (x⁵+x³+1)`, use the extended Euclidean algorithm as follows:

*   `x⁵ + x³ + 1 = x²(x³+x+1) + (x²+1)`
*   `x³ + x + 1 = x(x²+1) + 1`
*   `x³ + x + 1 − x(x²+1) = 1`
*   `(x³+1)(x³+x+1) + x(x⁵+x³+1) = 1`
*   `(x³+x+1)^(-1) = (x³+1)`

#### 1.2.5.4 Characteristic of a field

The characteristic of a field is a number (non-negative integer) associated with every field. It is denoted as `Ch(F)`; it is the smallest number of times the multiplicative identity (1) is added to itself to get back 0 (additive identity). For example: `F[2] = {0,1}` with the following composition table is `Ch(F) = 2` (1+1=0).

*   + 0 1 * 0 1
*   0 0 1 0 0 0
*   1 1 0 1 0 1

**Theorem**: Characteristic of a field is either 0 or a prime number.

**Proof**: The proof is by contradiction. Let `Ch(F) = n`, where `n` is not a prime. Therefore, `n = ab` such that neither of `a` or `b` is `1` and `1 < a, b < n`. By definition of characteristic of a field, `n ⋅ 1 = 0`, which implies `(ab) ⋅ 1 = 0`. By expanding the dot representation, `(a⋅1) * (b⋅1) = 0`. In fields there is no zero divisor, so either of `(a⋅1)` or `(b⋅1)` is 0. Let us say, `(a⋅1) = 0`. This contradicts the assumption that `n` is the smallest positive integer. Hence, `Ch(F) = 0 or p`.

## 1.3 APPLICATION TO CRYPTOGRAPHY

These number theory and abstract algebraic concepts have direct application in modern cryptography. The cryptosystems are designed in a way that involves one-way processes which are easy to compute but hard to reverse. These one-way processes are developed using the concepts in number theory. Consider the example of factoring, a very basic concept in number theory, which is a very famous example of such a one-way process in the sense that it is quite easy to multiply any two large prime, but extremely difficult to recover these prime factors given the number. This factoring problem linked with Euler's theorem forms the foundation of the most popular RSA cryptosystems. Another example of such a one-way process is the discrete logarithm problem which states that given two co-prime integers `a` and `n` and another integer `k` it is easy to find `a^k mod n`, but extremely difficult to find `k`, given `a^k mod n`. Discrete logarithm problems form the foundation of many cryptosystems and the Diffie–Hellman key exchange algorithm is the first successful example of this problem. More recently, these ideas have been extended and enriched by replacing modular arithmetic by the more exotic operations on points on elliptic curves.

## 1.4 CHAPTER SUMMARY

In this chapter we have discussed the fundamentals of number theory and abstract algebra which play an important role in understanding and the development of cryptosystems. Modern cryptography is totally based on the abstract algebra and number theory. Therefore, we have tried to briefly cover every aspect of these two prerequisites with respect to their application in cryptography. Further, keeping in mind the page limit as well as the clarity of concepts, we have selectively chosen topics and elaborated only those whose application can be directly seen in the cryptographic world.

# REFERENCES

1. V. Shoup, A Computational Introduction to Number Theory and Algebra. Cambridge University Press, 2009.
2. J. J. Tattersall, Elementary Number Theory in Nine Chapters. Cambridge University Press, 2005.
3. A. Weil, Basic Number Theory, vol. 144. Springer Science & Business Media, 2013.
4. B. Gupta, D. P. Agrawal, and S. Yamaguchi, eds. Handbook of Research on Modern Cryptographic Solutions for Computer and Cyber Security. IGI Global, 2016.
5. P. Premkamal, S. Kumar, P. J. A. Kumar Pasupuleti, and Alphonse, “Efficient escrow-free CP-ABE with constant size ciphertext and secret key for big data storage in cloud.”, International Journal of Cloud Applications and Computing (IJCAC), vol. 10, no. 1, pp. 28–45, 2020.
6. C. C. Sims, “Abstract algebra: a computational approach,” No. 512.02 S5. J. Wiley, 1984.
7. D. S. Dummit, and R. M. Foote, Abstract Algebra, vol. 3. Wiley Hoboken, 2004.

# Chapter 2

# Introduction to cryptography

CRYPTOGRAPHY is not just an area of study but is a mandatory requirement in today's digital world. It is an essential tool for keeping digital information safe both in the system and during its transmission. If we look carefully, cryptography can be seen everywhere, from secure communication over the Internet to user authentication and to encrypting files on our disks. Cryptography resides at the heart of every system or network that needs security and privacy. Cryptography existed for thousands of years and will continue to be the basis for developing security mechanisms. This chapter covers the basic concepts related to cryptography. It briefly discusses both traditional and modern cryptography as well as the journey from conventional to modern cryptography. It describes cryptographic principles and key terms in detail to build a strong foundation.

## 2.1 INTRODUCTION TO CRYPTOGRAPHY
