
## 7.4.2 STRENGTH OF RSA

Knowing public key $(e, n)$ and plaintext $M$, it is easy to compute Cipher-text $C = M \pmod n$ but knowing $C$ and public key $(e, n)$, it is computationally difficult to determine $M = \log_C (\pmod n)$. Thus, even if an adversary intercepts a cipher-text, it would be computationally infeasible to extract $M$ without knowledge of the related public key $(d, n)$.

To determine the private key $(d, n)$ from the knowledge of public key $(e, n)$, the adversary has to follow the following approach.

- Factorize $n$ into its prime factors $p$ and $q$
- Determine $\Phi(n) = (p - 1)(q - 1)$
- Determine $d \equiv e^{-1} \pmod{\Phi(n)}$

Since the prime factors of modulus $n$ are chosen to be very high, factorizing $n$ is considered to be computationally infeasible. For $n$ having 1024 bits (or 309 digits) it is considered computationally infeasible to factor it into primes $p$ and $q$. To make it more robust, the steps are recommended:

- 1. The primes $p$ and $q$ should differ in length only by a few digits. Thus, for a 1024-bit (309 digits) key, both $p$ and $q$ should be of the order of $10^{75}$ to $10^{100}$.
- 2. $(p - 1)$ and $(q - 1)$ should contain a large prime factor.
- 3. GCD $(p - 1, q - 1)$ should be small.

### 7.4.2.1 Different Types of Attacks on RSA

RSA is prone to the following types of attacks:

- 1. Attempt to Determine Private Key without Knowledge of Prime Factors $p$ and $q$ of Modulus $n$.

To determine the private key of a third party, an adversary may follow any of the following approaches:

- (a) – Factoring $n$ into primes $p$ and $q$
- Determining $\Phi(n) = (p - 1)(q - 1)$
- Computing $d \equiv (e - 1) \pmod{\Phi(n)}$

For a large $n$ (typical size of $n$ is 1024 bits or 309 decimal digits), factoring it $p$ and $q$ is highly time-consuming. For 155 decimal digits, the factoring effort is estimated to be 8000 MIPS-Years.

- (b) Determining $\Phi(n)$ directly, without determining $p$ and $q$, and then determining $d = e^{-1} (\text{mod } \Phi(n))$

- (c) Attempt to determine directly, without determining $\Phi(n)$.

## 2. Common Modulus Attack on RSA.

A plaintext $M$ is encrypted using RSA and two public keys $(n, e)$ and $(n, f)$ such that $GCD(E, f) = 1$. It produces cipher-texts $C_e$ and $C_f$.

```
$C_e = M^e \pmod n$
$C_f = M^f \pmod n$
```

The attacker can determine the plaintext without determining $\Phi(n)$.

**Solution:** This attack is known as a "Common Modulus Attack." Basically, it is a "Cipher-Text-Only" Attack, used to determine the Plaintext without determining $\Phi(n)$, as follows

```
Let $r + sf = 1 \quad$ (for some integers $r$ and $s$) $\quad$ (7.1)
$re = 1 - sf$
$1 = 1 + (-s)f$
$: $re = 1 (\text{mod } f)$
```

Since $GCD(e, f)$ is the multiplicative inverse of $e (\text{mod } f)$. Determine $r$ using the Extended Euclidean Algorithm. It is determined by substituting the value of $r$ in (7.1).

```
Then, determine plaintext $M = ((C_e)^r (C_f)^s) \pmod n$
Since $((C_e)^r (C_f)^s) \pmod n = (M^{er} \times M^{fs}) \pmod n$
$= M^{er+fs} \pmod n$
$= M \pmod n = M$
```

## Example 7.2 (Common Modulus Attack on RSA)

Let $p = 7$ and $q = 11$

RSA modulus $n = p \times q = 77$

The two RSA exponents be $e = 13$ and $f = 17$

$GCD(13, 17) = 1$

Let message $M = 2$

$C_e = M^e \equiv (2)^{13} \mod {77} = ((2)^{10} \times 8) \mod {77} = (23 \times 8) \mod {77} = 30$

$C_f = M^f \equiv (2)^{17} \mod {77} = ((2)^{10} \times 128) \mod {77} = (23 \times 128) \mod {77} = 18$

$r \times e + s \times f = 1$

For some integers $r$ and $s$

$r \times e = 1 (\mod {f})$

$r \times 13 = 1 (\mod {17})$

Determine “$r$", that is, the multiplicative inverse of $13$ (mod 17) using the Extended Euclidean Algorithm.

| (0, 17) | (0, 13) | (1, -1, 4) | 4 |
|---|---|---|---|
| (0, 13) | (1, -1, 4) | (-3, 4, 1) | 3 |

$.: r = 4$

Substituting the value of “$r$” in (7.1)

$4 \times 13 + s \times 17 = 1$

$.: s = (-51)/17 = -3$

Now computing $M = ((C_e)^r (C_f)^s) \mod n$

$= ((30)^4 (18)^{-3}) \mod {77}$

$= ((30)^4 ((18)^{-1})^3) \mod {77}$

Determine $(18)^{-1} \mod {77}$ using the "Extended Euclidean Algorithm."

| (0, 77) | (0, 18) | (1, -4, 5) | 4 |
|---|---|---|---|
| (0, 18) | (1, -4, 5) | (-3, 13, 1) | 3 |
| (1, -4, 5) | (-3, 13, 1) | (4, -17, 2) | 1 |
| (-3, 13, 1) | (4, -17, 2) | (-7, 30, 1) | 1 |

$\therefore (18)^{-1} \mod 77 = 30$
$\therefore M = ((30)^2) \mod {77} = 900 \mod {77} = 53$

Thus, it is possible to extract $M$ from $C_e$ and $C_f$ without determining $\Phi(n)$. This attack is called a “Common Modulus Attack.” This is possible if same message is encrypted with different public keys, relatively prime to each other, and the modulus for both is the same.

## 3. Digital Signature (Using RSA)

User “A” can encrypt a message $X$ ($0 < M < n$) by its private key $(d, n)$.

$Y = X^d \mod n$

The cipher-text $Y$ can be decrypted by a recipient using the public key $(e, n)$ of “A”.

$Y \mod n = (X^d)^e \mod n = X$ (Original message)

## KEY MANAGEMENT USING PUBLIC-KEY CRYOGRAPHY

### 7.5.1 Diffie-Hellman Algorithm

This algorithm facilitates the exchange of a secret key among users. The key can subsequently used for encryption/decryption of messages using a symmetric cipher. The effectiveness of the algorithm depends on difficulty of discrete logarithms.

### 7.5.2 Global Parameters

The Diffie-Hellman Key Exchange makes use of two global parameters made public among the users:

- 1. A large prime number $p$
- 2. A primitive root $g$ of $p$.

If “A” and “B” wish to exchange a secret key, they proceed as follows:

User A:

- 1. Chooses a random number $X_A$ ($0 < X_A < \Phi(p)$)
- 2. Computes $Y_A = g^{X_A} \bmod p$
- 3. Keeps $X_A$ secret and transmits $Y_A$ to “B.”

On receiving the message from “A,” “B” responds as:

User B:

- 4. Chooses a random number $X_B$ ($0 < X_B < p-1$)
- 5. Computes $Y_B = g^{X_B} \bmod p$
- 6. Keeps $X_B$ secret and transmits $Y_B$ to “A.”

User A:

- 7. Now user “A” computes the key $K_A = (Y_B)^{X_A} \bmod p$
- 8. Similarly, user “B” computes the key $K_B = (Y_A)^{X_B} \bmod p$

The Diffie-Hellman Algorithm can be better represented as follows in Figure 7.1.

| User "A" | User "B" |
|---|---|
| Chooses $X_A$ such that $1 < X_A < \Phi(p)$ | Receives $Y_A$ from "A" |
| Computes $Y_A = g^{X_A} \bmod p$ | Chooses $X_B$ such that $1 < X_B < \Phi(p)$ |
| Sends $Y_A$ to user "B" | Computes $Y_B = g^{X_B} \bmod p$ |
| | Sends $Y_B$ to user "A" |
| Receives $Y_B$ from "B" | |
| Computes $K_A = (Y_B)^{X_A} \bmod p$ | Computes $K_B = (Y_A)^{X_B} \bmod p$ |

Figure 7.1 A schematic diagram of the Diffie-Hellman Algorithm.

## Example 7.3

Prove that the keys $K_A$ and $K_B$ computed by users “A” and “B” respectively are equal.

Solution:

The Proof is as follows:
$K_A = (Y_B)^{X_A} \bmod p$
$(g^{X_B} \bmod p)^{X_A} \bmod p$
$(g^{X_B X_A}) \bmod p$
$(g^{X_A} \bmod p)^{X_B} \bmod p$
$(Y_A)^{X_B} \bmod p$
K_B$

### 7.5.3 Strength of Diffie-Hellman Key-Exchange Scheme

- An adversary will have access to global parameters $p$ and $g$. Also, it can intercept $Y_A$ and $Y_B$ from the communication media.
- But, for determining $K$, the previous parameters are not sufficient. The adversary needs either $X_A$ or $X_B$. But these parameters are kept secret by "A" and "B" respectively. And, if $p$ is sufficiently large, then determining $X_A$ from $Y_A$ or determining $X_B$ from $Y_B$ is considered computationally infeasible.
- Thus, it is considered computationally infeasible for an adversary to compute the main key $K$ without knowledge of either $X_A$ or $X_B$.

## Example 7.4

Let
$p = 7, g = 3$ (a primitive root of 7).

Let
$X_A = 3, X_B = 5$
$= (g)^{X_A} \bmod p$
$= (3)^3 \bmod 7$
$= 6$
$= (g)^{X_B} \bmod p$
$= (3)^5 \bmod 7$
$= 5$

```
$K_A = (Y_B)^{X_A} \bmod p = (5)^3 \bmod 7 = 125 \bmod 7 = 6$
$K_B = (Y_A)^{X_B} \bmod p = (6)^5 \bmod 7 = 7776 \bmod 7 = 6$
```
