
## 14.1 Isometries, Unitary Operators and Positivity

Let `U` be an operator on a Hilbert space `H`, and assume it is an isometry. That is, for any `v` and `w` in `H`, it follows that `<U v, U w>` = `<v, w>`. Using the definition of adjoint, namely `<U v, U w>` = `<U* U v, w>` accordingly, `U*U` = `I`, and therefore, `U*U` acts like the identity in a `C*` algebra. Notice that this is a one-sided identity. Again, let `U` be an isometry in `C*` acting on the elements in the Hilbert space `H`, with `v` and `w` in `H`. It is always 1–1, that is, `U` is injective. This follows because `‖U v−U w‖` = `‖v−w‖`, so then `U v` = `U w` iff `v` = `w`. When `U` is also onto, that is, surjective, then it is invertible, and therefore, `U U*` also equals the identity `I`. In this case, now, `U` is a unitary operator, `U*U` = `U U*` = `I`. Accordingly, `U` is a normal operator also; in other words, `U` commutes with its adjoint, `U*`. Furthermore, for nonzero `v` in `H`, `‖U*U v‖` = `‖v‖` is greater than or equal to zero and so `U*U` is a positive operator. A positive operator has a spectrum always on the nonnegative part of the real line. A unitary operator always has its spectrum on the unit circle in `C`. Consequently, the spectrum of `U U*` is just the point one.

### Example 14.2

For `T`: `H`→`H`, where `H` is as usual a complex separable Hilbert space and `T` a positive operator, that is, `<v, T v>` is greater than or equal to zero for all `v` in `H`. It follows that `T` is also self-adjoint. Here, it must be shown that `T` = `T*`. Since `T` is positive, then this implies that `<v, T v>` is real valued, and so `<v, T v>` = `<v, T v>*` = `<T v, v>` = `<T* v, v>`. Now, let `S` = `T` − `T*`, as a consequence `<S v, v>` = `<(T − T*) v, v>` = 0, but this does not show `T` = `T*`, because the inner product in this expression involves a single vector `v`. To conclude the verification that `T` = `T*`, the polarization identity is needed, with `v` and `w`. Set `<S v, w>` = 1/4 { `<S(v+w), v+w>` − `<S(v−w), v−w>` + i `<S(v+ i w), v+ i w>` − i `<S(v− i w), v− i w>` } = 0. This holds for all `v` and `w` in `H`, thereby showing that `T` = `T*`.

### Example 14.3

As in the previous example, let `T` be a positive operator, that is, `<v, T v>` is greater than or equal to zero for all `v` in the Hilbert space `H`. This time, however, assume that `H` is a real Hilbert space, equal to `R²`. So the carrier set for the Hilbert space is now a real vector space. It follows that `T` is not symmetric. To see this, let `T` =

$\\begin{matrix} {|0} & {{- 1}|} \\\\ {|1} & {0|} \\\\ \\end{matrix}.$

![Equation](Images/F00028Xsi2.png)

Then, if for any vector `v` in `H` `v` = `(a b)'`, then `<v, T v>` = `<(a b)', (−b a)'>` = 0, but `T` does not equal `T*`.

### Example 14.4

The Cayley transform can be used in relating self-adjoint operators with unitary operators. In particular, for a self-adjoint operator `T` on Hilbert space `H`, the Cayley transform `(z−i)/(z+i)` is a special type of Möbius transform from complex variables. This operation maps the x-axis onto the unit circle. It is analytic except for a simple pole at −i. Specifically, use the Mobius transform as a one-parameter group: `f(z)` = `(z + i t)/(z − i t)`, where `t` is real. So, `[(T + i t)/(T − i t)]*` = `(T − i t)/(T + i t)` = `[(T + i t)/(T − i t)]^(−1)`, thus showing that `f(T)` is unitary.

Similar to the illustration in the previous example, [Section 14.5](#Ch014_255-270_B978044313697900028X.xhtml#s0030) is dedicated to relating self-adjoint operators with unitary operators. Indeed, here Stone’s theorem shows the relationship between single-parameter families of unitary operators and self-adjoint operators.

Also, the von Neumann algebra was described in [Chapter 9](#Ch009_165-169_B9780443136979000242.xhtml#Ch009_165-169_B9780443136979000242). However, it is interesting to relate isometries and unitarily transformations in this regard. Here, a von Neumann algebra `V`, which is a subset of `B(H)`, is finite-dimensional iff all isometries are unitary transformations ([Sakai, 1971](#Ch014_255-270_B978044313697900028X.xhtml#bib9)).

## 14.2 Canonical hypergroups—a multisorted algebra view

A hypergroup is a multivalued operation with a binary-type operation taking pairs of elements from a set `H` into a subset of `H`. So it maps a pair of points into a set. It is a set-valued function. From an MSA perspective of a canonical hypergroup, there exist two sorts, and they are `ELEMENTS` and `SUB`. The first sort denotes elements from a nonempty set `H`; this set need not be a Hilbert space. The second sort `SUB` indicates all nonempty subsets from `H`. As in a group, there exist three signature sets one of each arity 0, 1, and 2, containing a single operation name: `ZERO`, `MINUS`, and `ADD`. The second sort `SUB` is the nonempty power set for `H`. Since `SUB` does not contain the empty set, it is denoted by `2^(H')` ![Equation](Images/F00028Xsi3.png). The prime indicates that `2^(H')` = `2^(H)` − `ϕ` ![Equation](Images/F00028Xsi4.png). Therefore, replace the following operator names by corresponding symbols:

* `ZERO`, 0 is in `H`.
* `MINUS`: `H`→`H`.
* `ADD`: `H x H`→`2^(H')` ![Equation](Images/F00028Xsi5.png). So for `a` and `b` in `H`, `ADD(a,b)` = `S` where `{a+b}` is a subset of `S`.

A polyadic graph provides an illustration of these closure operations for a canonical hypergroup. See [Fig. 14.1](#Ch014_255-270_B978044313697900028X.xhtml#f0010). The arity sequence is again (1, 1, 1) as in a group. However, the equational identities make a world of difference from those of a conventional group.

![Figure 14.1 Canonical hypergroup polyadic graph.](Images/F00028Xf14-01-9780443136979.jpg)

[Figure 14.1](#Ch014_255-270_B978044313697900028X.xhtml#Bf0010) Canonical hypergroup polyadic graph.

The corresponding operators are extended to allow for set operations. So let `ZERO` be represented by 0, `MINUS` be symbolized by −, and for `ADD`, use +. Also let `A` and `B` be nonempty subsets of `H`; then `A+B` = `{a+b, for all a in A and b in B}`. Note the ordering; in general, the hypergroup may not be commutative. To emphasize this, let `x+A` = `{x+a, where a is in A}` and `A+x` = `{a+x, where a is in A}`, so `A+x` need not equal `x+A`.

For the equational identities to prevail, let `A`, `B`, `C`, and `X` be nonempty subsets of `H`, and let `x`, `y`, and `z` be elements in `H`, then:

1. 1) Associative: `A+(B+C)` = `(A+B)+C`. This should be understood that for all `a` in `A`, for all `b` in `B`, and finally for all `c` in `C`, the following holds: `a+(b+c)` = `(a+b)+c`.

2. 2) Zero property: `0+x` = `x+0` = `{x}`. The meaning of this is when the binary operator is applied with `x` and one of its arguments is zero, then the singleton-type subset occurs, that is, then `{x+0}` = `{x}`.

3. 3) Minus property: `x+(−x)` = `(−x)+x` = `X`, where 0 is an element of `X`. This shows that the subset `X` of `H` will contain the `ZERO` in `H` whenever either operand of `ADD` is the negative of the other operand.

4. 4) Cyclic property: For `x` in `{y+z}`, this implies that `z` is in `{x−y}`. Note that liberties are taken here by using minus as a binary operation. Indeed `{x−y}` = `{x+MINUS(y)}`.

If in addition the equational identity (5) holds, then the hypergroup is said to be abelian.

5. 5) Commutative: `A+B` = `B+A`. This should be understood that for all `a` in `A` and for all `b` in `B`, the following holds: `a+b` = `b+a`.

### Example 14.5

Consider the set `H` = `{0, 1, 2}` mod 3. Using the usual mod 3 additive structure for this carrier set, here, −2 = 1 in `H` and −1 = 2 in `H`. So, `2+1` = `{0}`. Furthermore, illustrating the cyclic property, 2 is in the set `{1+1}`; as a consequence, 1 is in the set `{2−1}`. This shows that hypergroup results from the module three addition operation using `H` and `2^(H)'` = `{{0}, {1}, {2}, {0, 1}, {0, 2}, {1, 2}, {0, 1, 2}}`.

The next example of a hypergroup is from [Linzi and Stojalowska (2020)](#Ch014_255-270_B978044313697900028X.xhtml#bib5).

### Example 14.6

Let `H` = `{0, −1, 1}`, and consider the addition given below; this defines what is called the sign hypergroup.

`(−1) + (−1)` = `(−1) + 0` = `0 + (−1)` = `{−1}`

![Equation](Images/F00028Xsi6.png)

`0 + 0` = `{0}`

![Equation](Images/F00028Xsi7.png)

`1 + 1` = `1 + 0` = `0 + 1` = `{1}`

![Equation](Images/F00028Xsi8.png)

`1 + (−1)` = `(−1) + 1` = `H`.

![Equation](Images/F00028Xsi9.png)
