# 312 • NETWORK SECURITY AND CRYPTOGRAPHY

The number of points N in $E(a, b)$ is bounded by:
$(p+1)-2\sqrt{p} \le N \le (p+1)+2\sqrt{p}$

For a large $p$, $2\sqrt{p}$ will be insignificant compared to $p$.
:.\sqrt{p}$

# 7.7.6 Rules for Addition (+) Operation over $E_p, (a, b)$

Let $P, Q$ be the points in $E_p(a, b)$, such that $P: (X_p, Y_p)$ and $Q: (X_q, Y_q).
The addition within $E_p(a, b)$ follows the following rules:

+   1. O is an additive identity element.
.: $P+O = P$

+   2. $(-P) = (x_p, -y_p)$ will have the additive inverse of $P$.
.: $P+(-P) = O$

+   3. $R = (P+Q) = (x_r, y_r)$ will be the point from the Elliptic Curve Set $E_p(a, b)$.nThe $x_r$ coordinates of $R$ are determined as follows:
$x_r = (\lambda^2 - x_p - x_q) \mod p$
$y_r = ((\lambda(x_p - x_r) - y_p) \mod p$
where $\lambda = \left((y_q - y_p)/(x_q - x_p)\mod pight)\left((3X_p^2 + a)/2y_p\mod pight)$

Special Case
Suppose $P = (x_p, 0)$, then $(-P) = P = (x_p', 0)$.
Then $2P$ is defined as $2P = P+P = P+(-P) = O$

# 7.7.7 Multiplication over the Set $E_p(a, b)$

The multiplication $kP$ (where $P \in E_p(a, b)$ and $k$ is an integer) is as the repeated addition of $P$, $k$-times:

$kP = P+P+P+ \dots$ (k times)

# Order of a Point G

+   * Let G be a point in the set $E_p(a, b)$.
* The order of a point $G$ is defined as the least integer $n$ that satisfies $nG = O$.
* Then set $\langle G, 2G, \dots, nG angle$ represents a set of distinct points from $E_p(a, b)$.