
## 21.1 Feige-Fiat-Shamir

The $n$ should be at least 512 bits long. (Of course, there has been considerable progress in factoring then.)

If each chooses his own $n$ and publishes it in a public key file, they can dispense with the arbitrator. However, RSA-like variant makes the scheme considerably less convenient.

## Fiat-Shamir Signature Scheme

Turning this identification scheme into a signature scheme is basically a matter of turning Victor into a hash function. The primary benefit of the Fiat-Shamir signature scheme over RSA is: Fiat-Shamir requires only 1 percent to 4 percent of the modular multiplications of RSA. For this protocol, we'll bring Alice and Bob.

The setup is the same as the identification scheme. Choose $n$ to be the product of two large primes. Generate the public key, $v_1, v_2, \dots, v_h$, and the private key, $s_1, s_2, \dots, s_h$, such that $s_i^2 \equiv v_i \pmod n$.

- [1] Alice picks $t$ random integers between 1 and $n$: $t_1, t_2, \dots, t_t$, and computes $x_1, x_2, \dots, x_t$ such that $x_i = t_i^2 \pmod n$.

- [2] Alice hashes the collision of the message and the signature of $x$ to generate a stream: $H(m, x_1, x_2, \dots, x_t)$. She uses the first $k \cdot t$ bits of this stream as values of $b_{ij}$, where $i$ goes from 1 to $t$, and $j$ goes from 1 to $k$.

- [3] Alice computes $y_1, y_2, \dots, y_t$ where:
$y_i = t_i^{b_{i1}} \cdot s_1^{b_{i2}} \cdot \dots \cdot s_h^{b_{ih}} \pmod n$
(For $i$, she multiplies the values of the $s_j$ based on the random $b_{ij}$ values. If $b_{ij}$ is 1, then $s_j$ is multiplied; if $b_{ij}$ is 0, then $s_j$ is not multiplied.)

- [4] Alice sends Bob $m$, the values of $b_{ij}$ and all the values of $y_i$. Bob already has Alice's public key: $v_1, v_2, \dots, v_k$.

- [5] Bob computes $z_1, z_2, \dots, z_t$, where:
$z_i = y_i^2 \cdot v_1^{b_{i1}} \cdot v_2^{b_{i2}} \cdot \dots \cdot v_h^{b_{ih}} \pmod n$
(Again, Bob multiplies based on the $b_{ij}$ values.) Also note that $z_i$ should be equal to $x_i$,

- (6) Bob verifies that the first $k \cdot t$ bits of $H(m, z_1, z_2, \dots, z_t)$ are the $b_{ij}$ values that Alice sent.

As with the identification scheme, the security of this signature scheme is proportional to $2^k$. It also depends on the difficulty of factoring $n$. Feige and Shamir pointed out that forging a signature is easier when the complexity of factoring $n$ is considerably lower than $2^k$. And, because of birthday-type attacks [see Section 18.1], they recommend that $k \cdot t$ be increased from 20 to at least 72. They suggest $k=9$ and $t=8$.

## Improved Fiat-Shamir Signature Scheme

Silvio Miciai and Adi Shamir improved the Fiat-Shamir protocol in [1088]. They chose $v_1, v_2, \dots, v_k$ to be the first $k$ prime numbers. So

$v_1 = 2, v_2 = 3, v_3 = 5$, and so on.

This is the public key.
The private key, $s_1, s_2, \dots, s_k$ is a random square root, determined by:

`$s_i = \sqrt{v_i^{-1}} \pmod n$`

In this version, every person must have a different $n$. The modification makes it easier to verify signatures. The time required to generate signatures, and the security of those signatures, is unaffected.

## Other Enhancements

There is also N-party identification scheme, based on the Fiat-Shamir algorithm [264]. Two other improvements to the Fiat-Shamir scheme are proposed in [1218]. Another variant is [1368].

## Ohtat-Okamoto Identification Scheme

This protocol is a modification of the Feige-Shamir identification scheme and gets its security from the difficulty of factoring [1198, 1199]. The same authors also wrote a multisignature scheme (see Section 23.1), by which number of different people can sequentially sign a message [1200]. This scheme has been proposed for smart-card implementation [850].

## Patents

Fiat-Shamir is patented [1427]. Anyone interested in licensing the algorithm should contact Ydea Research and Development, The Weizmann Institute of Science, Rehovot, Israel.

## GUILLOU-QUISCARTER

Feige-Shamir was the first identification-based protocol. It minimized computation by reducing the number of iterations. For some implementations, like smart cards, this is less ideal. Exchanges with the outside world are time-consuming, and the storage required for each iteration can strain the resources of card. For the same level of security, the computation required by Guillou-Quisater is greater than Feige-Shamir by a factor of three.

## Guillou-Quisater Identification Scheme

Like Feige-Shamir, this identification algorithm can be converted to a digital signature. Peggy is a smart card who wants to prove her identity to Victor. Peggy's identity consists of a set of credentials: a data string consisting of name, account number, and whatever else. This bit string is analogous to the public key. Other information, shared by all "system", is an exponent $v$ and modulus $n$, where $n$ is the product of two primes. The private key is $B$, calculated such that $JB \equiv 1 \pmod{n}$. Now, she wants to convince Victor that she knows B. Here's protocol:

- (1) Peggy picks a random integer $r$, that is between 1 and $n-1$. She computes $T = r^v \pmod n$ and sends it to Victor.

- (2) Victor picks a random integer $d$, that is between 0 and $v-1$. He sends $d$ to Peggy.

- (3) Peggy computes $D = RB^v \pmod n$, and sends it to Victor.

- (4) Victor computes $T' = D^d \pmod n$. If $T = T' \pmod n$, the authentication succeeds. The math is not complex:
$T' = (RB^v)^d = r^d B^{vd} = r^d (1)^v = T \pmod n$

## Guillou-Quisater Signature Scheme

This identification can be converted to a signature scheme also suited for smart-card implementation. The public and private key setup is the same as before. Here's the protocol:

- (1) Alice picks a random integer $r$, that between 1 and $n-1$. She computes $T = r^v \pmod n$.

- (2) Alice computes $d = H(M,T)$, where $M$ is the message signed and $H(x)$ is a one-way hash function. The $d$ produced by the hash function must be between 0 and $v-1$. If the output of the hash function is not within range, it must be reduced modulo $v$.

- (3) Alice computes $D = rB^d \pmod n$. The signature consists of the message $M$, two calculated values, $d$ and $D$. She sends this to Bob.

- (4) Bob computes $T = r^d \pmod n$. He then computes $d' = H(M,T)$. If $d = d'$, Alice must know Bob and $B$ is the signature.

## Multiple Signatures

If many people want to sign the same document? The easy solution has each signing separately, but this signature scheme can do better than that. Alice and Bob sign the same document and Carol verifies the signatures, but any number of people can be involved in the signature process. Alice and Bob have their own unique $J$ and $B$ values: $[J_A, B_A]$ and $[J_B, B_B]$. The values $n$ and $v$ are common to the system.

- (1) Alice picks a random integer, $r_A$, that is between 1 and $n-1$. She computes $T_A = r_A^{d_A} \pmod n$ and sends $T_A$ to Bob.

- (2) Bob picks a random integer, $r_B$, that is between 1 and $n-1$. He computes $T_B = r_B^{d_B} \pmod n$ and sends $T_B$ to Alice.

- (3) Alice and Bob compute $T=[T_A,T_B] \pmod n$.

- (4) Alice and Bob compute $d = H(M,T)$, where $M$ is the message signed and $H[x]$ is a one-way hash function. The $d$ produced by the hash function must be within this range, $0$ and $v-1$. If the output of the hash function is not within this range, it must be reduced modulo $v$.

- (5) Alice computes $D_A = r_A^{d_A} \pmod n$ and sends $D_A$ to Bob.

- (6) Bob computes $D_B = r_B^{d_B} \pmod n$ and sends $D_B$ to Alice.

- (7) Alice and Bob compute $D=[D_A,D_B] \pmod n$. The signature consists of the credentials, $M$, the two calculated values, $d$ and $D$, and her credentials of credentials: $J_A$ and $J_B$.

- (8) Carol computes $J=[J_A,J_B] \pmod n$.

- (9) Carol computes $T' = D^{d'} \pmod n$. She computes $d'=H(M,T)$. If $d=d'$, then the multiple signature is valid.

## 21.3 SCHNORR

Claus Schnorr's authentication and signature scheme [1396,197] ensures its security from the difficulty of calculating discrete logarithms. To generate a key pair, first
