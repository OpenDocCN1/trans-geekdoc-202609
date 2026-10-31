# Quadratic equations in characteristic 2

Consider the quadratic equation

$$x^2 + a x + b = 0$$

with coefficients $a, b \in \mathbb{F}_q$. Let $q$ be a power of 2. The distinction between squares and nonsquares is no longer available. In fact, as squaring is a field automorphism (see Section 12.1, the Frobenius automorphism), every element of $\mathbb{F}_q$ is a square and possesses a unique square root. In particular, if $a = 0$, the equation $x^2 + b = 0$ has a unique solution. If $a \neq 0$, we divide by $a^2$. With $y = x/a$ the quadratic equation becomes $y^2 + y + (b/a^2) = 0$. The absolute trace $tr$ yields a condition: as $tr(y^2) = tr(y)$, we must have $tr(b/a^2) = 0$ if there is a solution. As each such quadratic equation cannot have more than two solutions, an obvious counting argument shows now that this condition is also sufficient: whenever $tr(b/a^2) = 0$, our quadratic equation has two solutions.

**17.21 Proposition.** Let $q$ be a power of 2. The quadratic equation $x^2 + a x + b = 0$, where $a, b \in \mathbb{F}_q$, $a \neq 0$, has no solution in $\mathbb{F}_q$ if $tr(b/a^2) = 1$. It has two solutions in $\mathbb{F}_q$ if $tr(b/a^2) = 0$.

Proposition 17.21 is also known as the additive version of **Hilbert’s theorem 90.**

# Maximal arcs, Denniston arcs and Denniston codes

How many points can an arc of species $s$ in $PG(2,q)$ have? It was noted that this is a very basic and difficult problem in general. An upper bound is obtained by fixing a point $P$ of the arc and considering the distribution of the points on the $q + 1$ lines through $P$. Each of these lines contains at most $s - 1$ points $\neq P$ of the arc. It follows that the arc has at most $1 + (q + 1)(s - 1) = qs + s - q$ points. In the case of equality, each line of the plane either avoids the arc or intersects it in precisely $s$ points.

**17.22 Definition.** An arc $K \subseteq PG(2,q)$ of species $s$ with $qs + s - q$ points is a maximal $s$ arc.

Once again the terminology is unfortunate (it can happen that maximal $s$ arcs do not exist and that $s$ arcs of maximal cardinality are not maximal $s$ arcs). When do maximal $s$ arcs exist? There are some trivial cases: a point is a maximal 1 arc, all of $PG(2,q)$ is a maximal $(q + 1)$ arc, and each affine subplane (the points off a line) is a maximal $q$ arc.