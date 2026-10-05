6.11. SUPPORT VECTOR MACHINES 105

![](bbox=[0.303, 0.093, 0.696, 0.283])

Proof: consider any two points on $H$, $x_0$ and $x_1$. We will show that $(x_1 - x_0) \perp ((x_1 + w) - x_1).
Note that

```
$$(x_1 - x_0)^T((x_1 + w) - x_1) = (x_1 - x_0)^T w = x_1^T w - x_0^T w = b - b = 0$$
```

Since $w$ is perpendicular to $H$, the (shortest) distance from any arbitrary point $z$ to the hyperplane $H$ is determined by a scaled multiple of $w$. If we take any point on the hyperplane $x_0$, the distance from $z$ to $H$ is the length of the projection from $z - x_0$ to the vector $w$, which is

```
$$$D = \frac{|w^T(z - x_0)||}{\|w\|_2} = \frac{|w^T z - b|}{\|}{\|w\|_2}$$
```

![](bbox=[0.383, 0.522, 0.617, 0.672])

Therefore, the distance from any of the training points $x_i$ to $H$ is

```
$$$\frac{|w^T x_i - b|}{\|}{\w\|_2}$$
```

In order to ensure that positive points are on the positive side of the hyperplane outside a margin of size $m$, and that negative points are on the negative side of the hyperplane outside a margin of size $m$, we can express the constraint

```
$$$y_i \frac{|w^T x_i - b|}{\|}{\w\|_2} \geq m$$
```