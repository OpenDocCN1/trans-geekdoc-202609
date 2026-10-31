
In the previous chapter, digital signals and wraparound digital signals were presented as inner product space and Hilbert space, respectively. The basic axioms of quantum are vague in defining the type of underlying Hilbert space. Again at a lower level, a precise specification relative to the global Hilbert space structure shall be made. Here, the actual elements are provided; specifically, carrier sets for the two sorts, one corresponding to `SCALAR` and the other for `VECTOR`, are given. The actual operations themselves will be specified matching the names of operations within the signature sets.

## 4.1

### Example 4.1

This is perhaps the simplest example of a Hilbert space. Here, the reals form a vector space, `V`, over the real number field, `R`. This fact was previously mentioned in Example 2.13, illustrating the effect of a vector on an element in affine space. The carrier set for `SCALAR` and the carrier set for `VECTOR` both consist of elements from the real line. The real numbers play a dual role with the usual operations and functions involving real numbers. All the axioms are upheld for an inner product space, as well as for a Hilbert space. The space is only a single dimension. Note that `IN-PROD` results in just the product of any two vectors, which in this case are two scalars. The Hilbert space equational constraint (9) holds. See Section 1.8:

1. 9) Positive definite: `v·v` is greater or equal to 0, and =0 iff `v=0`.

Another concrete example is provided next.

### Example 4.2

This example is very similar to the previous example. Indeed, the complex number system forms a vector space over the complex field `C`. It follows that both sorts are complex in this case. Again both carrier sets are the same; this time, they are the complex numbers. Also, see Example 1.7. This structure also forms a very important Hilbert space for Fock space. It describes the vacuum space. Fock space will be presented in the many-sorted algebra (`MSA`) description in a later chapter. Again, notice that `IN-PROD` of `v` with `w` results in the usual complex product involving the conjugate of the first entry inner product with the second: `<v|w> = v*·w`. All the constraining equations for inner product space hold; for instance, number (9) again refers to Section 1.8:

1. 9) Positive definite: `v*·v` is greater or equal to 0 and =0 iff `v=0`.

Also notice that the norm squared of `v = (a + i b)` is again given by just the product: `v*·v = (a − i b)(a + i b) = a² + b² = ‖v‖²`.

## 4.2 Complexification

The next method of creating a Hilbert space involves complexification of a Hilbert space, ([Halmos, 1958](#Ch004_57-81_B9780443136979000011.xhtml#bib3)). For a Hilbert space, `Hr` over the real number field, the procedure results in the complex Hilbert space denoted by `Hc`. It is of the same dimension as `Hr`, but it is over the complex number field. In this case, the real scalar multiplication of a vector is extended to the complex scalar multiplication. Among the many procedures for performing complexification, the tensor product method is utilized. The method is described next. Later sections will utilize the complexification of tangent spaces to a fiber when considering quantization on manifolds.

In the `MSA` global view, sorts similar to those already mentioned for the Hilbert space structure and field structure must be given. These sorts are suggestively defined by `C-SCALAR`, `R-VECTOR`, and `C-VECTOR`. The complex field is denoted by `C-SCALAR`. The real scalar field exists in complexification, but is not mentionded again. The Hilbert space over the reals is given by `R-VECTOR`. Similarly, the resulting complex-valued Hilbert space is `C-VECTOR`. Exactly, the same types of signature sets and corresponding operational names are employed for both Hilbert space specifications; again refer to Section 1.8. However, for complexification, there is an additional signature set with an element of arity two. It contains the binary operator name `TENSOR`. In this case:

`TENSOR maps C-SCALAR x R-VECTOR -> C-VECTOR`.

![Equation](Images/F000011si1.png)

More details will be given about tensors in subsequent sections, but for the time being this should be sufficient for illustrating the complexification operation. For `C-SCALAR`, the corresponding carrier sets will always consist of the complex field `C`. In addition, the actual operation that is named `TENSOR` will be denoted by `⊗`, and it is such that `Hc = C ⊗ Hr`. Moreover, the operations corresponding to those of `V-ADD` and `S-MULT` are defined in an obvious fashion given next.

For any `a` and `b` in `R` and `u`, `v`, `w`, and `z` in `Hr`, it follows that:

For `V-ADD`: `(u + i v) + (w + i z) = (u + w) + i (v + z)`.

![Equation](Images/F000011si4.png)

For `S-MULT`: `(a + i b) ⋅ (u + i v) = (a ⋅ u − b ⋅ v) + i (a ⋅ v + b ⋅ u)`.

![Equation](Images/F000011si5.png)

Also, every vector `(u + i v)` in `Hc` is actually a short notation for `1 ⊗ u + i ⊗ v`.

The complexification of the inner product follows from the obvious expansion:

`IN-PROD`: `<u + i v | w + i z> = <u | w> + <v | z> + i (<u | z> − <v | w>)`

![Equation](Images/F000011si8.png)

Additionally, the norm squared of `u + i v` in `Hc` is `‖u + i v‖² = ‖u‖² + ‖v‖²`.

The expression for `Hc` could have been written in the form `Hc = Hr ⊗ C`, thus obtaining the same overall result. However, this will not be considered correct, even though they are isomorphic representations. Moreover, most operations in quantum disciplines are noncommutative. For this reason, the polyadic graph description is modified to represent the actual order in which operands are used. This was mentioned earlier for left or right `R`-modules. Again, for those operators for which the order of operand usage is important, the arrow tails are modified. The corresponding arrow tails have slash (`/`) indicators denoting the order. Thus, one slash (`/`) denotes the first operand, two slashes (`//`) represent the second operand, and so on. For the situation at hand, the arrow for the operator `TENSOR` has one tail with a single slash emanating from `C-SCALAR`, and the other tail with two slashes is connected to `R-VECTOR`. [Fig. 4.1](#Ch004_57-81_B9780443136979000011.xhtml#f0010) illustrates this fact. In this diagram, all arrows previously utilized in both Hilbert space descriptions and those for a field are omitted. If the other complexification method were used, that is, `Hc = Hr ⊗ C`, then the slashes in the below figure would be reversed.

![Figure 4.1 Polyadic graph for complexification.](Images/F000011f04-01-9780443136979.jpg)

[Figure 4.1](#Ch004_57-81_B9780443136979000011.xhtml#Bf0010) Polyadic graph for complexification.

### Example 4.3

In this example, we use the complexification just described with carrier set: `Hr = R`, the real one-dimensional Hilbert space as in [Example 4.1](#Ch004_57-81_B9780443136979000011.xhtml#enun1). In this case, `Hc = C ⊗ R` is just the one-dimensional Hilbert space; the vacuum space, `Hc = C`, is given in [Example 4.2](#Ch004_57-81_B9780443136979000011.xhtml#enun2).

At this point, as a reminder, the type of `SCALAR` determines whether the vector space is real or complex. For instance, if the `VECTOR` has a carrier set consisting of all complex numbers and the carrier set for `SCALAR` is the reals, with the usual operations, then the vector space is a real one.

## 4.3 Dual space used in quantum
