
In order to facilitate calculations with concrete values of the K polynomials, consider the product $K_1(X)K_k(X)$. This is a polynomial of degree $k + 1$ and therefore has to be a linear combination of the $K_i(X)$ for $i \le k + 1$. In fact, go back to the definition of the K coefficients and fix a vector $x$ of weight $i$ :

$$K_1(i)K_k(i) = \left( \sum_{wt(u)=1} \zeta^{u\cdot x}\right)\left( \sum_{wt(v)=k} \zeta^{v\cdot x}\right) = \sum_{u,v} \zeta^{(u+v)\cdot x}.$$

Clearly $wt(u+v)$ is between $k - 1$ and $k + 1$. Let $wt(z) = k - 1$. The number of pairs $u, v$ as above such that $u + v = z$ does not depend on the choice of $z$. Denote this number by $p_{1,k}^{k-1}$. Analogously the numbers $p_{1,k}^k$ and $p_{1,k}^{k+1}$ are defined. The following is obtained:

$$K_1(i)K_k(i) = p_{1,k}^{k+1}K_{k+1}(i) + p_{1,k}^k K_k(i) + p_{1,k}^{k-1}K_{k-1}(i).$$

Also, it is an easy combinatorial exercise to compute those coefficients:

### 15.31 Theorem.

$$K_1(i)K_k(i) = (k + 1)K_{k+1}(i) + (v - 2)kK_k(i) + (v - 1)(n - k + 1)K_{k-1}(i).$$

In general, the existence of constants $p_{i,j}^k$ as above expresses the fact that Hamming space is an **association scheme**.

### 15.32 Definition.

Let $z$ be a vector of weight $k$ in $n$-dimensional $v$-ary Hamming space. Let $p_{i,j}^k$ be the number of vectors $x$ such that $wt(x) = i$ and $d(x,z) = j$.

The values used in Theorem 15.31 are $$p_{1,k}^{k+1}=k+1,\; p_{1,k}^k=(v-2)k,\; p_{1,k}^{k-1}=(v-1)(n-k+1).$$

### 15.33 Theorem.

For every natural number $r$ between $0$ and $n$ and for $0 \le i,j \le n$, we have $$K_i(r)K_j(r)=\sum_{k=0}^{n} p_{ij}^{(k)} K_k(r). \tag{15.7}$$

If $i+j \le n$, then it follows that the polynomials themselves satisfy this relation: $$K_i(X)K_j(X)=\sum_{k=0}^{n} p_{ij}^{(k)} K_k(X) \text{ if } i+j \le n. \tag{15.8}$$

The following obvious corollary will be used in Section 15.4.

### 15.34 Corollary.

If $p_1(X)$ and $p_2(X)$ have nonnegative $K$ coefficients, then the same is true of $p_1(X)p_2(X)$.

## Optimality of the Best code

In the final chapter we will encounter the **Best code**, a $(10,40,4)_2$ code. In the present section we wish to prove its optimality, as an application of the **LP** method. Here we follow the lines of [14].

### 15.35 Theorem.
*There is no $(10,41,4)_2$ code and no $(9,21,4)_2$ code.*

**PROOF** By shortening it suffices to prove the second statement of the theorem. Assume a $(9,21,4)_2$ code exists. Then there exists such a code all of whose weights are even. The unknowns are the rational numbers

$$x = A_4,\quad y = A_6,\quad z = A_8$$

and $M = 1 + x + y + z$. An obvious inequality is $z = A_8 \le 1$. Consider the transforms $A'_k$ for $k = 1,2,3,4$. The K coefficients can be calculated recursively from Theorem 15.31:

$$(k + 1)K_{k+1}(i) = (9 - 2i)K_k(i) - (10 - k)K_{k-1}(i)$$

using $K_0(i) = 1$, $K_1(i) = 9 - 2i$. For example,

$$A'_1 = (1/21)(9 + x - 3y - 7z) \ge 0.$$

Likewise, as $K_2(i) = 2i^2 - 18i + 36$, we have

$$A'_2 = (1/21)(36 - 4x + 20z) \ge 0.$$

The inequality $A'_k \ge 0$ takes the form

$$-K_k(4)x - K_k(6)y - K_k(8)z \le \binom{9}{k}.$$

Use these inequalities for $k = 1,2,3,4$ together with the obvious inequality $z \le 1$. This leads to the following linear program:

$$ \begin{aligned}
 -x + 3y + 7z &\le 9\\
x - 5z &\le 9\\
x - 2y + 7z &\le 21\\
-3x + 3y - 7z &\le 63\\
z &\le 1
\end{aligned}$$

In order to obtain a basic LP problem, introduce five additional variables $y_1,y_2,y_3,y_4,y_5$ as described after Definition 15.1. The starting vertex is then $\mathbf{x}_0 = (0,0,0,9,9,21,63,1)$, the basis is $Z = \{4,5,6,7,8\}$ and clearly we have the objective function $Q = -x - y - z$. The starting array is

1 2 3   x₀
4 -1 3 7   9
5 1 0 -5   9
6 1 -2 7  21
7 -3 3 -7  63
8 0 0 1   1
1 1 1   Q₀ = 0

As the bottom entry in the first column is positive, we choose this column as the pivot column. The pivot element is printed in bold. Proceeding in this fashion the following arrays are obtained:

5 2 3   x₁
4 1 3 2   18
1 1 0 -5   9
6 -1 -2 12  12
7 3 3 -22  90
8 0 0 1   1
-1 1 6   Q₁ = -9

5 4 3   x₂
2 1/3 1/3 2/3   6
1 1 0 -5   9
6 -1/3 2/3 40/3  24/3
7 2 -1 -24  72
8 0 0 1   1
-4/3 -1/3 16/3   Q₂ = -15

5 4 8   x₃
2     -2/3   16/3
1     5   14
6     -40/3
7     24
3     1   1
-4/3 -1/3 -16/3   Q₃ = -20 1/3

As the entries d_i in the last row are negative, we have reached the minimum. Observe that there is no need to calculate all the entries in this last array. We conclude that M = 1 + x + y + z ≤ 1 − Q₃ = 21 1/3, hence M ≤ 21.

Now assume a code (9, 21, 4) exists. As M is odd, the basic relation between A'_k and the Fourier transform (see the calculation after Definition 15.22) shows that in fact A'_k ≥ (9 choose k)/M². This leads to a strengthened inequality

−K_k(4)x − K_k(6)y − K_k(8)z ≤ (9 choose k) (M − 1)/M,

with a factor of (M − 1)/M = 20/21 on the right side. If you think about it, also the last inequality z ≤ 1 can be strengthened. As M is odd, it cannot be that all codewords have a partner at distance 8, so in fact z ≤ 20/21. The right sides of the inequalities pick up a factor of 20/21. The same is true of the objective value: the contradiction M ≤ 1 + 20·61/63 < 21 is obtained.

## 15.3 Some explicit LP bounds

The easiest way to derive an explicit bound from the general LP bound of Theorem 15.30 is to use polynomials of small degree. Degree 1 leads to the Plotkin bound: recall K₁(X) = (v − 1)n − vX. We must have p(X) = 1 + cX where c ≥ 0. The second condition to satisfy is then p(r) ≤ 0. This is possible only if K₁(r) < 0. The optimal choice is then c = −1/K₁(r) and the bound is p(0) = 1 + c(v − 1)n = vr/(vr − (v − 1)n). In the case of codes, this is the Plotkin bound. As for OA, the following is obtained:

### 15.36 Theorem (dual Plotkin bound).
Let M be the number of rows of a v-ary OA of strength t. Then

$$\frac{v^n}{M} \le \frac{v(t+1)}{v(t+1)-n(v-1)}$$ 

provided the expression on the right is > 0.

This is a strong bound on OA of large strength ((t+1)/n > (v−1)/v) just as the Plotkin bound on codes is useful for codes of large minimum distance. Reconsider the family of additive codes and OA from Theorem 16.29. They have length n = q^a, are q^b-ary (where a ≥ b > 0) and have M = q^{a+b} codewords. The minimum distance is d = q^a − q^{a−b}, and the strength is 2. We encountered them again in Section 18.1 (see Theorem 18.3), where they were called C(a,b) and used in the Bose-Bush construction. The minimum distance is rather large but not large enough to apply the Plotkin bound (the Plotkin bound would require \frac{q^a − q^{a−b}}{q^a} > \frac{q^b − 1}{q^b}, which is not satisfied: we have equality instead of strict inequality). This motivates us to generalize the Plotkin bound, applying Theorem 15.30 not to linear but to quadratic polynomials.

Choose p(X) = a(X − r)(X − n) for a > 0. The nonpositivity condition of Theorem 15.30 is then satisfied. As p(0) = arn, we want to minimize a. Let p(X) = c₀ + c₁K₁(X) + c₂K₂(X). We have to choose a such that c₀ = 1, c₁, c₂ ≥ 0. Recall the value of K₁(X) given above and observe that

$$K₂(X) = \frac{v^2}{2}X^2 - v\big[(v-1)(n-1)+v/2\big]X + \binom{n}{2}(v-1)^2.$$

Comparing coefficients, we obtain a = c2 v^2 /2,

c1 = c2 { v/2 (r + 1 - n) + n - 1 }, c2 = 2 / [n[vr - (n - 1)(v - 1)]]

provided the denominator of the last expression is positive. It follows that p(0) = v^2 r / [vr - (n - 1)(v - 1)]. This bound is never better than the Plotkin bound as long as the Plotkin bound is applicable. The quadratic bound is interesting when $(n - 1)(v - 1)/v < r \le n(v - 1)/v$.

### 15.37 Theorem.
Let $(n - 1)(v - 1)/v < d \le n(v - 1)/v$. If an $(n, M, d)_v$ code exists, then

M <= v^2 d / [v d - (n - 1)(v - 1)]

Let $(n - 1)(v - 1)/v < t + 1 \le n(v - 1)/v$. If there is a v-ary OA of length n and strength t with M rows, then

v^n / M <= v^2 (t + 1) / [v(t + 1) - (n - 1)(v - 1)]

The quadratic bound applies to our $(q^a, q^{a+b}, q^a - q^{a-b})_{q^b}$ codes C(a,b). The bound on M is in fact reached with equality.

The Singleton bound on codes is also an example of this mechanism. Surprisingly its derivation is rather involved. Our direct proof in Chapter 4 was clear and short in comparison. The corresponding polynomial is

p(X) = v^{n - r + 1} . (n - X choose n - r + 1) / (n choose r - 1) = sum_{k=0}^n (n - k choose r - 1) / (n choose r - 1) . K_k(X). (15.9)

The dual Singleton bound states that v^t is a lower bound on the number of rows of a v-ary OA of strength t. This is a triviality.

For the sphere-packing bound, the situation is even more extreme. Our direct proof from Section 1.6 is all but trivial whereas the derivation from the LP bound is rather involved. The underlying polynomial is p(X) = sum_{k=0}^n c_k K_k(X), where c_k = (Psi_s(k)/V)^2 and Psi_s(X) = sum_{l=0}^s K_l(X), V = V_v(s,n) (see Definition 1.11) and s is maximal such that 2s < r. However, the dual sphere-packing bound is interesting. It is known as the Rao bound:

### 15.38 Theorem (Rao bound).
Let M = lambda v^t be the number of rows of a v-ary OA of strength t and length n. Let e' = [t/2]. Then

M >= sum_{i=0}^{e'} (n choose i) (v - 1)^i

For odd t the Rao bound can be strengthened. In this text we only needed the strength 2 case of the Rao bound in Theorem 15.38. This is the Bose-Bush bound Theorem 9.6, which we derived from the Plotkin bound for codes.
