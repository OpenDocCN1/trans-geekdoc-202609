plete the transformation from image to membership matrix, and enhance the transformation of edge information. This greatly reduces the amount of computation and dynamically adjusts the threshold to accommodate different types of images and user requirements.

# Algorithm 14.4:

+   (1) Initialisation of threshold α

+   (2) Adjustment α

+   (3) Introduction of the qualification function, such as Zadeh’s S function, owing to further normalisation and enhancement of the original image. The anti-fuzzy transformation formula $x'_{m,n} = \mu_{m,n}(r-p)$ can be used to obtain the enhanced image. Extract the edge with ‘Min’ or ‘Max’.

# 14.2 Edge division method based on homological algebra

This section applies homology theory to the study of partitioning problems.

# 14.2.1 Basic concepts of homological algebra

The basic concepts that are drawn later are described below [6–10]:

```
$x^{0},x^{1},x^{2},\dots,x^{\mathrm{q}}\quad 0\leq q \leq n$
$x^{1}-x^{0},x^{2}-x^{0},\dots,x^{\mathrm{q}}-x^{0}$
$x = \lambda_{0}a_{0}+\lambda_{1}a_{1}+\cdots+\lambda_{q}a_{q}$
$\lambda_{0}+\lambda_{1}+\dots,\lambda_{q}=1$
$gi_{i}s_{i}^{q}=(-gi_{i})(-s_{i}^{q})$
$x_{q}=g_{1}s_{1}^{q}+g_{2}s_{2}^{q}+\dots,g_{a_{q}}s_{a_{q}}^{q}$
$y_{q}=h_{1}s_{1}^{q}+h_{2}s_{2}^{q}+\dots,h_{a_{q}}s_{a_{q}}^{q}$
$x_{q}+y_{q}=(g_{1}+h_{1})s_{1}^{q}+(g_{2}+h_{2})s_{2}^{q}+\dots(g_{a_{q}}+h_{a_{q}})s_{a_{q}}^{q}$
```

**Definition 14.1**. (14.1) is a point in Euclidean space $E^{n}$. When $q = 0$, (14.1) has only one point, so it occupies the widest position. When $q > 0$, (14.2) is linearly independent; in (14.1), this set of points occupies the widest position.

A group of points is selected in Euclidean space to occupy the widest position, such as $a_{0}$, $a_{1}$, \dots, $a_{q}$ and $q \leq$ n. If (14.3) is established, the real numbers $\lambda_{0}$, $\lambda_{1}$, \dots, $\lambda_{q}$ satisfy the following conditions (see (14.4)) and satisfy $\lambda_{0} \geq 0$, $\lambda_{1} \geq 0$, $\lambda_{q} \geq 0$. The set $X$ of such points in $E^{n}$ is called a $q$ dimension simplex, denoted by $(a_{0}$, $a_{1}$, \dots, $a_{q})$ or $s^{q}$. We call $a_{0}$, $a_{1}$, \dots, $a_{q}$ the vertexes of $s^{q}$.