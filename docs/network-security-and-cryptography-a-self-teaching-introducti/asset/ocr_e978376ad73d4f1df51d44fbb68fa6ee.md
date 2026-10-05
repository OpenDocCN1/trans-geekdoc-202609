$F_y(y) = P[Y \le y] = P[g(X) \le y] = P[X \le g^{-1}(y)] = F_x(g^{-1}(y))$

Hence,

$f_y(y) = \frac{d}{dy}F_x(g^{-1}(y)) = \frac{d}{dx}F_x(g^{-1}(y))\frac{dx}{dy}$

or

$f_y(y) = \frac{f_x(x)}{dy} \quad (2.70)$

where $x = g^{-1}(y)$. In case $Y = g(X)$ has a finite number of roots $X_1, X_2, \dots, X_n$ such that

$Y = g(X_1) = g(X_2) = \dots = g(X_n)$

then the PDF of $Y$ becomes

$f_y(y) = \frac{f_x(x_1)}{dx_1} + \frac{f_x(x_2)}{dx_2} + \dots + \frac{f_x(x_n)}{dx_n} \quad (2.71)$

Once the PDF of $Y$ is determined, we can find its mean and variance using the regular approach.

# 2.7 GENERATING FUNCTIONS

It is sometimes more convenient to work with generating functions. A probability generating function, often called the $z$-transform, is a tool for manipulating infinite series. Generating functions are important for at least two reasons. First, they may have a closed form. Second, they may be used to generate probability distribution and the moments of the distributions.

If $p_0, p_1, p_2, \dots$ form a probability distribution, the probability generating function is

$G(z) = E[z^I] = \sum_{i=0}^{\infty} z^i p_i \quad (2.72)$