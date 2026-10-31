# LP bounds for codes and OA

Let $C \subseteq E^n$ be a multisubset, which we identify with its characteristic function $\chi_C \in L^2(V)$. As a tool to derive bounds, we use the distance distribution $(A_i)$ of $C$ :

**15.21 Definition.** Let $\mathcal{C}$ be a $q$-ary code of length $n$. The distance distribution of $\mathcal{C}$ is the $(n+1)$-tuple of rational numbers $A_i$, $i = 0,1,\dots,n$, where

$A_i = \frac{1}{|\mathcal{C}|} \bigl(\#\{(x,y) \mid x,y \in \mathcal{C}, d(x,y)=i\}\bigr)$.

The distance polynomial of $\mathcal{C}$ is $W_{\mathcal{C}}(X,Y)=\sum_{i=0}^{n} A_i X^{n-i}Y^{i}$.

We encountered this earlier, in Section 3.5, where we derived the MacWilliams transform for linear codes. In the case of a linear or additive code, $A_i$ is the number of codewords of weight $i$. Clearly always $A_0 = 1$. By definition the $A_i$ are nonnegative rational numbers and the minimum distance is the smallest $i > 0$ such that $A_i > 0$. Also $\sum A_i = M$, the number of codewords.

Here comes the key idea: We wish to define a transform $(A'_k)$ of the weight distribution which satisfies the following conditions:

+   - $A'_k \ge 0$ for all $k$, and
+   - $C$ is an OA of strength $t$ if and only if $A'_1 = \cdots = A'_t = 0$.

The fact that $(A'_k)$ is a transform of $(A_i)$ means that we can write

$A'_k = \frac{1}{M} \sum_{i} A_i K_k(i)$

for suitable coefficients $K_k(i)$. How are we going to choose those coefficients? The following definition will be justified by two lines of computation which suffice to check that the conditions above are satisfied. Here is the definition.

**15.22 Definition.**

$K_k(i) = \sum_{z:\ wt(z)=k} \zeta^{x\cdot z}$, 

where $x$ is a vector of weight $i$.

It is rather obvious that this expression is indeed independent of the choice of $x$. This follows from Lemma 15.24 below. Here comes the justification: