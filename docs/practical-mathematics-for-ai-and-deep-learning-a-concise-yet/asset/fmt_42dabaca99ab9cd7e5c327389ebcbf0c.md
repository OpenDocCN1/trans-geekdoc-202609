
Here, if `x` is sufficiently close to `x=0`, even the Taylor series expansion truncated to 1 term approximates the sin function well. This is a linear approximation of sin function near `x=0` with the Taylor polynomial `TS 1(x) = x`, as shown in *[Figure 3.8](#c03.xhtml#fig3_8)*. As we include more terms, we see that the Taylor series polynomial coincides more with `sin(x)`, that is, we get an improved approximation. Refer to the following figure:

![](images/Figure-3.8.jpg)

**Figure 3.8:** *Function approximation locally (Taylor series)*

***Note: If we have a differentiable function f, calculating the first derivative of a function f’(a) at a point x = a, we can approximate the function close to "a" by a line y = f(a) + f'(a). This approximation is valid and very close to the point.***

***For example, if we take the function |x|. At any non-zero point, the function represents a straight line. However, at 0, where its not differentiable, we cannot approximate the function by a like however small interval around zero we take.***

So far, we have covered a few basic concepts for studying the functions of a single real variable. In ML, we will mostly encounter function of several variables. These concepts of real analysis can be extended to the functions of several variables. In fact, this way of approximating a differentiable function locally by a line will be useful in defining the derivative of functions of several variables. In the following sections, we will study functions of several variables.

# [Scalar and vector fields](#toc.xhtml#s108a)

In the previous chapter, we studied linear transformations ![](images/385.jpg), from one linear vector space `V` to another vector space `W`. Let both of these vector spaces be finite dimensional. Let the dimension of the domain space `V` is `dim(V) = n` and dimension of range space `W` be `dim(W) = m`. We call `T` a real valued function or a scalar field or a vector field based on `n` and `m`. Here, `T` need not be a linear function.

![](images/386.jpg)

*Scalar field* represents functions that maps a point in `n`\-dimensional space to a real number. For example, if at each point ![](images/387.jpg)of the atmosphere, we assign a real number `f(a)` representing the temperature at `a`, the function `f` is a scalar field. As we move from point ‘`a`’ to nearby point in space, the scalar field will vary. In ML, scalar fields arise while we train models. A model can be represented as a scalar field on the parameter space. It maps each possible parameter vector to total error value (a real number) w.r.t the given data points.

Let’s first see how points close to the vector `a` look like. In real line, points near number ‘`a`’ are points in the ∈ neighbourhood of `a` ![](images/388.jpg)More formally, a set of all real numbers `x` such that ![](images/389.jpg). For vectors, this generalizes to the concept of open ball: Set of all vectors `x` in `V` such that : ![](images/390.jpg)is called an *open ball around* `a`. The open ball around a represents points that are within a sphere of radius ∈. A two-dimensional open ball is shown by the shaded region in *[Figure 3.9](#c03.xhtml#fig3_9)*:

![](images/Figure-3.9.jpg)

**Figure 3.9:** *Open ball*

# [Limits and continuity](#toc.xhtml#s109a)

The concepts of limit and continuity can be easily extended to scalar and vector fields. Function ![](images/391.jpg)with domain ![](images/392.jpg). Let ![](images/393.jpg)and ![](images/394.jpg). Then, ![](images/395.jpg)means the limit:

![](images/396.jpg)

This is the usual limit for real valued function as ![](images/397.jpg)is a real valued function. Similarly, function `f` is said to be continuous at `a` if `f` is defined at `a` and ![](images/398.jpg). `f` is said to be continuous on the set `S` if its continuous at every point in `S`.

**Theorem**: For vector valued function, the function is continuous if each component is continuous. For example, ![](images/399.jpg). Each component is continuous, and hence, `f` is continuous.

So, we see that the definitions are straightforward extensions of those in the real valued functions in one-dimensional case. However, extending concept of derivative at a point for scalar fields requires some more work.

# [Derivative of scalar fields w.r.t. vector](#toc.xhtml#s110a)

Generally, the manner in which a field changes depends on the direction in which we move away from `a`. Let’s take the temperature scalar field example. Starting from `a`, the temperature increases moving towards the heat source, and it decreases as we move away from it. The rate of change or derivative of a scalar field is defined only in a fixed direction. Starting from the same point `a` and going in a different direction, there may be a different rate of change.

# [Directional derivative and partial derivatives](#toc.xhtml#s111a)

Let’s first choose a direction represented by a vector `u` and then compute rate of change in that direction. Let `u` be a unit vector. To compute rate of change in the direction of `u`, let’s choose an arbitrary point `x` close to `a`. Let `u` be a unit vector, that is, ‖`u`‖ = 1. For any real number `h`, the vector `a` + `hu` represents all points on the line parallel to vector `u`. If we choose `h` sufficiently small, then we can find a vector `y` = `a` + `hu` that is within the -ball around and lies on the line parallel to direction vector `u`, as shown in *[Figure 3.10](#c03.xhtml#fig3_10)*:

![](images/Figure-3.10.jpg)

**Figure 3.10:** *Directional derivatives*

Similar to the case of single variable, we can now write the derivative of a scalar field formally as:

![](images/400.jpg)

This is called the ***directional derivative*** of scalar field `f` at `a` in the direction of `u`. In particular, if `u` = `e[k]` (the `k^(th)` unit coordinate vector `e[k]` = (0, 0, …, 1, …, 0), with 1 at the `k^(th)` coordinate only), the directional derivative `f` '(a, `e[k]`) is called the ***partial derivative*** with respect to `e[k]` and is denoted by symbols as follows:

![](images/401.jpg)

Calculating partial derivatives is fairly simpler compared to arbitrary directional derivatives because only the rate of change along one of the coordinate axes is being measured. So, we can treat all other coordinate variables as fixed as we move parallel to only one axis. Hence, we can use all known formulas and rules for derivatives of single variable to compute partial derivatives.

**Example**: Let ![](images/402.jpg)

![](images/403.jpg)

Real valued function with one variable differentiability implies continuity at that point. For scalar fields, does the existence of all directional derivatives at a point imply continuity at that point? The following scalar field shows an exception:

![](images/404.jpg)

If we approach `(0,0)` along any line through origin other than `x` axis represented by a vector `u` *\= (a, b)` where ![](images/405.jpg).

![](images/406.jpg)

So, all the directional derivatives exist for `f`. Now, if we choose ![](images/407.jpg), we have ![](images/408.jpg)![](images/409.jpg). So, there are infinite points in the ∈ ball around `(0,0)` where `f` takes the value ½, but `f(0,0)` is `0`. Hence, `f` is not continuous at origin as close by points near origin are not mapped to close values. So*, even the existence of all the directional derivatives does not imply continuity of the scalar field at given point*. We need a better generalization of derivative for functions of several variables.

# [Total derivative](#toc.xhtml#s112a)

We have seen that for real valued function ![](images/410.jpg)we can approximate `f` locally at a point by a line using first order Taylor series expansion. This shows a way of extending the concept of differentiability to the higher-dimensional case using linear function.
