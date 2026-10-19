For the distance between the origin 0 and a point z:

$d_h(0,z) = \operatorname{arccosh}\left(1 + \frac{2\|z\|^2}{1 - \|z\|^2}\right)$

Using the Euclidean norm for $z = x + yi$:

$\|z\| = \sqrt{x^2 + y^2}$

$d_h = \operatorname{arccosh}\left(1 + \frac{2(x^2 + y^2)}{1 - (x^2 + y^2)}\right)$

$\therefore d_h = \Phi(\|z\|) = \operatorname{arccosh}\left(1 + \frac{2\|z\|^2}{1 - \|z\|^2}\right)$

# 3.4. Mapping Function

Consider an arbitrary point $P$ in the Poincaré disk model $\mathbb{D}$. Let the coordinates of $P$ be $(x,y)$, where $x^2 + y^2 < 1$. We define a mapping $\Psi : \mathbb{D} \to \mathbb{M}$, such that a point $P$ in $\mathbb{D}$ is mapped to a point $P'$ in $\mathbb{M}$, the Mader model.

$\Psi(x,y) = (h(x), h(y)) \quad (7)$

$h(z) = \operatorname{arccosh}(\ln(1 + z)) \quad (8)$

For $z$ in $\mathbb{D}$, the function $h$ effectively translates each coordinate from $\mathbb{D}$ to a corresponding coordinate in $\mathbb{M}$.

# 3.5. Distance Function

Given two points, $P_1'$ and $P_2'$ in $\mathbb{M}$, which correspond to $P_1$ and $P_2$ in $\mathbb{D}$, the distance between $P_1'$ and $P_2'$ in the Mader model, $d_\mathbb{M}(P_1', P_2')$, is defined in terms of the distance between $P_1$ and $P_2$ in the Poincaré disk model, $d_\mathbb{D}(P_1, P_2)$, as follows:

$d_M(\Psi(x_1,y_1), \Psi(x_2,y_2)) = h(d_D((x_1,y_1),(x_2,y_2))) \quad (9)$

The transformation $\Psi$ offers a one-to-one mapping between the Poincaré disk $\mathbb{D}$ and Mader model $\mathbb{M}$ using the function $h$ defined in (7). By making use of the function $h$ and the transformation $\Psi$, this continuous mapping preserves the underlying geometric structures to compare the geometric properties between $\mathbb{D}$ and $\mathbb{M}$.

# 4. Series Expansions for Approximations

Understanding the behavior of the function $\lambda(r)$ and the hyperbolic distance $d_h$ under different geometrical transformations is critical. To address this, we employ Taylor series expansion to approximate these functions around the point $P$.

$f(x + y) = \ln\big[(x + y) + \sqrt{(x + y)^2 - 1}\big]$

The Taylor series expansion of a function $f$ about a point $P$ is represented as

$f(x + y) \approx f(P) + f'(P)(x + y - P) + \frac{f''(P)}{2!}(x + y - P)^2 + \frac{f'''(P)}{3!}(x + y - P)^3 + \cdots$

$f(P) = \ln\big[ P + \sqrt{P^2 - 1}\big] \quad (10)$