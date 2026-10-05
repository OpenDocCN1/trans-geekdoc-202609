
In this expression, *w̃*[*i*, *k*[*h*]]^((*h*,  ± ))\[*n*[1], …, *n*[*h*]\] are given functions that describe the left and right limits of the above intervals. For example, they can be defined as the exponential functions

$$
\\begin{aligned} {{\\widetilde{w}}\_{i,k\_{h}}^{(h, - )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {= {\\prod\\limits\_{j = 1}^{h}\\beta\_{(i,k\_{h})}^{(h, - )}}(j)\\,\\exp\\left( {- \\alpha\_{(i,k\_{h})}^{(h, - )}(j)\\, n\_{j}} \\right),} \\\\ {{\\widetilde{w}}\_{i,k\_{h}}^{(h, + )}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack} & {= {\\prod\\limits\_{j = 1}^{h}\\beta\_{(i,k\_{h})}^{(h, + )}}(j)\\,\\exp\\left( {- \\alpha\_{(i,k\_{h})}^{(h, + )}(j)\\, n\_{j}} \\right).} \\\\ \\end{aligned}
$$

(4.39)

A convenient approach is to treat their ordinates as the RPM parameters. This allows us to transform the nonlinear RPM to its linear analog of considerably higher dimension. The transformation procedure for the one-dimensional RPM (with one input and one output) is given by

$$
\\begin{array}{r} {\\hat{y}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{H}\\sum\\limits^{K}}(n\_{1},\\ldots,n\_{h}) = 0w^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack\\,{\\prod\\limits\_{i = 1}^{h}x}\\lbrack k - n\_{i}\\rbrack,\\text{\\quad\\quad}k \\geq K.} \\\\ \\end{array}
$$

(4.40)

Introduce a lexicographical ordering of the variables {*n*[1],…,*n*[*h*]} by reassigning numbers from 0 to *t*[*h*] = (*K* + 1)^(*h*) − 1 to the resulting sets. Then

$$
\\begin{array}{r} \\left. \\left\\{ n\_{1},\\ldots,n\_{h} \\right\\}\\rightarrow i^{(h)},\\text{\\quad\\quad}i^{(h)} \\in \\lbrack 0,t\_{h}\\rbrack. \\right. \\\\ \\end{array}
$$

(4.41)

In accordance with this numbering scheme, define the following indexes for the random parameters that correspond to the values of the pulse characteristics at the discrete times 0, 1, …, *K*:

$$
\\begin{array}{r} \\left. a\_{i^{(h)}}^{(h)}\\rightarrow w^{(h)}\\lbrack n\_{1},\\ldots,n\_{h}\\rbrack,\\text{\\quad\\quad}i^{(h)} \\in \\lbrack 0,t\_{h}\\rbrack. \\right. \\\\ \\end{array}
$$

(4.42)

Construct a random vector

$$
\\begin{array}{r} {\\mathbf{a}(h) = \\left\\{ a\_{0}^{(h)},\\ldots,a\_{t\_{h}}^{(h)} \\right\\}.} \\\\ \\end{array}
$$

(4.43)

The elements of the vector **a**(*h*) —see (4.38)—take values within the intervals

$$
\\begin{array}{r} {\\mathcal{A}^{(h)}(i^{(h)}) = \\left\\lbrack {a\_{-}^{(h)}(i^{(h)}),\\, a\_{+}^{(h)}(i^{(h)})} \\right\\rbrack.} \\\\ \\end{array}
$$

(4.44)

By analogy with (4.41), introduce a lexicographical ordering of the variables *k* − *n*[1], …, *k* − *n*[*h*], where *k* is a fixed parameter and the indexes *n*[1], …, *n*[*h*] take values within the interval \[0,*K\]*.

For each fixed *k*, renumber the resulting sets as follows:

$$
\\begin{array}{r} \\left. \\left\\{ k - n\_{1},\\ldots,k - n\_{h} \\right\\}\\rightarrow(k,i^{(h)}). \\right. \\\\ \\end{array}
$$

(4.45)

Then the lexicographically ordered products of the variables *x*\[*k* − *n*[1]\], …, *x*\[*k* − *n*[*h*]\] with fixed *k* form the vector

$$
\\begin{array}{r} {\\mathbf{x}^{(h)}\\lbrack k\\rbrack = \\left\\{ {x\_{k,0}^{(h)},\\ldots,x\_{k,t\_{h}}^{(h)}} \\right\\}.} \\\\ \\end{array}
$$

(4.46)

Consequently, the expression (4.40) can be written as

$$
\\begin{array}{r} {\\hat{y}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{H}\\left\\langle \\mathbf{a}^{(h)},\\,\\mathbf{x}^{(h)}\\lbrack k\\rbrack \\right\\rangle},} \\\\ \\end{array}
$$

(4.47)

where ⟨•, •⟩ denotes the scalar product of vectors ∙ and  • .

Consider a one-dimensional RPM with structured nonlinearities (see [Fig. 4.11(a)](#chapter4.xhtml#f4_11)) and the following discrete time-varying functions as its input:

$$
\\begin{array}{r} {\\hat{y}\\lbrack k\\rbrack = {\\sum\\limits\_{h = 1}^{H}\\left( {{\\sum\\limits\_{n = 0}^{K}w^{(h)}}\\lbrack n\\rbrack x\\lbrack k - n\\rbrack} \\right)^{h}},\\text{\\quad\\quad}k \\geq K.} \\\\ \\end{array}
$$

(4.48)

The pulse characteristics *w*^((*h*))\[*n*\] have a finite memory *K* and random parameters. Again, as the latter choose their ordinates, i.e.,

$$
\\begin{array}{r} {w^{(h)}\\lbrack n\\rbrack = a\_{n}^{(h)},\\quad n = \\overline{0,K}.} \\\\ \\end{array}
$$

(4.49)

Construct the vector

$$
\\begin{array}{r} {\\mathbf{a}^{(h)} = \\left\\{ a\_{0}^{(h)},\\ldots,a\_{K}^{(h)} \\right\\}.} \\\\ \\end{array}
$$

(4.50)

The parameters *a*[*n*]^((*h*)) are random, independent, and take their values within the intervals

$$
\\begin{array}{r} {\\mathcal{A}\_{n}^{(h)} = \\lbrack - A\_{n}^{(h)},\\, A\_{n}^{(h)}\\rbrack,\\quad A\_{n}^{(h)} = \\beta\_{n}^{(h)}\\exp( - \\alpha\_{n}^{(h)}).} \\\\ \\end{array}
$$

(4.51)

The PDFs $p\_{n}^{(h)}(a\_{n}^{(h)}),\\,\\, n = \\overline{0,K},$ are defined on these intervals.

Get back to equality (4.48) and introduce the following notations:

* the index set

$$
\\begin{array}{r} {\\mathcal{I}\_{h}(K) = \\left\\{ i\_{n}:\\,{\\sum\\limits\_{n = 0}^{K}i\_{n}} = h,\\, i\_{n} = \\overline{0,K} \\right\\};} \\\\ \\end{array}
$$

(4.52)

* the vector

$$
\\begin{array}{r} {\\mathbf{i} = \\left\\{ i\_{0},\\ldots,i\_{K} \\right\\};} \\\\ \\end{array}
$$

(4.53)

* the function

$$
\\begin{array}{r} {C\_{(k,i\_{n})}(x) = \\frac{1}{i\_{n}!}\\, x^{i\_{n}}\\lbrack k - n\\rbrack.} \\\\ \\end{array}
$$

(4.54)

Then formula (4.48) can be written as

$$
\\begin{aligned} {\\hat{y}\\lbrack k\\rbrack} & {= {\\sum\\limits\_{h = 1}^{H}V\_{k}^{(h)}}(\\mathbf{a}^{(h)},x),} \\\\ {V\_{k}^{(h)}(\\mathbf{a}^{(h)},x)} & {= {\\sum\\limits\_{\\mathbf{i} \\in \\mathcal{I}\_{h}(K)}\\,}{\\prod\\limits\_{n = 0}^{K}\\,}C\_{(k,i\_{n})}(x)\\,{\\lbrack a\_{n}^{(h)}\\rbrack}^{i\_{n}}.} \\\\ \\end{aligned}
$$

(4.55)

Hence, unlike the RPM (4.40), the model under consideration is nonlinear with power nonlinearities.

## 4.2.5 Nonlinear dynamic models with polynomial nonlinearities

In machine learning problems, it is often necessary to deal with dynamic objects whose observable output has jumps at certain times or under certain values of its input. In other cases, there exists prior information about the object's properties that defines its structure as illustrated in [Fig. 4.13(a)](#chapter4.xhtml#f4_13) or [Fig. 4.13(b)](#chapter4.xhtml#f4_13). The nonlinear blocks in these diagrams are described by orthonormal polynomials of different classes (see [Table 4.1](#chapter4.xhtml#t4_1)).

![Figure 4.13](images/fig4_13.jpg)

[Figure 4.13](#chapter4.xhtml#f4_13b)

Consider an RPM with the structure presented in [Fig. 4.13(a)](#chapter4.xhtml#f4_13). Using orthogonal polynomials *g*[*k*](*x*), let us write this RPM in the following form:

$$
\\begin{array}{r} \\left. \\hat{y}(t) = {\\sum\\limits\_{k = 0}^{K}c\_{k}}{\\int\_{0}^{t}w}(t - \\tau\\, \\middle| \\mathbf{b})\\, g\_{k}(x(\\tau))d\\tau, \\right. \\\\ \\end{array}
$$

(4.56)

where the coefficients *c*[0], …, *c*[*K*] are independent random variables of the interval type, i.e.,

$$
\\begin{array}{r} {c\_{k} \\in \\mathcal{C}\_{k} = \\lbrack c\_{k}^{-},c\_{k}^{+}\\rbrack,\\text{\\quad\\quad}k = \\overline{0,K}.} \\\\ \\end{array}
$$

(4.57)

The parameters **b** of the pulse characteristic *w*(*t* |**b**) are randomized and belong to the intervals

$$
\\begin{array}{r} {\\mathbf{b} \\in \\mathcal{B} = \\lbrack\\mathbf{b}^{-},\\mathbf{b}^{+}\\rbrack.} \\\\ \\end{array}
$$

(4.58)

Now get back to the block diagram in [Fig. 4.13(b)](#chapter4.xhtml#f4_13). Obviously, the linear and nonlinear dynamic elements of the object have interchanged their places. The object's input is a function *x*(*t*). Let us construct the RPM of this object using the pulse characteristic with random parameters *w*(*τ* | **b**) for the linear element and a collection of orthogonal polynomials with random coefficients for the nonlinear element. Then the RPM can be written as
