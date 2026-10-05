# CHAPTER 23 Special Algorithms for Protocols

Bob has a public key, $e$, a private key, $d$, and a public modulus, $n$. Alice wants Bob to sign message $m$ blindly.

+   (1) Alice chooses a random value, $k$, between 1 and $n$. Then she blinds $m$ by computing
$t = mk^e \pmod n$

+   (2) Bob signs $t$
$t^d = \{mk^e\}^d \pmod n$

+   (3) Alice unblinds $t^d$ by computing
$s = t^d/k \pmod n$

+   (4) And the result is
$s = m^d$ easily
This can be shown
$t^d = \{mk^e\}^d \pmod n$, so $t^d/k = m^d k/k = m^d \pmod n$.

Chaum invented a family of more complicated blind signature algorithms in [320,524], called unicipated signatures. These signatures are more complex in construction, but more flexible.

# 23.13 OBLIVIOUS TRANSFER

In this protocol by Rabin [1286], Alice has a 50 percent chance of sending Bob two primes, $p$, and $q$. Alice will not know whether the transfer is successful. [Section 5.5.] This protocol can be used to send Bob any message with a 50 percent success rate if $p$ and $q$ reveal an RSA private key.

+   (1) Alice sends the product of the two primes: $n = pq$.
(2) Bob chooses a random $x$ less than $n$, such that $x$ is relatively prime to $n$. He sends Alice:
$a = x^2 \pmod n$

+   (3) Alice, knowing $p$ and $q$, computes the four roots of $a$: $x, n-x, y, $ and $n-y$. She chooses one of these roots at random and sends it to Bob.
(4) If Bob receives $y$ or $n-y$, he can compute the greatest common divisor of $x+y$ and $n$, which is either $p$ or $q$. Then, of course, $n/p = q$. If Bob receives $x$ or $n-x$, he can't compute anything.

This protocol may have a weakness: it might be the case that Bob can compute a number $a$ such that given the square root of $a$ he can calculate a factor of $n$ all of the time.