
Thus it is seen that the inner product in the higher dimensional space is the same as the inner product in the lower dimensional space raised to the power `d=2`. This is the crux of the matter; whenever the inner product in the higher dimension is desired, there is no need to utilize the feature maps. The result is obtained in the lower dimension simply by raising the inner product there to the power `d`, thus determining the higher dimension inner product.
More generally, the kernel method maps the dot product of two vectors in a Hilbert space `H[L]`=`R^(n)` into the dot product of two associated vectors in another Hilbert space `H[H]`=`R[m]`. When `n`=`m`, a linear kernel arises. In this case, `K(v,w)`=`<v, w>`, and for `a` in `R`, `<a v+u, w>`=`a` `<v, w>`+`<u, w>`. Similarly, `<v, a w+u>`=`a` `<v, w>`+`<v, u>`. Because it is linear, the kernel is `K(v,w)`=`v’w` and the feature map `Φ(v)`=`v`. The Gram matrix for this situation is an `n` by `n` matrix whose entries consist of inner products of vectors from `R^(n)`, specifically for {`v[1]`, …, `v[n]`} in `R^(n)`; then entry `G[ij]` in `G` equals `<v[i], v[j]>`.

### Example 1.11
Again consider the carrier set `H[L]`=`R²` with the vectors, `v`=`(v[1] v[2])′`=`(2 3)′`, and `w`=`(w[1] w[2])′`=`(4 –1)`. Assume that `H[L]`=`H[H]` and that the feature map `Φ` is the identity; then the Gram matrix for `v` and `w` is given in general and again using the actual tuple values for `v` and `w`, `G`=
```
\begin{array}{l}
{\left| \left\langle v,v \right\rangle\quad\left\langle v,w \right\rangle \right| = \left| 13 5 \right|}
\left. \left| \left\langle w,v \right\rangle\left\langle w,w \right\rangle \right|\mspace{21mu} \middle| 5 17 \middle| .# \right.
\end{array}
```
![Equation](Images/F000199si21.png)
When `m` is greater than `n`, `m`=`n^(d)`; then the dot product in `R^(n)`, raised to the positive integer power `d`, will equal the dot product in `R^(m)`. This is called the polynomial kernel method or the kernel trick. Here, vectors `v` and `w` in the domain space `R^(n)` are `v`=`(v[1] v[2]…v[n])′` and `w`=`(w[1] w[2]…w[n])′`. The mapping function `Φ`: `R^(n)` → `R^(m)` takes all `n` tuples of a vector, for instance, `v` in the domain space, and forms all possible homogeneous monomials of degree `d`. When forming these monomials, tuples within the domain vector are to be repeated in different orders. These distinct monomials then become the tuples of associated vectors in `R^(m)`; that is, monomials formed from tuples of `v` become tuples in `Φ(v)`. As far as the tuples are concerned, this is a nonlinear mapping. If this process is carried out, then `m`=`n^(d)`. Moreover, the kernel `k` is such that `k(v,w)`=`<Φ(v), Φ(w)>`=`(<v, w>)^(d)`. This result can be seen by taking the inner product in the higher dimensional space:
```
\left\langle {\Phi\left( v \right),\Phi\left( w \right)} \right\rangle = {\sum\limits_{\mathit{j}1}}\cdots{\sum\limits_{\mathit{jd}}{v_{\mathit{j}1}\cdots v_{\mathit{jd}} \cdot w_{\mathit{j}1}\cdots w_{\text{jd},}}} = {\sum\limits_{\mathit{j}1}{v_{\mathit{j}1} \cdot w_{\mathit{j}1}\cdots}}{\sum\limits_{\mathit{jd}}{v_{\mathit{jd}} \cdot w_{\text{jd},}}} = \left\lbrack {\sum\limits_{\mathit{j}}{v_{\mathit{j}} \cdot w_{\mathit{j}}}} \right\rbrack^{d} = \left\langle {v,w} \right\rangle^{d}
```
![Equation](Images/F000199si22.png).

### Example 1.12
In this example, let `n=2` and `d=3`. For `v`=`(v[1] v[2])′` in `R²`, `Φ(v)` = (`v[1]³ v[2]³ v[1]² v[2] v[1] v[2]² v[2] v[1]² v[2] v[1]² v[1] v[2] v[1] v[2] v[1] v[2]`) , ![Equation](Images/F000199si23.png) is a vector in `R⁸`. If `w`=`(w[1] w[2])'`, then homogeneous polynomials of degree three could fill the eight tuples of `Φ(w)`, just as it did `Φ(v)`. Assume that this is done, then forming:
```
\begin{matrix}
{\left\langle {\Phi\left( v \right),\Phi\left( w \right)} \right\rangle = {\sum\limits_{\mathit{j}1}}\cdots{\sum\limits_{\mathit{jd}}{v_{\mathit{j}1}\cdots v_{\mathit{jd}} \cdot w_{\mathit{j}1}\cdots w_{\mathit{jd}}}} = {\sum\limits_{\mathit{j}1}{\sum\limits_{\mathit{j}2}{\sum\limits_{\mathit{j}3}{v_{\mathit{j}1}v_{\mathit{j}2}v_{\mathit{j}3}w_{\mathit{j}1}w_{\mathit{j}2}w_{\mathit{j}3}}}}}
{= {\sum\limits_{\mathit{j}1}{v_{\mathit{j}1}w_{\mathit{j}1}}}{\sum\limits_{\mathit{j}2}{v_{\mathit{j}2}w_{\mathit{j}2}}}{\sum\limits_{\mathit{j}3}{v_{\mathit{j}3}w_{\mathit{j}3}}} = {\lbrack{\sum_{j = 1}^{2}{v_{j} \cdot w_{j}}}\\rbrack}^{3} = \left\langle {v,w} \right\rangle^{3} = \left\lbrack {v_{1}w_{1} + v_{2}w_{2}} \right\rbrack^{3}}
{= v_{1}^{3}w_{1}^{3} + v_{2}^{3}w_{2}^{3} + 3v_{1}^{2}v_{2}w_{1}^{2}w_{2} + 3v_{1}v_{2}^{2}w_{1}w_{2}^{2}.#}
\end{matrix}
```
![Equation](Images/F000199si24.png)
The benefit of using the feature map `Φ` is not using it. Dimension `n` data can be employed in a Hilbert space of dimension `m`=`n^(d)` without actually transforming the data to this dimension. This is true whenever the inner product of the higher dimensional data is all that is desired. Here, the only calculation needed is simply to find `<v, w>^(d)`. Applications of the feature map and kernel methods will be provided in a later chapter, along with several feature maps and various kernels.

### 1.1.11 R-Modules
Again, to take advantage of the in-depth high-level definition in the MSA, a vector space substructure will be described. It is called unit R-modules over a commutative ring `R` with unity. The sorts are exactly as in the MSA vector space and field descriptions. So the sorts are again `SCALAR` and `VECTOR`. The same is true for the signature sets, except that the partial operational name `INV` does not exist in a commutative unital ring, nor does it exist for a ring. Accordingly, in a polyadic graph as in [Fig. 1.1](#Ch001_1-19_B9780443136979000199.xhtml#f0010), the resulting graph would be modified. In this case, the dotted arrow for `INV` would be removed entirely.
The actual signature sets for R-modules are as in a vector space structure. Accordingly, the arity sequence for an R-modules is again `(1, 1, 2(1, 1))`. The signature sets are as follows:
```
\begin{array}{l}
\left. {Binary}{operation}{\left\{ {V - {ADD}} \right\}},V - {ADD}{maps}{VECTOR} \times {VECTOR}\rightarrow{VECTOR} \right.
\left. \quad\quad\quad\quad\quad\quad\quad\left\{ {S - {MULT}} \right\},S - {MULT}{maps}{SCALAR} \times {VECTOR}\rightarrow{VECTOR} \right.
\left. {Unary}{operation}{\left\{ {V - {MINUS}} \right\}},V - {MINUS}{maps}{VECTOR}\rightarrow{VECTOR} \right.
{{Zero} - {ary}{operation}{\left\{ {V - {ZERO}} \right\}},V - {ZERO} = 0.}
\end{array}
```
![Equation](Images/F000199si25.png)
Referring back to the equational identities for a vector space structure: `(1)–(8)`, they all hold for unit R-modules.
Recall that constraints `(1)–(4)` imply that the structure being described, that is, a unit R-modulus, is also an abelian group under vector addition. Moreover, sometimes, the commutative property of a ring is left out in the definition of a module. If this is the case, the constraints `(5)−(8)` are adjusted accordingly. For instance, constraint `(5)` might be written as only: `1 · v=v`. The `1`, is a one-sided identity. Additionally, in this case, care must be taken in defining `S-MULT`. It can only be defined, taking the order of operations into account. In the MSA polyadic diagram, slashes are used marking the tails of polyadic arrow. In this type of diagram, a slash `/` is used for the first operand and double slash `//` is used for the second argument of `S-MULT`. The symbology is important in describing left or right modules. When the ring is a field, all this does not matter.

### Example 1.13
