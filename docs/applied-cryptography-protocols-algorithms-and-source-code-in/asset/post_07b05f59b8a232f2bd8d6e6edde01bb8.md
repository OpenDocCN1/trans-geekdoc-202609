
(2) Alice creates a {k+j+1, 2k+j+1} threshold scheme, with:
- K as the secret.
- The secret keys of the intended recipients as shadows.
- The secret keys of nonrecipients not as shadows.
- j randomly chosen shadows, not the same as any of the secret keys.

(3) Alice broadcasts k+j randomly chosen shadows, none of which is any of t shadows listed in step (2).

(4) All listeners who receive the broadcast add their shadow to the k+j shadows they received. If adding their shadow allows them to calculate the secret, then if it does not, then they have recovered the key.

Another approach can be found in [885,886,1194]. For yet another approach, see [1000].

## Conference Key Distribution

This protocol allows a group of n users to agree on a secret key using only insecure channels. The group shares two large primes, p and q, and a generator g of the same size as q.

(1) User i, where i goes from 1 to n, chooses a random r, less than q, and broadcasts:
$z_i = g^i \pmod p$

(2) Every user verifies $z_i^q = 1 \pmod p$, for all i from 1 to n.

(3) User i broadcasts:
$x_i = [z_{i+1}/z_{i-1}]^i \pmod p$

(4) User computes:
$K = [z_{i-1}]^i \cdot x_{i+1}^{n-2} \cdot \dots \cdot x_{i-2} \pmod p$

All index computations in the protocol i-1, i-2, and i—should be computed mod n. At the end of the protocol, all honest users have the same K. No else gets anything. However, this protocol fails to a man-in-the-middle attack. Another protocol, not quite as prime, is in [757].

## Tatebayashi-Matsumoto-Newman

This key distribution protocol is suitable for networks [1521]. Alice wants to generate a session key with Bob using Trent, the KDC. All parties know Trent's public key, n. Trent knows the two large primes that n factors to, and hence can easily cube roots modulo $n$. A lot of the details are left out of the following protocol, and you get the idea.

- (1) Alice chooses a random number, $r_A$, and sends Trent $r_A^8 \pmod n$
- (2) Trent tells Bob that someone wants to exchange a key with him.
- (3) Bob chooses a random number, $r_B$, and sends Trent $r_B^8 \pmod n$
- (4) Trent uses his private key to recover $r_A$ and $r_B$. He sends Alice $r_A \oplus r_B$
- (5) Alice calculates $[r_A \oplus r_B] \oplus r_A = r_B$

She uses $r_B$ to communicate securely with Bob.

This protocol looks good, but it has a horrible flaw. Carol can listen on step [3] and use that information, with the help of an unsuspecting Trent and another malicious user [Dave], to recover $r_B$ [1472].

- (1) Carol chooses a random number, $r_C$, and sends Trent $r_B \oplus r_C^3 \pmod n$
- (2) Trent tells Dave that someone wants to exchange a key with him.
- (3) Dave chooses a random number, $r_D$, and sends Trent $r_D^3 \pmod n$
- (4) Trent uses his private key to recover $r_C$ and $r_D$. He sends Carol $[r_B \oplus r_C] \pmod n \oplus r_D$
- (5) Dave sends $r_D$ to Carol.
- (6) Carol uses $r_C$ and $r_D$ to recover $r_B$. She uses $r_B$ to eavesdrop on Alice and Bob.

This is not good.

## CHAPTER 23
## Special Algorithms for Protocols

### 23.1 MULTIPLE-KEY PUBLIC-KEY CRYPTOGRAPHY

This is a generalization of RSA (see Section 19.3) [217,212]. The modulus, $n$, is the product of two primes, $p$ and $q$. However, instead of choosing $e$ and $d$ such that $ed = 1 \pmod{|p-1||q-1|}$, choose $t$ keys, $K_i$, such that
$K_1 \cdot K_2 \cdot \dots \cdot K_t = 1 \pmod{|p-1||q-1|}$

Since

$M^{K_1 \cdot K_2 \cdot \dots \cdot K_t} = M$

this is a multiple-key scheme as described in Section 3.5.
If, for example, there are five keys, a message encrypted with $K_3$ and $K_5$ can be decrypted with $K_1, K_2$, and $K_4$.

$C = M^{K_3 \cdot K_5} \pmod n$
$M = C^{K_1 \cdot K_2 \cdot K_4} \pmod n$

Use one for multisignatures. Imagine a situation where both Alice and Bob have to sign a document for it to be valid. Use three keys: $K_1, K_2$, and $K_3$. The first two are issued to Alice and Bob, and the third is made public.

- (1) First Alice signs $M$ and sends it to Bob.
$M = M^{K_1} \pmod n$
- (2) Bob can recover $M$ from $M'$.
$M = M'^{K_2 \cdot K_3} \pmod n$
- (3) He can also add his signature.
$M'' = M'^{K_2} \pmod n$
- (4) Anyone can verify the signature with $K_b$, the public key.
$M = M^{*s} \pmod n$

Note that $K_b$ is the public key. This scheme is used for multisignatures. The complexity of generating a multi-party signature is proportional to the number of signers.

### 23.2 SECRET-SHARING ALGORITHMS

Back in Section 3.7 discussed the idea of secret-sharing. The four algorithms follow:

## Interpolating Polynomial

Shamir's secret-sharing scheme uses the property that a polynomial of degree $k$ is uniquely determined by $k+1$ points. To share a secret $S$, one chooses a random polynomial $f(x)$ of degree $k$ with $f(0) = S$. The shares are the points $(x_i, f(x_i))$ for $i=1, \dots, n$. Any $k+1$ shares can reconstruct the polynomial and the secret using Lagrange interpolation.

$f(x) = \sum_{i=1}^{k+1} y_i L_i(x)$
where $L_i(x) = \prod_{j=1, j \neq i}^{k+1} \frac{x-x_j}{x_i-x_j}$

The secret is $S = f(0) = \sum_{i=1}^{k+1} y_i \prod_{j=1, j \neq i}^{k+1} \frac{-x_j}{x_i-x_j}$.

## Vector Scheme

This secret-sharing scheme uses vectors instead of single numbers. The secret is a vector $S = (s_1, s_2, \dots, s_m)$. Each share is a vector $V_i = (v_{i,1}, v_{i,2}, \dots, v_{i,m})$. Any $k+1$ shares can recover the secret by interpolating each component separately.

## Vector Scheme

George Blake invented a scheme using points in space [182]. The message is defined as a point in $m$-dimensional space. Each shadow is the equation of an $[m-1]$-dimensional hyperplane that includes the point. The intersection of any $m$ of the hyperplanes exactly determines the point.

## Asm-Bloom

This scheme uses prime numbers [65]. For an $(m, n)$-threshold scheme, choose a large $p$, greater than $m$. Then choose $n$ numbers less than $p$, $d_1, d_2, \dots, 	ilde{d}_n$ such that:

- The $d$ values are in increasing order; $d_i < d_{i+1}$
- Each $d_i$ is relatively prime to every other $d_j$
- $d_1 \cdot d_2 \cdot \dots \cdot ildeilde{d}_m > p \cdot d_{n-m+2} \cdot d_{n-m+3} \cdot \dots \cdot 	ilde{d}_n$
