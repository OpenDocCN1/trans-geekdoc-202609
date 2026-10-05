
## CHAPTER 23 Special Algorithms for Protocols

(4) Alice sends Bob $q$, so that Bob can use $m^*$ and reconstruct $s_1$ and $s_2$. If

$s_1 = cg^d \bmod p$
$s_2 = (g^b)^b + az^z \bmod p$

then the signature is valid.

Alice can also disavow a signature, $z$, for a message, $m$. See [329] for details. Additional protocols for undeniable signatures can be found in [584,344]. Lein Harn and Shoubao proposed a group undeniable signature scheme [700].

## Convertible Undeniable Signatures

An algorithm for a convertible undeniable signature, which can be verified, disavowed, and also converted to a conventional digital signature is given in [213]. It's based on the ElGamal digital signature algorithm.

Like ElGamal, first choose primes, $p$ and $q$, such that $q$ divides $p-1$. Now you have create a number, $g$, less than $q$. Choose a random number, $h$, between 2 and $p-1$. Calculate

$g = h^{-1/q} \bmod p$

If $g$ equals 1, choose another random $h$. If it doesn't, stick with the $g$ you have. The private keys are two different numbers, $x$ and $z$, less than $q$. The public keys are $p, q, g, y$, and $u$, where

$y = g' \bmod p$
$u = g' \bmod p$

To compute the undeniable signature of message $m$ (which is actually the hash of a message), first choose a random number, $t$, between 1 and $q-1$. Then compute

$T = g^t \bmod p$

and

$m' = Ttztm \bmod q$.

Now, compute the ElGamal signature on $m'$. Choose a random number, $R$, such that $R$ is less than and relatively prime to $p-1$. Then compute $r = g^R \bmod p$, and use the extended Euclidean algorithm to compute $s$, such that

$m' = tx + Rs \bmod q$

The signature is the ElGamal signature $[t, s]$, and $T$. Here is how Alice verifies her signature to Bob:

- (1) Bob generates two random numbers, $a$ and $b$. He computes $c = T^{ma'} \bmod p$ and sends it to Alice.
- (2) Alice generates a random number, $k$, and computes $h_1 = cg^k \bmod p$, and $h_2 = h_1^{k'} \bmod p$, and sends both of those numbers to Bob.

## 23.5 Designated Confirmer Signatures

(3) Bob sends Alice $a$ and $b$.
(4) Alice verifies that $c = T^{T_{mg}^g} \pmod p$. She sends $k$ to Bob.
(5) Bob verifies that $h_1 = T^{T_{mg}^{g+k}} \pmod p$, and that $h_2 = y^{c^{a}u^b+k} \pmod p$.

Alice can convert any of her undesirable signatures to normal signatures by publishing $z$. Now, anyone can verify her signature without her help.

Undeniable signature schemes can be combined with secret-sharing schemes to create distributed undeniable signatures [1235]. Someone can sign a message, distribute the ability to confirm that the signature is valid. Might, for example, require three out of five people to participate in the protocol in order to convince Bob that the signature is valid. Improvements on this notion deleted the requirement for a trusted dealer [700,1369].

## 23.5 Designated Confirmer Signatures

Here's how Alice can sign a message and Bob can verify it, such that Carol can verify Alice's signature at some later time to Dave (see Section 4.4) [333].

First, a large prime, $p$, and a primitive element, $g$, are made public and used by a group of users. The product of two primes, $n$, is also public. A private key, $z$, and a public key is $h = g^z \pmod p$. Carol has a private key, and a third party.

In this protocol Alice can sign $m$ such that Bob is convinced that the signature is valid, without choosing a third party.

- (1) Alice chooses a random $x$ and computes
$a = g^x \pmod p$
$b = h^x \pmod p$

She computes the hash of $m, H[m]$, and the hash of $a$ and $b$ are concatenated, $H(a,b)$. She then computes
$nj=[H(m) \oplus H(a,b)]^s \pmod n$

- and sends $a, b$, and $j$ to Bob.
- (2) Bob chooses two random numbers, $s$ and $t$, both less than $p$, and sends Alice
- (3) Alice chooses a random $q$ less than $p$, and sends Bob
$d = g^q \pmod p$
$e = (cd)^q \pmod p$

- (4) Bob sends Alice $s$ and $t$.
- (5) Alice confirms that
$g^{ht'} = c \pmod p$

Then she sends Bob $q$.

- (6) Bob confirms
$d = g^a \bmod p$
$e^s = a^b \bmod p$
$H(m) \oplus H(a, b) = j^s \bmod n$

If they all check out, he accepts the signature as genuine.

Bob cannot use transcript of this proof to convince Dave that the signature is genuine, but Dave can conduct protocol with Alice's designated confirmer, Carol.

- (1) Dave chooses a random $u$ and $v$, both less than $p$, and sends Carol
$k = g^a \bmod p$
- (2) Carol chooses a random $w$, less than $p$, and sends Dave
$l = g^w \bmod p$
- (3) Dave sends Carol $u$ and $v$.
- (4) Carol confirms that
$g^a = k \bmod p$
Then she sends Dave $w$.
- (5) Dave confirms that
$g^w = l \bmod p$
$h^w = h^b \bmod p$

If they both check out, he accepts the signature.

In another protocol Carol can convert the designated-confirmer protocol into conventional digital signature. See [333] for details.

## 23.6 COMPUTING WITH ENCRYPTED DATA

### The Discrete Logm Problem

There is a large prime, $p$, and a generator, $g$. Alice has a particular value for $x$, and wants to know $e$, such that

$g^x = x \bmod p$

This is a hard problem, and Alice lacks the computational power to compute the result. Bob has the power to solve the—he represents the large computing, or whatever. Here's how Bob can do it without Alice revealing $x$ [5,4]:

## 23.7 Fair Flips

(1) Alice chooses a random number, $r$, less than $p$.
(2) Alice computes

$x' = x \bmod p$

Similar protocols for quadratic residuity and primitive root problem are in [3,4]. (See Section 4.8.)

## 23.7 FAIR COIN FLIPS

The following protocols allow Alice and Bob to flip a fair coin over data (see Section 4.9) [194]. This is an example of flipping a coin into (see Section 4.10). At first, Bob only knows the result of the toss and tells it to Alice. Later, Alice may check to make sure that Bob told her the correct outcome.

### Coin Flipping Using Square Roots

Coin-flip protocol:

- (1) Alice chooses two large primes, $p$ and $q$, and sends their product, $n$, to Bob.
- (2) Bob chooses a random positive integer, $r$, such that $r$ is less than $n/2$. Bob computes
$z = r^2 \bmod n$
s $z$ to Alice.
- (3) Alice chooses the four square roots of $z [\bmod n]$. She can do this because she knows the factorization of $n$. Let's call $x, -x, y$, and $-y$. Call $x'$ the smaller of these two numbers:
$x \bmod n$
$-x \bmod n$
Similarly, call $y'$ the smaller of these two numbers:
$y \bmod n$
$-y \bmod n$

Note that $r$ is equal to $x'$ or $y'$.
- (4) Alice guesses whether $r = x'$ or $r = y'$, and sends her guess to Bob.
- (5) If Alice's guess is correct, the result of the coin flip is heads. If Alice's guess is incorrect, the result of the coin flip is tails. Bob announces the result of the coin flip.

Verification subprotocol:

- (6) Alice sends $p$ and $q$ to Bob.
- (7) Bob computes $x'$ and $y'$ and sends them to Alice.
- (8) Alice calculates $r$.

Alice has no knowing of $r$, so her guess is real. She only tells Bob one bit of her guess in [4] to prevent Bob from getting both $x'$ and $y'$. If Bob has both of those numbers, he can change $r$ after step [4].

### Coin Flipping Using Exponentiation Modulo p

Exponentiation modulo a prime number, $p$, is used as a one-way function in this protocol [1306]:

Coin-flip subprotocol:

- (1) Alice chooses a prime number, $p$, in such a way that the factorization of $p-1$ is known and contains at least one large prime.
- (2) Bob selects two primitive elements, $h$ and $t$, in $GF(p)$. He sends them to Alice.
- (3) Alice checks that $h$ and $t$ are prime and chooses a random integer $x$, relatively prime to $p-1$. She computes one of the two values:
$y = h^x \bmod p$, or $y = t^x \bmod p$
She sends $y$ to Bob.
- (4) Bob guesses whether Alice calculated $y$ as a function of $h$ or $t$, and sends his guess to Alice.
- (5) If Bob's guess is correct, the result of the coin flip is heads. If Alice's guess is incorrect, Alice announces the result of the coin flip.

Verification subprotocol:

- (6) Alice reveals $x$ to Bob. Bob computes $h^x \bmod p$ and $t^x \bmod p$, to confirm that Alice has played fairly and to verify the result of the toss. He also checks that $x$ and $p-1$ are relatively prime.

For Alice to cheat, she has to know two integers, $x$ and $x'$, such that $h^x = t^{x'} \bmod p$. She would be able to calculate:

```
$log
```

These are hard problems.
