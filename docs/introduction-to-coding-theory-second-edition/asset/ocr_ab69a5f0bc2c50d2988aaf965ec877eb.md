rational function field there. The strategy is to construct a suitable polynomial $Q(X,Y)$ with the property that every polynomial $f(X)$ on the **list** contributes a linear factor $Y - f(X)$ of $Q(X,Y)$. This will be the case if $f(X)$ is a root of $Q(X,Y)$, equivalently, if $Q(X, f(X))$ is the 0 polynomial.

Here is the trick: fix a **multiplicity** $r$ and choose $Q(X,Y)$ such that the following conditions are satisfied. For each pair $(x_i, y_i)$ we demand that the shifted polynomial defined by $Q^{(i)}(X,Y)=Q(X+x_i,Y+y_i)$ does not have terms of degree less than $r$. In particular, we demand $Q(x_i,y_i)=0$. As the number of such terms is $inom{r+1}{2}$, this gives $ninom{r+1}{2}$ linear equations for the coefficients of $Q(X,Y)$ to satisfy. Let us see what the consequences are when these conditions are satisfied.

For fixed $i$, let $f(X)$ be a polynomial satisfying $f(x_i)=y_i$ and consider the polynomial $g(X)=Q(X,f(X))$ (which we wish to be the 0 polynomial if $f(X)$ is on the **list**). We have

$g(X + x_i)=Q(X + x_i, f(X + x_i))=Q^{(i)}(X, f(X + x_i)-y_i).$

As $f(X + x_i)-y_i$ is a multiple of $X$, it follows that $X^r$ divides $g(X + x_i)$ and therefore that $(X - x_i)^r$ divides $g(X)$. Now let $f(X)$ be on the **list**. Then $g(X)$ is a multiple of $(X - x_i)^r$ for all $i$ such that $f(x_i)=y_i$. There are at least $t$ such indices $i$. If we can manage that the degree of $g(X)$ is $< r t$, it follows that $g(X)$ is the 0 polynomial (as the 0 polynomial is the only polynomial of degree $\le n$ with more than $n$ roots, for any $n$).

Recall that $f(X)$ has degree $\le k$. It follows that the degree of $g(X)$ is guaranteed to be $< r t$ if all monomials $X^i Y^j$ occurring in $Q(X,Y)$ satisfy $i + k j < r t$. This is it. We just need to write down the conditions explicitly and to work out when they can be satisfied.

The number of monomials in question equals the number of nonnegative solutions $(i,j)$ of the inequality $i + k j \le l$, where $l = r t - 1$. This number is

$(\lfloor l/k \rfloor + 1)(2l + 2 - k\lfloor l/k \rfloor)/2$

(see Exercise 23.1.1). The first factor $\lfloor l/k \rfloor + 1$ is $(l + k)/k$ if $k$ divides $l$; it is $\ge (l + 1)/k$ otherwise. This gives us a lower bound of $(l + 1)(l + 2)/(2k)$ on the number of monomials. The condition $l < r t$ will be satisfied if we choose $l = r t - 1$. Only one condition remains to be satisfied. The polynomial $Q(X,Y)$ must be nonzero such that its coefficients satisfy some $n\binom{r+1}{2}$ linear equations. This can be done provided the number of monomials is larger than the number of constraints. Using $l = r t - 1$, the condition becomes $r t (r t + 1)/k > n r (r + 1)$, equivalently, $r(t^2 - k n) > k n - t$. This can be done as long as $t^2 > k n$.

We sum up: assume $t^2 > k n$, equivalently $t > \sqrt{k n}$. Dividing by $n$ we obtain the equivalent condition $t/n = 1 - \delta > \sqrt{R}$, where $R$ is the information rate and $\delta$ the relative minimum distance. Use multiplicity $r$ such that $r > (k n - t)/(t^2 - k n)$. Find a nonzero polynomial $Q(X,Y)=\sum_{i,j} q_{ij} X^i Y^j$ with coefficients $q_{ij} \in F$ where the sum is over all pairs $i,j$ such that $i + k j \le r t - 1$