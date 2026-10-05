
+   3. Computes $r = (g^k \bmod p) \bmod q$.
4. Computes $s = k^{-1} (m + rx) \bmod q$.

+   5. If $((r=0)$ or $(s=0))$ then repeats steps 1 to 4 by choosing another value of $k$. The parameters have to be non-zero, so that $s^{-1} \bmod q$ is defined.

+   6. Now, $(r, s)$ forms the digital signature which is sent to the intended recipient along with the message $M$.

## 8.8.3.4 Signature Verification Algorithm

Knowing the Public Key $(p, q, g, y)$ of use “A,” the recipient will verify the digital signature $(r, s)$ as follows:

+   1. Compute $m = H(M)$.

+   2. Verify that $t < r$ and $0 < s < q$; else reject the signature.

+   3. Compute $t = s^{-1} \bmod q$.

+   4. Compute $v = ((gm^y)^r \bmod p) \bmod q$

+   5. If $v = r$ then accept the signature; else reject it.

## Proof

$v = ((gm^y)^r \bmod p) \bmod q$
$= ((gm^{yr}) \bmod p) \bmod q$
$= ((g^{s+ry}) \bmod p) \bmod q$
Since $s = k^{-1}(m+rx)$
.: $(m+rx) = ks$
.: $v = ((g^{kst} \bmod q) \bmod p) \bmod q$
Since $t = s^{-1} \bmod q$
.: $st \bmod q = 1$
.: $v = (g^k \bmod p) \bmod q = r$
Thus, the Proof.

## 8.8.3.5 Why Are r and v Computed (mod p) and Then (mod q) but s and t Are Computed Directly (mod q)?

$r = (g^k \bmod p) \bmod q$

The argument for computation of $r$ is $g$, which is computed $(\bmod p)$. That is why $r$ is first computed $(\bmod p)$ and then $(\bmod q)$.

Similarly, $v = ((g^y)^k \bmod p) \bmod q$.

The arguments for $v$ are $g$ and $y$ and both have been computed $(\bmod p)$. That is why $v$ also first computed $(\bmod p)$ and then $(\bmod q)$.

$s = k^{-1} (m + rx) \bmod q$.

All the arguments of $s$, that is, $k, m, r$, and $x$, are integers less than $q$. That is why $s$ is computed $(\bmod q)$.

$T = s^{-1} \bmod q$

This argument holds for $s$ also holds for $t$.

![](img/d3b56042c756fbcc011ff06f1b9f53f0_409_0.png)

**FIGURE 8.19** A schematic diagram depicting DSA.

where

M: Message to be sent

H: Hash Function

$KR_s = (p, q, g, x)$ : Private Key of Sender

$p$: Prime Number (512 to 1024 bits long)

$q$: prime (160 bits long) such that $q$ divides $\Phi (p)$

$g = (h) \Phi^{y_q} \bmod p$, where $h \in \{0, 1, 2, \dots, \Phi(p)\}$ such that $g > 1$

$x$: a random integer $(1 < x < q)$

Sign: Signature Function

$k$: a random integer $(1 < k < q)$

$KU_x^g = (p, q, g, y)$ : Public Key of Sender

$r = (g^k \bmod p) \bmod q$

$s = k^{-1} (m + rx) \bmod q$. $(s \neq 0)$

$y = (g^y) \bmod p$

$v = ((g^y)^t) \bmod p \bmod q$ where $t = s^{-1} \bmod q$.

## **Example 8.4:** (DSA)

Let $p = 23, q = 11$ ($q$ divides $\Phi(p)$)
$g = (h) \Phi^{y_q} \bmod p$
Let $h = 2$
$g = (2)^{2/11} \bmod 23 = 4$
To verify that $g = 4$ has order 11 (mod 23):

| $x$ | $g^x \bmod 23$ |
|---|---|
| 1 | 4 |
| 2 | 16 |
| 3 | 18 |
| 4 | 3 |
| 5 | 12 |
| 6 | 2 |
| 7 | 8 |
| 8 | 9 |
| 9 | 13 |
| 10 | 6 |
| 11 | 1 |

Since all values $g^x \bmod 23$ ($1 \leq x \leq 11$) are distinct and less than 23, the order of $g \bmod 23$ is 11. Therefore $p = 23, q = 11$, and $g = 4$ form global parameters.

## 8.8.3.6 Determination of Keys by Authorized Signer

Let private key be $x = 3$
Then Public $y = g^x \bmod p = 4^3 \bmod 23 = 18$

## Signing of message by authorized signer

Let the $h$ value of the message to be signed $m = 5$ ($0 \le m < q$)
Let the random integer chosen by signer $k = 3$ ($1 < k < q$)
$r = (g^k \bmod p) \bmod q = (4^3 \bmod 23) \bmod 11 = (18) \bmod 11 = 7$
$s = k^{-1} (m+r) \bmod q = (3^{-1} (5 + 7)) \bmod 11 = (4) \bmod 11 = 5$
Digital Signature = $\{r, s\} = \{7, 5\}$

## Verification of the Signature by authorized Recipient

$t = s^{-1} \bmod q = 5^{-1} \bmod 11 = 9$
$v = ((g^m \times y^r) \bmod q$
$= ((4^5 \times 18^7)^9 \bmod 23) \bmod 11$
$= ((12 \times 6)^9 \bmod 23) \bmod 11$
$= ((3)^9 \bmod 23) \bmod 11$
$= ((4 \times 4 \times 4) \bmod 23) \bmod 11$
$= (18) \bmod 11 = 7$
Thus, $v = r = 7$ and signature stands.

$(4)^2 \bmod 23 = 16$
$(4)^4 \bmod 23 = 3$
$(4)^5 \bmod 23 = 3 \times 4 \bmod 23 = 12$
$(18)^2 \bmod 23 = 324 \bmod 23 = 2$
$(18)^4 \bmod 23 = 4$
$(18)^6 \bmod 23 = 8$
$(18)^7 \bmod 23 = (8 \times 18) \bmod 23 = 6$

## Example 8.5: (DSA) Construct an element of order 103 in the multiplicative group of residues mod 1237

Here, $p = 1237$
$q = 103; q$ divides $(p)$
Let $h = 2$
Then the element of 103 (mod 1237) = $g = (h) \Phi^{p(q)} \bmod p$
$= (2)^{1236/103} \bmod 1237$
$= (2)^{12} \bmod 1237$
= 385

## 8.9 EXERCISES

1. Differentiate between Source Authentication and Source Non-Repudiation. Can Source Non-Repudiation be provided by Symmetric Cryptography? Justify your answer.

2. What are the services provided by digital signatures? Does it provide (a) Source Authentication, (b) Data Integrity, and (c) Source Non-Repudiation?

3. Differentiate between Message Authentication Code (MAC) and Hash Value. Which one is encrypted?

4. What is the strength of MAC? Is MAC a reversible function? If no, does it pose any limitation or is designed to be so?

5. What are the characteristics of a good Hash Function?

6. What is a Birthday Attack on Digital Signatures? Can it be performed by an “Outsizer”?

7. What is the input message size in MD5 and SHA-1?

8. What is the Message Digest Size in MD5 and SHA-1?

9. What is the number of
