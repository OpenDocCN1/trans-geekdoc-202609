# Chapter 4 Essential Cryptographic Tools | 121

![](bbox=[0.301, 0.107, 0.698, 0.335])

![](bbox=[0.301, 0.368, 0.698, 0.597])

**Figure 4.13** A geometric approach to producing the addition table: (a) (4, 28) + (24, 6) = (7, 28); (b) (5, 15) + (20, 3) = (24, 25). Own graphics.

The discrete log problem requires finding $k$ for a given triple $(p, \alpha, \alpha)$. We can formulate its elliptic curve version as follows: Given $E_T$, and a point $A \in \mathbb{E}_G$. find $k$, such that

> $A = k \times G = ((G + G) + G) + ... + G).$ (4.145)

When $E_t = \mathbb{E}_G$, the problem becomes particular to formulate (but, in general, very difficult to solve!). Given a point $A \in E_T$, find $k$, such that $A = k \times G$.

In many respects problems (4.64) and (4.145) are similar! Given this fact, we can develop the elliptic curve version of the ElGamal signature and the Diffie-Hellman key exchange.