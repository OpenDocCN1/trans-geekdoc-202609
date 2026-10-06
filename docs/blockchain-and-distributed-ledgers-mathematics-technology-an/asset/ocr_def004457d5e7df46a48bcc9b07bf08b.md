# Blockchain and Distributed Ledgers: Mathematics, Technology, and Economics

![](bbox=[0.143, 0.073, 0.856, 0.403])

**Figure 4.4** Conceptual framework for blind signature algorithm underlying anonymous digital cash. Alice sends N messages for signature to her bank. The bank checks randomly-chosen N−1 messages for validity and, if satisfied, signs the remaining message blindly. Alice sends message signed by the bank to Bob, who in turn, submits it to the bank for payment. Own graphics.

Digcach solves some of the problems Bitcoin wishes to solve, except for one crucial aspect — it is centralized and relies on the trusted third party — Ben the Banker. Alice is the first, and Bob is the second vertex in the corresponding triangle.

# 4.6 Finite field cryptography

# 4.6.1 Definitions

So far, we have looked at one possible candidate for a trapdoor function — exponent n = pq. Are there other possibilities? Yes, for instance, discrete logarithms p are as to compute as factoring of n — same complexity as before! As we see shortly, discrete logarithms have some useful features; for example, one can use them for the so-called Diffie-Hellman key exchange. With some additional tricks, one can utilize discrete logarithms to build trapdoor functions.

We start with some useful definitions. Let's define discrete logarithms as solutions of the congruence:

```
$\alpha^x = y \pmod p, \quad x = \log_{\alpha}(y) \equiv L_{\alpha}(y). \quad (4.64)$
```