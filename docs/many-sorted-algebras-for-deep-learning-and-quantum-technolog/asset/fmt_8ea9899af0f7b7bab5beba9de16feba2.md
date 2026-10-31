
The general linear group `GL(2, R)` is a smooth manifold of four dimensions; it is a noncompact open subset of `R⁴`. As mentioned earlier, this Lie group is represented by 2 by 2 real-valued matrices with nonzero determinants. It is disconnected and has two connected components corresponding to the sign of the determinant. Those elements with positive determinants are called the positive component and include the `IDENTITY`. It too is a Lie group and is denoted by `GL+(2, R)`. Both `GL(2, R)` and `GL+(2, R)` have the same Lie algebra `m(2, R)`. The Lie bracket in `m(2, R)` is the algebra multiplication \[A, B\], which equals `AxB−BxA` that can equal zero, for instance, if `A=I`. Thus, the Lie algebra is not a division algebra. The maximal compact subgroup for `GL(2, R)` is `O(2, R)`, the orthogonal Lie group, which is described in detail in a subsequent section. For `GL+(2, R)`, the maximal compact subgroup is the special orthogonal group `SO(2)` ([Jacobson, 1979](#Ch011_191-216_B9780443136979000126.xhtml#bib11)). These subgroups will be addressed subsequently.

A topological space `T` is said to be simply connected when it is path connected, and every loop can be continuously contracted into a point in `T`. Rigorously, it is a homotopy between the two continuous functions `f` and `g`, describing the loop in `T`. Say that `f: [0, 1] → T`, `g: [0, 1] → T`, `f(0)=g(0)`, `f(1)=g(1)`. Then, these two paths define a loop. The properties of loops will be more thoroughly explained in Chapter 12, where homotopy is the principal concept.

Lie’s third theorem states every finite-dimensional real Lie algebra is the Lie algebra of a simply connected Lie group. In essence, simple connectivity will be the criteria for establishing a 1–1 correspondence between Lie groups and Lie algebra in the real case. Finally, a Lie group is said to be simple when it is connected, not Abelian, and all closed-connected subgroups are trivial, that is, they equal the identity or the whole space.

The next figure, [Fig. 11.3](#Ch011_191-216_B9780443136979000126.xhtml#f0020), illustrates two continuous paths. This shows path connectivity, but simple connectivity is problematic from an analytical or practical point of view. Here, let `f(t)=t sin(π /(2t))` for `t` in `(0, 1]`, and `f(0)=0`. Then, `f` is continuous in the interval `[0, 1]`, since it satisfies the condition at the origin that `|f(t)|` is less than or equal to `|t|`. A Lipchitz condition therefore holds for `f` at the origin. Also, let `g(t)=2t – t²`. Since `f(0)=g(0)` and `g(1)=f(1)`, together they form a loop. However, shrinking this loop to a point, say zero would take a lot of doing because the function `f` is not of bounded variation. The total variation in `[0, 1]` equals summation, $\\sum\_{n = 0}^{\\infty}{\\left( {1/\\left( {2n + 1} \\right)} \\right) = \\infty}$![Equation](Images/F000126si8.png). Thus, the curve corresponding to this function is not rectifiable and intuitively it is of infinite arc length.

![Figure 11.3 Path connectivity.](Images/F000126f11-03-9780443136979.jpg)

[Figure 11.3](#Ch011_191-216_B9780443136979000126.xhtml#Bf0020) Path connectivity.

### Example 11.9

The special Lie group `SL(2, R)` is a subgroup of `GL(2, R)`. This subgroup `SL(2, R)` consists of all 2 by 2 matrices with determinant equal to one. It is connected, not compact, and a simple group. `SL(2, R)` is not simply connected; however, `SL(2, C)`, the complex special group, will be seen to be simply connected subsequently. The dimension of `SL(2, R)` is three because of the constraint on the determinant. Polar form parametrization, among other parametrizations, can be employed on elements of this group. Indeed, elements of `SL(2, R)` can be written as the product of an orthogonal rotation matrix and a symmetric matrix with positive eigenvalues and unit determinant. The corresponding Lie algebra `sl(2, R)` consists of all 2 by 2 matrices `A`, and `B` over the reals with trace zero. The binary operation as usual is the Lie bracket commutator. So, \[A, B\]=`AxB−BxA`.

Among the many applications involving elements from `SL(2, R)` is the classification of conic sections utilizing a modified eccentricity parameter `e`, see (SL[2](R), Wikipedia). This involves the Cayley-Hamilton equation. Every matrix satisfies its characteristic equation. Thus, for `A` in `SL(2, R)`, the characteristic equation for `A` is `x²−tr(A) x + det(A)=0`, and since `det(A)=1`, the characteristic equation becomes `x² −tr(A) x + 1=0`. The quadratic formula provides the solution `x`, for the characteristic equation:

*x* = (*t**r*(*A*)+−(*t**r*(*A*)²−4)^(1/2))/2.*L**e**t**t**i**n**g**e* = |*t**r*(*A*)|/2*t**h**e**n*:

![Equation](Images/F000126si9.png)

*   For `e <1`, `A` is elliptic with complex, unit, and conjugate eigenvalues, used for rotation.

*   For `e=1`, `A` is parabolic with single eigenvalue +1 and −1, used as a shear operation.

*   For `e> 1` `A` is hyperbolic with real reciprocal eigenvalues, used as a squeeze operation.

Operators of the hyperbolic case mentioned in the previous example are also from the projective linear Lie group `PSL(2, R)`. They are used as the Lorenz boost in Minkowski space. The hyperbolic functions `sinh` and `cosh` are employed in this case, providing a symmetric hyperbolic space. The latter property means that `cosh²–sinh²=1` ([Bargmann, 1947](#Ch011_191-216_B9780443136979000126.xhtml#bib1)).

### Example 11.10

Again consider `SL(2, R)`. In [Example 11.9](#Ch011_191-216_B9780443136979000126.xhtml#enun0050), it was mentioned in not so many words that the manifold associated with this group is parametrized by the product manifold `R²` and the circle group `S¹`. Also mentioned is that there are other parameterizations. For instance, every point `(a, b, c)` in this group belongs to `R³` and a parameterization for the case where `a` is nonzero, which can also be given by the matrix:

$\\begin{matrix} {|a} & {\\qquad{b\\mspace{31mu}|}} \\\\ {|c} & {{\\left( {1 + {bc}} \\right)/a}|} \\\\ \\end{matrix}$

![Equation](Images/F000126si10.png)

The point `a` is a singular point. However, when the scalar `a` is nonzero, the determinant of this matrix is one. Singular points are abundant in Lie groups and are problematic. In any case at these singular points, alternative parametrization is required and can often be provided.

It seems at this point in the document all Lie groups that have been described are matrix Lie groups. An example of a nonmatrix Lie group is given next ([Hall, 2013](#Ch011_191-216_B9780443136979000126.xhtml#bib7)).

### Example 11.11

Again consider a dimension three Lie group, similar in dimension and construction to `SL(2, R)`. This time, every point `(a, b, c)` in this group belongs to the carrier set: `R²×S¹`, where `S¹` is the circle group. So the third tuple is complex valued and of length one in this case. Thus `c` is nonzero. The real dimension in this example is four. A parameterization is given involving the addition of points in the plane `R²` and rotations using elements of the circle group `S¹`. Specifically, for two elements `v=(a, b, c)` and `w=(d, g, f)` in this manifold, then

$\\begin{array}{l} {{MULT}\\left( {v,w} \\right) = \\left( {a + d,b + g,c f\\exp^{iag}} \\right)} \\\\ {{INV}\\left( v \\right) = \\left( {- a, - b,{1/c}} \\right),{note}{that}{MULT}\\left( {v,{INV}\\left( v \\right)} \\right) = \\left( {0,0,{c/c}} \\right) = {IDENTITY}} \\\\ {{IDENTITY} = \\left( {0,0,1} \\right)} \\\\ \\end{array}$

![Equation](Images/F000126si11.png)

It can be shown ([Hall, 2013](#Ch011_191-216_B9780443136979000126.xhtml#bib7)) that there is no matrix Lie group corresponding to this abstract Lie group.

## 11.7 Formal description of matrix Lie groups
