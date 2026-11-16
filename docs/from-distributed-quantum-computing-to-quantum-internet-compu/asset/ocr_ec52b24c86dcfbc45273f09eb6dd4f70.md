Other solutions have been developed for the DBA problem, including generalizations to any number of dishonest parties and with more than three generals as in Cholvi [2022], and earlier techniques such as Ben-Or and Hassidim [2005] and one using QKD protocols [Iblisdir and Gisin, 2004], to mention only a few.

# 3.2.7 Quantum Secret Sharing

We consider the problem of sharing a secret among multiple parties so that each party has part of the secret and cannot use the part to obtain the full secret, and the secret can only be put together by combining the parts from multiple (if not all) parties. More generally, one can consider a secret sharing scheme called the $(k, n)$-threshold scheme as follows: a secret is divided into $n$ shares such that any $k \le n$ of those shares can be used to assemble the secret, but any $k - 1$ shares would not provide any information about the secret.

In the classical case, consider three parties $A$, $B$, and $C$. $A$ wants to share a secret $s$, an $n$-bit string, shared among $B$ and $C$ so that only when $B$ and $C$ get together can the secret be reconstructed. One way to do this is for $A$ to take the secret $s$ and an $n$-bit random string $r$ and compute $s' = s \oplus r$ (where “$\oplus$” here denotes the bitwise addition modulo 2). $A$ then gives $s'$ to $B$ and the string $r$ to $C$. Note that at this point, neither $B$ or $C$ knows anything about $s$, but when they get together, they compute $s' \oplus r = s \oplus r \oplus r = s$, and so, obtains the secret $s$. There are other protocols to split $s$ into more than two shares. Such a protocol is subject to eavesdropping so that the shares $r$ and $s'$ might need to be encrypted using keys shared between $A$ and $B$ and between $A$ and $C$. A protocol such as QKD as we have seen can be used to general such keys for secret sharing.

Alternatively, quantum approaches using GHZ states can be used to split the secret as well as detect eavesdropping, without using QKD, and has been proposed as far back as the late 1990s [Hillery et al., 1999].

Here, we outline briefly the idea of a quantum secret sharing scheme, i.e. a (2,3)-threshold scheme, where a secret in this case is a quantum state of a quantum trit (or qutrit), as described in Cleve et al. [1999].

The secret qutrit $\alpha |0\rangle + \beta |1\rangle + \gamma |2\rangle$, with $\alpha^2 + \beta^2 + \gamma^2 = 1$, is encoded using three qutrits as follows:

```
\frac{1}{\sqrt{3}} [\alpha(|000\rangle + |111\rangle + |222\rangle) + \beta(|012\rangle + |120\rangle + |201\rangle) + \gamma(|021\rangle + |102\rangle + |210\rangle)]
```

And then each qutrit is one of three shares. From any one share, no information about the secret can be obtained since the party with the one share has equal mix of $|0\rangle$, $|1\rangle$ and $|2\rangle$ – for example, consider the party with the first qutrit, and suppose