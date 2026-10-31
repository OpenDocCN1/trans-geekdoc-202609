
## 4.5 Outer Product

` (u ⊗ v)'* = (v ⊗ u) `, where the first term `(u ⊗ v)` is transposed and then conjugated.

[Fig. 4.5](#Ch004_57-81_B9780443136979000011.xhtml#f0030) depicts the outer product operation twice, once in general and then using kets and bras. The sort `SCALAR` is not illustrated. No other operations are illustrated in this diagram. Operator names solely involving Hilbert space, the complex field, or the unital associative algebra are not shown. In the lower illustration, the polyadic arrow has the first tail corresponding to a ket and the second to a bra. This is the opposite order as used when forming the inner product.

![Figure 4.5 Polyadic graphs illustrating outer product.](Images/F000011f04-05-9780443136979.jpg)

Figure 4.5 Polyadic graphs illustrating outer product.

For vectors `v` and `w` in `C^n`, the outer product `u` is most easily found by forming `u = v w'*`. So the dimension of `v` is `n` by one, and `w'*` is one by `n`; therefore, the outer product is an `n` by `n` matrix.

### Example 4.6

A simple instance of the outer product can be given with the carrier set associated with `VECTOR` being `C²`. The corresponding carrier set for `MATRIX` is the unital associative algebra of all 2 by 2 matrices over the complex field. So, for instance, if `v = (a b)'` and `w = (c d)'` are in `C²`, then we can use the operator `⊗`, denoting the actual operator whose name is outer product. For chosen `v` and `w`, `v ⊗ w` is the 2 by 2 matrix:

$|\\begin{matrix} {\\text{ac} \\ast} & {\\text{ad} \\ast} \\\\ \\end{matrix}|$

![Equation](Images/F000011si38.png)

$|\\begin{matrix} {\\text{bc} \\ast} & {\\text{bd} \\ast} \\\\ \\end{matrix}|$

![Equation](Images/F000011si39.png)

As mentioned earlier, the result could have been found using `v ⊗ w = v w'*`, where `w'*` is the conjugated transpose of `w`. So, `w'*` is a row vector, `w'* = (c* d*)`. However, from the definition of bras, `<w| = (c* d*)`, and kets, `|v> = (a b)'`, it follows that the representation in [Fig. 4.5](#Ch004_57-81_B9780443136979000011.xhtml#f0030) holds, that is, `v ⊗ w = |v><w| = (a b)' (c* d*)`.

## 4.6 Multilinear forms, wedge, and interior products

Before tensors are introduced, the concept of a n linear or multilinear form will be given. For this definition, the cartesian product `Π` operation is `Π[i] (Vi)` representing the product `V1 x V2 x … x Vn`. In this case, `{Vi} i=1, …, n` is a set of vector spaces over the complex field, and `Π` represents the cartesian product of all `n` vector spaces in the set. Then, the operation `M: ∏(Vi)→ C` is a multilinear map when `M` is linear in every coordinate. That is, the equational identities (1) and (2) hold:

1. `M (v1, v2, …, a vi, …, vn) = a M (v1, v2, …, vi, …, vn)`.

2. `M (v1, …, vi + v'i, …, vn) = M (v1, …, vi, …, vn) + M (v1, …, v'i, …,vn)`.

* In equation (1) mentioned earlier, vector `vi` is multiplied by scalar `a`, and the result is `M`, where `M` is the multilinear mapping; similarly, in equation (2) vectors `vi` and `vi'` are added together each is in `M`, and the result is the sum involving `M`.

* The set of all n multilinear maps `M: P (Vi) → C` themselves form a vector space `V`. The multilinear form is called alternating whenever it changes sign by interchanging, permuting, or transposing any two vectors. That is:

1. `M (v1, v2, …, vi, …, vj,…, vn) = − M (v1, v2, …, vj,…, vi, …,vn)`.

The set of all alternating n forms is also a vector space and is represented by `AnV*`. The dual basis for this space is denoted by `{e^S, such that card(S)=n; that is, there are n elements in S}`. Furthermore, `S` itself is a subset of `{1, 2, …, k}`, which results in an easy method for keeping track of the basis elements. For `k` greater than or equal to one, the symbol `e^S` is defined as `e^S = e^{j1} ∧ e^{j2} ∧ … ∧ e^{jn}` using `S = {j1 < j2 < … < jn}`. These `jk` superscripts are not powers; they are superscripts denoting a dual space basis. The wedge, `∧`, in logic denotes the (and) symbol.

For a basis set of `V`, `{ei1, …, ein}`, since `e^S` is the dual space, when `e^S` operates on vectors in `V`, scalars are obtained. In this case, `e^S(ei1, …, ein) = 1, 0, or −1`. This value depends on whether the indexing set for the basis of `V`, that is, `T = {i1 < … < in}`, involves the same `n`, corresponding basis elements as does `S`. Also the ordering has to be the same. When it does, this yields 1. When the same `n` elements are employed, but they are permuted, then for an even number of transpositions, 1 is again obtained. For an odd number of transpositions, −1 is the result. Otherwise, the value is zero. That is, it is zero when the dual basis `e^S` involves different vectors from those in its argument. The argument consists of the vectors in `V`, namely `(ei1, …, ein)`.

### Example 4.7

Using the aforementioned notation, let `k = 3`, but `n = 2`. A basis for the set of all alternating two forms, `A2V*`, must have two vectors in a basis, but they can be labeled with superscripts from the set, `{1, 2, 3}`. So, assume that the dual basis in this case is the set `{e¹, e³}`, that is, `e^S = e^{1,3} = e¹ ∧ e³`. Using this dual space basis, these vectors `e^S` can operate on vectors in `V`, and since they are in the dual space, the result is a scalar. So for the given dual basis, the wedge operating on `e2` and `e3` results in `(e¹ ∧ e³)(e2, e3) = 0`. This is because different labeled vectors are employed. Next, `(e¹ ∧ e³)(e3, e1) = −1`; this occurs because the vectors have the same labels, but in different single-transposed orders. Finally, `(e¹ ∧ e³)(e1, e3) = 1`, because the vectors have the same labels and identical order.

Next, use linear combinations of vectors from `V`, with scalars `ai` and `bj` in `C`. The dual operation is applied illustrating the linearity aspects. Let the sum for `v = Σ_{i = 1}^{3} ai ei` and also the sum for `w = Σ_{j = 1}^{3} bj ej`; then `(e¹ ∧ e³)(v, w) = a1 b3 − a3 b1`. This follows, since seven terms among the nine terms have the value zero. For instance, `(e¹ ∧ e³)(a1 e1, b2 e2) = a1 b2 (e¹ ∧ e³)(e1, e2) = a1 b2·0 = 0`; this follows first using linearity, that is factoring out `a1 b2`. Then notice that the superscripts are in `{1, 3}`, but the vectors in `V` are with labels in `{1, 2}`.

For the vector space of alternating n forms, `AnV*`, its dimension is denoted by `dim`, and its dimension is calculated using the combination formula of k things then n at a time: `(k/n) = k!/(n! (k−n)!)`. It follows that `dim(AkV*) = 1`, since in this case `n = k`, that is, k things taken k at a time, and so `(k/k) = k!/(k! (k−k)!)` equals one. Moreover, `AkV* = {0}` for `n > k`. When `n = k`, the result is often called a top form, because no larger value of `n` can be used without obtaining zero. Also `A1V* = V*`. The degree `n`, of form `w`, is denoted by `deg(w)` and is defined by the relation `w` is an element of `AnV*`. Suppose that the wedge or exterior product for `w` and `u` are elements of `AnV*` and `AmV*`, respectively. Here, `w ∧ u` is an element of `A(n+m)V*` defined as follows: `(w ∧ u)(v1, …, vn, v(n+1), …, v(n+m)) = sum over all permutations s of {1, …, n+m}, of the product: [sign(s) w(vs1, …, vsn) u(vs(n+1), …, vs(n+m)) ]`, and preserving the order: `s1 < … < sn`, and `s(n+1) < … < s(n+m)`, but also the summation involves shuffling of arguments.
