# 1.2 Preordered Linear Spaces and Convex Cones

Fig. 1.6 Illustration of the basic version of the Hahn-Banach theorem (see [72, Fig. C.1])

![](bbox=[0.623, 0.086, 0.878, 0.215])

$\ell$ on $Y$

$\ell(y) \leq f(y)$ for all $y \in Y$

(see Fig. 1.6).

# 1.2 Preordered Linear Spaces and Convex Cones

We start with the definition of a preorder in a real linear space.

Definition 1.8 Let $Y$ be a real linear space.

+   (a) Every nonempty subset $R$ of the product space $Y \times Y$ is called a binary relation on $Y$ (one writes $xRy$ for $(x, y) \in R$).
(b) Every binary relation $\leq$ on $Y$ is called a preorder on $Y$ iff for arbitrary $w, x, y, z \in Y$:
(i) $y \leq y$ (reflexivity),
(ii) $x \leq y, y \leq z \Rightarrow x \leq z$ (transitivity),
(iii) $x \leq y, w \leq z \Rightarrow x + w \leq y + z$ (compatibility with the addition),
(iv) $x \leq y, \alpha \in \mathbb{R}_+ \Rightarrow \alpha x \leq \alpha y$ (compatib. with the scalar multiplication).

+   (c) A preorder $\leq$ on $Y$ is called antisymmetric iff for arbitrary $x, y \in Y$

```
$x \leq y, y \leq x \Rightarrow x = y.$
```

An antisymmetric preorder is said to be a *partial order*.

+   (d) A real linear space equipped with a preorder is called a *preordered linear space*, and a real linear space equipped with a partial order is called a *partially ordered linear space.*