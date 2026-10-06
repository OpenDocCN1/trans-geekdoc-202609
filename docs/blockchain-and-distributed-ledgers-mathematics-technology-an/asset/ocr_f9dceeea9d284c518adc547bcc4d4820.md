# Table 4.4 Finite points belonging to the curve $E_{31}$.

| x | 0 | 0 | 1 | 1 | 4 | 4 | 5 | 5 | 7 | 7 |
|---|---|---|---|---|---|---|---|---|---||}{
| y | 10 | 21 | 15 | 16 | 3 | 28 | 15 | 16 | 3 | 28 |
| # | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
| x | 11 | 11 | 20 | 24 | 24 | 25 | 25 | 27 | 27 | |
| y | 6 | 25 | 38 | 6 | 25 | 15 | 16 | 6 | 25 |
| # | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 |

All finite points belonging to the curve $E_{31}$ are shown in Table 4.4.
Besides, there is the neutral element (infinity) $O$. We assign # 0 to $O$. Thus, there are 21 points in total, including the neutral element (infinity).

In general, Hesse's theorem estimates the total number of points on a discrete elliptic $E_p$. We emphasize that in contrast to statements like “Assume that $f$ is a good cryptographic trapdoor function”, Hesse's theorem is a “real” theorem and can be proven rigorously.^5$

**Theorem 4.5.** Hesse's theorem: The total number of points $N$ on a discrete elliptic curve satisfies the following inequality:

```
$|N - (p+1)| < 2\sqrt{p}$.
```

If a point $(x,y)$ belongs to the elliptic curve, $(x,y) \in E_p$ so does $(x, p-y)$. There are $p$ possible absciss, roughly half of these absciss belonging to $E_p$. Finding the exact value of the correction

```
$t = N - (p+1)$,
```

is extremely important for cryptographic purposes to know the exact value of the correction, given by Eq. (4.137), which can be done via a very efficient Schoof’s algorithm; see Schoof (1985). $\#E_p$ denotes the number of points on the curve.
It is easy to check that for $E_{31}$ inequality is valid:

```
$|21 - 32| = 11 < 2 \times 5$.
```

Interestingly, there are “few” points on the curve in question, so that Hesse’s theorem barely holds.
Table 4.5 shows how to add points on $E_{31}$.

> ^5However, it is a conditional statement of the form “If $p$ is prime, then ...”.