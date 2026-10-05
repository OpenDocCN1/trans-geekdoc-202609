376 • NETWORK SECURITY AND CRYPTOGRAPHY

#  8.8 DIGITAL SIGNATURE SCHEMES

+   * RSA Digital Signature Scheme
* ElGamal's Digital Signature Scheme
* Digital Signature Algorithm (DSA)

#  8.8.1 RSA Digital Signature Scheme

The scheme comprises the following components:

+   * Key Generation
* Signature Algorithm
* Signature Verification Algorithm

#  8.8.1.1 Generation of Keys

Each user generates its Public Key and Private Key as follows:

+   * Choose two large prime numbers $p$ and $q$. (The larger the prime numbers, the harder it would be to break the cipher).
* Compute $n = pq$
* Compute $\Phi(n) = (p-1)(q-1)
* Choose an integer $e$ such that $e$ is less than $\Phi(n)$ and relatively prime to $\Phi(n)$, that is, $GCD(e,\Phi(n)) = 1$.
* Compute $d$ as the multiplicative inverse of $e$ modulus $\Phi(n)$; $d \equiv e^{-1} \pmod{\Phi(n)}$ Thus $e$ and $d$ form multiplicative inverses of each other (mod $\Phi(n)$).

The pair $(e,n)$ forms the Public Key and the pair $(d,n)$ forms the Private Key of User "A". The Private Key is kept secret by the owner and the Public Key is made available to all other users in the cryptosystem.

#  8.8.1.2 Signature Algorithm

The sender of a message $M$ signs it as follows:

+   * Generate hash value $H(M)$ of the message using a Hash Function such that
0 < H(M) < n