# 17.5 Proposition. Let q be a power of 2. Using representatives of a hyperoval in PG(2,q) as columns of a generator matrix defines a [q + 2, 3, q]_q code.

The first example beyond the familiar hexacode is a [10,3,8]_8 code. Here is its generator matrix:

```
\begin{pmatrix}1&1&1&1&1&1&1&1&0&0\\0&1&\epsilon&\epsilon^2&\epsilon^3&\epsilon^4&\epsilon^5&\epsilon^6&0&1\\0&1&\epsilon^2&\epsilon^4&\epsilon^6&\epsilon&\epsilon^3&\epsilon^5&1&0\end{pmatrix}
```

# Codes of dimension 2

Our newly gained geometric insight makes it easy to decide the existence of two-dimensional linear codes. When will a code [n,2,d]_q exist? Apply Theorem 17.1. The projective line PG(1,q) has q+1 points. Each point is a hyperplane. Let w_i be the weight of point P_i, i=1,...,q+1, where notation is chosen such that 0 ≤ w1 ≤ w2⋯ ≤ w_{q+1}. We must have w1+⋯+w_{q+1}=n and w1+⋯+w_q = d. In particular, the largest weight of a point is w_{q+1}= n−d. As w1+⋯+w_q is bounded by q w_{q+1}= q(n−d), the code will exist if and only if q(n−d) ≥ d, equivalently, if n ≥ (q+1)/q d. Compare this with the Griesmer bound (Theorem 5.7). It says that a necessary condition for an [n,2,d]_q code to exist is n ≥ d + ⌈d/q⌉. This is equivalent to n ≥ d + d/q = (q+1)/q d. It follows that the Griesmer bound is always met with equality in the case of two-dimensional codes.

# 17.6 Theorem. An [n,2,d]_q code exists if and only if the Griesmer bound does not exclude it. The precise condition is n ≥ d + d/q = (q+1)d/q.

As an example, what is the smallest n such that [n,2,8]_7 exists? The Griesmer bound shows n ≥ 8 + 8/7, so n ≥ 10. It follows from Theorem 17.6 that a [10,2,8]_7 does indeed exist. The largest weight of a point is n−d = 2. We can use as weights of points 2,2,1,1,1,1,1,1. This is not the only choice. Another possibility is to choose weights 2,2,2,2,2,0,0,0. One possible generator matrix corresponding to the former choice of weights is

```
G = \begin{pmatrix}0&0&1&1&1&1&1&1&1\\1&1&0&0&1&2&3&4&5&6\end{pmatrix}.
```

# Codes of dimension 3

This is the lowest dimension where open problems remain. We want to prove that, for d large enough, there are always [n,3,d]_q codes meeting the