# 2.1 Bishop-Phelps, Penalty, and Scalarizing Functionals

![](bbox=[0.219, 0.093, 0.775, 0.269])

**Fig. 2.3** Illustration of the distance functional value at some $y \in Y$ (see [72], Fig. 2.10)

**Proposition 2.1** (See [144, Proposition 3.2, (4)]) Let $C$ be a closed preordered cone in a reflexive real Banach space $(Y, ||\cdot||)$ with $C \neq Y$. *Then we have*

```
$-C = \{y \in Y \mid \Delta_{-C}(y) \leq 0\}$
```

**Proof**

(a) Let $y \in -C$ be arbitrarily chosen. Then we have

> $$\Delta_{-C}(y) = d_{-C}(y) - d_{Y\setminus(-C)}(y) \leq 0.\n=0$

(b) For an arbitrarily chosen $y \notin -C$, it follows

> $$\Delta_{-C}(y) = d_{-C}(y) - d_{Y\setminus(-C)}(y) = d_{-C}(y).\\n=0$

For the closed convex cone $-C$, there is some $\tilde{y} \in -C$ so that

> $$\d_{-C}(y) = ||\tilde{y} - y|| > 0.\n\neq 0y$

(compare [72, Thm. 2.18], which follows from Theorem 1.2). Hence, we conclude $\Delta_{-C}(y) > 0$.



Under appropriate assumptions, Proposition 2.1 states that the negative convex cone equals the sublevel set of the signed distance functional $\Delta_{-C}$ with respect to the level 0.