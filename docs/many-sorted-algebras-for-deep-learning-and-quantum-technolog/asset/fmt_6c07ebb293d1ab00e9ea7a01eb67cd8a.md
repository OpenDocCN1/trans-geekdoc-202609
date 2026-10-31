
Note that `MINUS(1)=−1`, `MINUS(−1)=1`, and `MINUS(0)=0`. Also, 2) holds because `ZERO` added to anything is anything. Additionally, 3) holds because say `1+(−1)={0, −1, 1}`, and `0` is in this set. Unlike a regular group, the `ZERO` element must be in a set where `1+(−1)` is located, but it need not be `{0}`. Finally, note that 4) holds; for instance, `x=1` is in the set `{1+1}`, referring to 4), `y=1` and `z=1`; therefore, `z` is in `{x−y}`=`{1−MINUS(1)}`=`{1+1}`=`{1}`.

## 14.3 Partial isometries
A partial isometry `U` for a bounded operator on `H` is where `U` is an isometry when `U` is restricted to `perp(ker(U))`. That is, `U`: `perp(ker(U))`→ range of `U`. To obtain some intuition about a partial isometry operator `U`, it is best to see that it is a mapping from a closed subspace, `A` in `H` onto another closed subspace `B` of `H`. Often, in this case, `A` is referred to as the initial space, and `B` is called the final space. `A` is found by taking the orthogonal complement to the kernel, and `B` is found by taking the range. See [Fig. 14.2](#Ch014_255-270_B978044313697900028X.xhtml#f0015). Simultaneously, the adjoint `U*` performs the opposite mapping. It maps subspace `B` onto subspace `A`. Additionally, it is useful to think that in the complement of domains `A` and `B`, the values are all equal to zero. `U*U` is a projection on subspace `A`, also called the initial projection, while `UU*` is a projection on subspace `B` and it is called the range projection. These mappings are used to indicate if there exist self-adjoint extensions for symmetric operators. Additionally, if there are extensions, these mappings are useful in determining these extensions.

![Figure 14.2 Partial isometry mappings.](Images/F00028Xf14-02-9780443136979.jpg)

[Figure 14.2](#Ch014_255-270_B978044313697900028X.xhtml#Bf0015) Partial isometry mappings.

### Example 14.7
Let `L` be the left shift operator in *l*^(*p*)![Equation](Images/F00028Xsi10.png), where `L(v1, v2,…)=(v2, v3,…)`, then `L` is a partial isometry. Since `ker(L)={(v1, 0, 0, 0,…)}`, it consists of all those vectors in *l*^(*p*)![Equation](Images/F00028Xsi11.png) which map to zero. `Perp(ker(L))={(v2, v3,…)}=ran(L)`.

### Example 14.8
Let the carrier set for the sort `VECTOR` be the two-dimensional complex-valued field. So, here in Hilbert space `H`= `C`²![Equation](Images/F00028Xsi12.png), consider the partial isometry `Ua`=

```
\begin{matrix} {|0} & {1|} \\\\ {|0} & {0|} \\\\ \\end{matrix}
```

![Equation](Images/F00028Xsi13.png)

Then, the initial space for `Ua` is `A`=direct sum of `C` and `{0}`. This follows because the `ker(Ua)`=the set of all column vectors `(z 0)′`, where `z` is any complex number. Multiplying `Ua` times this vector gives zero. So the initial space consists of all two-by-one column vectors with first tuple in `C` and the second tuple zero. `Perp(ker(Ua))`=the set of all vectors of the form `(0 w)′`, where `w` is any complex number. This is also the range of `Ua`. The final space `B` is the direct sum of `{0}` and `C`.

Refer to the partial isometries from subspaces `A` to `B` in `H`. Denote `Ua` to be the partial isometry from `A` to `B`. The deficiency indices of `Ua` are given by the dimensions of `perp(A)` and `perp(B)`, respectively. Only when these indices are equal can `Ua` be extended to a unitary operator on all `H`. First, when these indices are equal, it will be shown that `U` is the extension to all of `H`. `U` will equal the direct sum of `Ua` and `Up` where `Up` is the unitary operator from `perp(A)` to `perp(B)`. This operator maps `H` into itself using the domain equaling the direct sum of `A` with `perp(A)` and range being the direct sum of `B` with `perp(B)`. Since two Hilbert spaces are isomorphic when and only when they have the same dimension, this shows that `U` is an extension. On the other hand, if `U` extends `Ua`, then `U(perp(A))=perp(U(A))=perp(Ua(A))=perp(B)`; since `U` is unitary, `dim(perp(A))=dim(perp(B))` and the indices are equal.

The Cayley transform mentioned in [Example 14.4](#Ch014_255-270_B978044313697900028X.xhtml#enun4) provides a partial isometry between `ran(T+iI)` and `ran(T−iI)` in `H` when `T` is a closed and symmetric operator. Moreover, under these conditions, the transform is unitary on `H` if and only if `T` is self-adjoint. A theorem of von Neumann states that for `T` closed and symmetric, `T` has a self-adjoint extension if and only if the deficiency indices of its Cayley transform are equal. Additionally, `T` has a self-adjoint extension if and only if `ker(T*−iI)` and `ker(T*+iI)`, or `ran(T+iI)` and `ran(T−iI)`, have the same dimension ([Conway, 1999](#Ch014_255-270_B978044313697900028X.xhtml#bib1)).

There are strong relations between partial isometries and projections in Hilbert space. A bounded operator `U` is said to be a partial isometry whenever `UU*` is a bounded projection. Additionally, it is called a partial isometry whenever `U=UU*U` or whenever `U*` is a partial isometry and all are in `B(H)`. The first identity mentioned earlier is related to the pseudoinverse operation. These relations are verified below in the next section. Additionally, the pseudoinverse operation is illustrated in Section 18.4 in a machine learning environment, namely a regression application. Previously mentioned, but not in the same manner, using function composition, if `Ua`: `A→B`, then `Ua*`: `B→A` and then `Ua*Ua=I` on `A`, that is, it is the identity operator on the Hilbert space `A`. Similarly, `UaUa*=I` on `B`, the identity operator on `B`. Partial isometries are intrinsically related to generating a von Neumann algebra as well as showing the unitary equivalence of bounded operators in a Hilbert space ([Pearcy, 1964](#Ch014_255-270_B978044313697900028X.xhtml#bib7)).

## 14.4 Multisorted algebra for partial isometries
Partial isometries of `B(H)` operators in a `C*` algebra as mentioned earlier are described in several equivalent ways:

1. 1) Idempotent: if `v=UU*`, then `v²=v`![Equation](Images/F00028Xsi14.png).
2. 2) Pseudoinverse: `UU*U=U`.
3. 3) Pseudoinverse: `U*UU*=U*`.
4. 4) Idempotent: if `w=U*U`, then `w²=w`![Equation](Images/F00028Xsi15.png).

To show (1)→(2), set `u=U−UU*U` and then evaluate `uu*=(U−UU*U)(U*−U*UU*)`=`UU*−UU*UU*−UU*UU*+UU*UU*UU*`=`v−v²−v²+v³`=0. Because `v³=v²v=v²`, and `uu*=‖u‖²`. Next, to show (2)→(3), take adjoint. To show (3)→(4) since `U*UU*=U*` and `w=U*U`, multiplying the equation `U*UU*=U*` on the right by `U` shows `w²=w`![Equation](Images/F00028Xsi16.png). Lastly, to show (4)→(1), set `u=U*−U*UU*`; next multiplying by `U` on the left gives `v²=v`![Equation](Images/F00028Xsi17.png). It will be seen next that in the `MSA`, the high view for partial isometries is that of an idempotent semigroup.

Several times in this document, it was seen that not all operators were defined fully on their domain. For instance, special attention and notation was given for the inverse operation in a field, and the same is true for both the momentum and the distance operators on a Hilbert space. Including the inversion of the zero element in a field would have enlarged the domain to include the point at infinity. This results in a pointed set, and a new algebraic structure arises, but it is not a field. Under function composition, often a partial isometry `U` cannot be followed by itself. That is, `U²`![Equation](Images/F00028Xsi18.png) is not defined unless `U*U=UU*`, and the same is true for `U*` ([Paterson, 1999](#Ch014_255-270_B978044313697900028X.xhtml#bib6)). As a consequence, the binary operation of multiplication, actually function composition, is modified in the `MSA` to accommodate these types of partial isometries. Additionally, as in previous structures, there is an order in which these operators can perform. The arguments do not necessarily commute. For these situations, as previously mentioned, the polyadic graph has slashes indicating the order of argument utilization from designated sorts. The same is true in this application along with an additional restriction, described later; also see [Fig. 14.3](#Ch014_255-270_B978044313697900028X.xhtml#f0020).
