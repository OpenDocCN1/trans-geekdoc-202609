there is an identity element, and every element has an inverse with respect to the group operation. An element g in G is called a generator if every element of G can be obtained from the successive application of the group operation on g. In additive groups, a many addition of g is represented as b = ag. Similarly, in multiplicative groups a times multiplication of g is represented as b = g^a.

# Definition 4 (Discrete Logarithm Problem): Let g be a generator of a group G. Given b and g such that b = g^a, finding a is the discrete logarithm problem (DLP).

That the tractability of DLP depends on the group G. If our group consists of elements in Zp = {0, 1, 2, ..., p-1} where p is a prime number and our group operation is multiplication, it is easy to compute g^a(mod p) but it is harder to find a when we know g, a, and p.

This problem becomes even harder if we use the points of an elliptic curve as the elements of a group G. This is ECDLP (Elliptic Curve Discrete Logarithm Problem). The best-known algorithms of ECDLP show that in to have 128-bit security, one needs 256-bit discrete key and 3,072-bit group.

An elliptic curve has many points when it is considered in R or C. For an odd prime p > 3, an elliptic curve over finite fields Fp. Fp is defined by y² = x³ + ax + b and 4a³ + 27b² ≠0 (mod p) where a, b ∈ Fp. The set E(Fp) consists of all points (x, y) where x, y ∈ Fp satisfying the elliptic curve equation and a special point O called the infinity as an identity element. A similar definition is valid for elliptic curves that are defined over finite fields Fq where q is not a prime number but a power of 2, i.e. q = 2^n.

The addition of two points Q and P on the elliptic curve provides the output R where addition is defined by drawing the line that passes through P and Q and taking the negative of the y-coordinate of the third point where this line intersects the elliptic curve.

# Definition 5 (Elliptic Curve Discrete Logarithm Problem): Let E be an elliptic curve over a finite field Fq. Let N be the order of the group E(Fq) and P ∈ E(Fq). Given j = ord(P) and Q ∈ <P>, finding the unique m ∈ {0, 1, 2, ..., j-1} such that Q = mP is the elliptic curve discrete logarithm problem (ECDLP).

Digital signature algorithm (DSA) and its elliptic curve analogue ECDSA (elliptic curve digital signature algorithm) are used mostly for signing transactions.

DSA Parameter Generation:

+   1. Choose a good function H(.) of SHA-2, SHA-3
2. Choose key lengths L and N (e.g. (3072,256))
3. Choose N-bit prime q such that p-1 is a multiple of q
4. Choose g (its multiplicative group order modulo p is q)

DSA User Key Generation:

+   1. Randomly choose x where 0 < x < q
2. Calculate y = g^x mod p

x is the secret and y is the public key.