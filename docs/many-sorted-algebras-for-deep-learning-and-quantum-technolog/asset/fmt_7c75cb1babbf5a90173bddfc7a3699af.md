
* [Humphreys, 1997](#Ch012_217-230_B9780443136979000254.xhtml#BIB_5) Humphreys J. 978–3540900535 *Introduction to Lie Algebras and Representation Theory*. vol 9 2nd ed. Springer 1997;.
* [Strom, 2011](#Ch012_217-230_B9780443136979000254.xhtml#BIB_6) Strom, J., 2011. Modern Classical Homotopy Theory, vol 127. American Mathematical Society.
* [Whitehead, 1978](#Ch012_217-230_B9780443136979000254.xhtml#BIB_7) Whitehead. GTM *Elements of Homotopy Theory*. Vol. 61 Springer-Verlag 1978;.

# Chapter 3

## Basic algebras underlying quantum and NN mechanisms

### Abstract
This chapter begins with a description of how a vector space becomes an algebra. Several distinct algebras are described using the MSA methodology. Examples are provided of unital algebras as well as associative as well as nonassociative algebras. Both in quantum technology and deep learning disciplines, the underlying algebraic structure is more than just a vector space or a field. It is very often an algebra. In particular, the algebra of time-limited signals is introduced. Numerous examples are provided along with bound vector representations. This is followed by the commutant in algebra, and again examples are provided. The Hilbert space of wraparound digital signals is described and illustrated in Section 3.4. This section is followed by MSA for Banach space, Banach algebras, as well as `C*` algebras. All these algebras are presented with examples.

#### Keywords
Unital algebra; commutant; normed vector space; Banach space; Banach algebra; adjoint operation; `C*` algebra; wraparound signals

### 3.1 From a vector space to an algebra
Referring to the arbitrary vector and Hilbert space representations in the MSA will allow generalizations of these structures to be described in a high or global view. To begin, a vector space equipped with a bilinear operation is called an algebra, when several equational identities hold ([Gratzer, 1969](#Ch003_41-55_B9780443136979000175.xhtml#bib3)). The bilinear operation is usually defined by multiplying two vectors resulting in another vector. This multiplication can take numerous forms depending on the carrier set corresponding to the sort of objects being manipulated. The carrier set could result in signature sets involving the point-wise type of multiplication as in function spaces. It could be a composition of operators, that is, functions of functions. It can be the concatenation of equivalence sets consisting of paths as in homotopy. Additionally, it can be convolution or group multiplication as it is often called. The last type of multiplication is the principal operation employed in convolutional neural networks (CNNs). Independent of the type of multiplication, the MSA global view embellishes all of these representations.

More precisely, the sorts for describing an algebra consist of `VECTOR` and `SCALAR`, as in the vector space structure. All the corresponding signature sets for vector space and field structures must hold in this case. However, an additional operator name is included. It is a binary operational name and exclusively involves sort `VECTOR`. The element is named `BINE`, indicating it is a binary operation and it is such that.

`BINE` maps `VECTOR` x `VECTOR`→`VECTOR`; as usual, the order of the operands being multiplied together does not matter. Both operands could be on the left or right when multiplied together.

When `BINE` is included within signature sets among those of a vector space structure, an arity sequence of (1, 1, 3 (2, 1)) results for an algebra. Here, again there are three binary operations, inner product excluded. Two of the three operations belong to the same signature set having names of arity two; they are `V-ADD` and `BINE`. The other binary operation name is in a signature set of its own; it is `S-MULT`. There is a single unary operator name, `V-MINUS`, and a single zero-ary name, `V-ZERO`.

In an algebra, three additional constraining equations must hold, excluding those for a vector space and a field structure. These constraints are given below. In order to describe these constraints in a more succinct manner, denote:
* `SCALAR` by: `a`, `b`
* `VECTOR` by: `u`, `v`, `w`
* `V-ADD` by `+`
* `S-MULT` by `×`
* `BINE` by `·`

These equational identities for an algebra are as follows:
1. Distributive law: `(u + v)·w = u·w + v·w`.
2. Distributive law: `w·(u + v) = w·u + w·v`.
3. Multiplicative homogeneity: `a b × (u·v) = (a × u)·(b × v)`.
An algebra is said to be associative when the additional constraint (4) holds:
4. Associative law: `((u·v)·w) = (u·(v·w))`.
Additionally, an algebra is said to be unital whenever, along with `V-ZERO`, there exists `V-ONE`, both belonging to the zero-ary signature set for `VECTOR`. Moreover, these elements must be distinct from each other, as indicated by the separate arrows in the polyadic graph ([Fig. 3.1](#Ch003_41-55_B9780443136979000175.xhtml#f0010)). As a consequence, an arity sequence of (2, 1, 3 (2, 1)) exists for a unital algebra. Here, equational identities (1), (2), (3), and (5), given below, must hold true. Again for convenience, replace `V-ONE` with `I`,
5. `V-ONE` law: `I·v = v·I = v`.
An associative algebra with a unital element is a unital associative algebra satisfying all identities mentioned earlier. Moreover, when (6) holds, the algebra is also said to be commutative or abelian.
6. Commutative law: `v·w = w·v`.

![Figure 3.1 Polyadic graph of a unital algebra.](Images/F000175f03-01-9780443136979.jpg)

Figure 3.1 Polyadic graph of a unital algebra.

When all equational identities hold, a unital algebra is called an associative, commutative unital algebra. A unital associative algebra in which all nonzero elements are invertible is called a division algebra. Again, the polyadic graph of a unital algebra is provided in [Fig. 3.1](#Ch003_41-55_B9780443136979000175.xhtml#f0010). In this diagram, none of the many-sorted polyadic arrows solely involving `SCALAR` are displayed. Also, as in a vector space or an R-module, the only link or connection between a `VECTOR` and `SCALAR` is through `S-MULT`. Moreover, the `S-MULT` operation should use a scalar and a vector in either order. Accordingly, the operation is somewhat commutative, and the result must be the same.

#### Example 3.1
Let the carrier set for sort `VECTOR` be the set of all complex-valued entire functions. Among the many equivalent characterizations of entire functions is that they have a power series representation with an infinite radius of convergence. Using the usual point-wise complex addition and multiplication provides an example of a unital commutative associative algebra. This algebra is important for the development of the holomorphic functional calculus, which is useful in spectral theory mentioned in later sections.

Entire functions are analytic everywhere and so are the sums and products. In general, their reciprocals are entire for nonzero scalars. The unital element, `V-ONE`, is the number 1. Included in this algebra are all polynomials, `sin(z)`, `cos(z)`, and hyperbolic sine and cosine, along with their sums and products. Not included, for instance, are rational functions having poles in `C`, `z^(1/2)` having a branch point at the origin in `C`, `exp(1/z)` having an essential singularity in `C`, and finally any function employing the conjugate `z*`. However, functions with only removable singularities are in this unital commutative algebra. For instance, `sin(z)/z` has the singularity at 0, which can be removed.

#### Example 3.2
