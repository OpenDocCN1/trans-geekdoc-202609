
$$\\begin{aligned} & {P^{\*}(\\mathbf{a}) = P\_{0}(\\mathbf{a})\\frac{\\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack}{\\mathcal{P}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)})},} \\\\ & {Q\_{j}^{\*}({\\overline{\\xi}}^{(j)}) = Q\_{j}^{0}({\\overline{\\xi}}^{(j)})\\frac{\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack}{\\mathcal{Q}\_{j}({\\overline{\\theta}}^{(j)}),}\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$

(5.64)

Here

$$\\begin{aligned} & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\mathcal{P}({\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}) = {\\int\_{\\mathcal{A}}P\_{0}}(\\mathbf{a}) \\times} \\\\ & {\\times \\exp\\left\\lbrack \\left. - {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{B}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}\\rbrack \\right\\rangle \\right\\rbrack d\\mathbf{a},} \\\\ & {\\quad\\text{\\quad\\quad}\\mathcal{Q}\_{j}({\\overline{\\theta}}^{(j)}) = {\\int\_{\\Xi}Q\_{j}^{0}}({\\overline{\\xi}}^{(j)})\\exp\\left\\lbrack {- \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\xi}}^{(j)} \\right\\rangle} \\right\\rbrack d{\\overline{\\xi}}^{(j)},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s}.} \\\\ \\end{aligned}$$

(5.65)

Clearly, the entropy-optimal PDFs are parameterized by the Lagrange multipliers and represent exponential functions. However, they may have any form, depending on the parameters `a`. [Figure 5.2](#chapter5.xhtml#f5_2), [Figure 5.3](#chapter5.xhtml#f5_3), [Figure 5.4](#chapter5.xhtml#f5_4), [Figure 5.5](#chapter5.xhtml#f5_5) demonstrate some examples of the estimated PDFs of the model parameters. For the linear RPM-Orig model, the estimated PDFs are always exponential functions; see [Fig. 5.2](#chapter5.xhtml#f5_2). Note that their form is affected by the input and output measurements.

![Figure 5.2: p(a\_{1},a\_{2}) = \\exp( - 0.3a\_{1} + 2.5a\_{2}).](images/fig5_2.jpg)

[Figure 5.2:](#chapter5.xhtml#f5_2b) *p*(*a*[1], *a*[2]) = exp ( − 0.3*a*[1] + 2.5*a*[2]).

![Figure 5.3: p(a\_{1},a\_{2}) = exp(4a\_{1} - a\_{1}^{2} + a\_{2}).](images/fig5_3.jpg)

[Figure 5.3:](#chapter5.xhtml#f5_3b) *p*(*a*[1], *a*[2]) = *e**x**p*(4*a*[1] − *a*[1]² + *a*[2]).

![Figure 5.4: p(a\_{1},a\_{2}) = exp(4a\_{1} - a\_{1}^{2} + 6a\_{2} - a\_{2}^{2}).](images/fig5_4.jpg)

[Figure 5.4:](#chapter5.xhtml#f5_4b) *p*(*a*[1], *a*[2]) = *e**x**p*(4*a*[1] − *a*[1]² + 6*a*[2] − *a*[2]²).

![Figure 5.5: p(a\_{1},a\_{2}) = exp(0.5a\_{1} + 3.5a\_{2} + 2a\_{1}^{2} - a\_{1}^{3} - 0.2a\_{2}^{2} - 0.2a\_{2}^{3}).](images/fig5_5.jpg)

[Figure 5.5:](#chapter5.xhtml#f5_5b) *p*(*a*[1], *a*[2]) = *e**x**p*(0.5*a*[1] + 3.5*a*[2] + 2*a*[1]² − *a*[1]³ − 0.2*a*[2]² − 0.2*a*[2]³).

For the nonlinear RPMs, the estimates have a wider variety of structural forms. For example, the estimated PDFs for the RPM-Orig models with the quadratic, quadratic-linear and cubic nonlinearities are shown in [Fig. 5.3](#chapter5.xhtml#f5_3), [Fig. 5.4](#chapter5.xhtml#f5_4), [Figure 5.5](#chapter5.xhtml#f5_5).

### 5.4.2 Randomized models of the RPM-Rel class with output errors

To construct optimality conditions for this class of the randomized models, introduce similar notations as (5.57–5.4.1), i.e.,

* the Lagrange multiplier `λ` for the first constraint in (5.21), writing it in the form

$$\\begin{array}{r} {w\\lbrack W(\\mathbf{u})\\rbrack = 1 - {\\int\_{\\mathcal{U}}W}(\\mathbf{u})d\\mathbf{u};} \\\\ \\end{array}$$

(5.66)

* the vector `\\overline{\\mu} = \\left\\{ \\mu\_{1},\\ldots,\\mu\_{s} \\right\\}` composed of the Lagrange multipliers for the second group of constraints in (5.21), writing them in the form

$$\\begin{aligned} & {\\mathbf{g}\\lbrack G(\\overline{\\eta})\\rbrack = \\left\\{ g^{(1)}\\lbrack G\_{1}({\\overline{\\eta}}^{(1)})\\rbrack,\\ldots,g^{(s)}\\lbrack G\_{s}({\\overline{\\eta}}^{(s)})\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}g^{(j)}\\lbrack G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack = 1 - {\\int\_{\\mathcal{E}}G\_{j}}({\\overline{\\eta}}^{(j)})\\, d{\\overline{\\eta}}^{(j)},} \\\\ & {\\text{\\quad\\quad}\\quad\\text{\\quad\\quad}\\text{\\quad\\quad}j = \\overline{1,s};} \\\\ \\end{aligned}$$

(5.67)

* the vectors `${\\overline{\\theta}}^{(j)} = \\left\\{ \\theta\_{1}^{(j)},\\ldots,\\theta\_{m}^{(j)} \\right\\},\\, j = \\overline{1,s},$` composed of the Lagrange multipliers for the constraints (5.22), writing them in the form

$$\\begin{aligned} & {\\text{\\quad\\quad}\\mathbf{h}^{(j)}\\lbrack W(\\mathbf{u}),G\_{j}({\\overline{\\eta}}^{(j)})\\rbrack = \\mathbf{y}(t\_{j}) -} \\\\ & \\left. - {\\int\_{\\mathcal{U}}W}(\\mathbf{u})\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}),\\, \\middle| \\, h = \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack\\, d\\mathbf{u} - \\right. \\\\ & {+ {\\int\_{\\mathcal{E}\_{j}}\\,}G\_{j}({\\overline{\\eta}}^{(j)})\\,{\\overline{\\eta}}^{(j)}\\, d{\\overline{\\eta}}^{(j)},\\quad j = \\overline{1,s}.} \\\\ \\end{aligned}$$

(5.68)

Using these notations, define the Lagrange functional

$$\\begin{aligned} {\\mathcal{L}\\lbrack W(\\mathbf{u}),G(\\overline{\\eta})\\rbrack} & {= \\mathcal{H}\\lbrack W(\\mathbf{u}),G(\\overline{\\eta})\\rbrack + \\lambda w\\lbrack W(\\mathbf{u})\\rbrack + \\left\\langle \\overline{\\mu},\\mathbf{g}\\lbrack G(\\overline{\\eta})\\rbrack \\right\\rangle +} \\\\ & {\\left. + {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{(j)},\\mathbf{h}^{(j)}\\lbrack W(\\mathbf{u}),G\_{j}( \\right.}{\\overline{\\eta}}^{(j)})\\rbrack \\right\\rangle.} \\\\ \\end{aligned}$$

(5.69)

To get optimality conditions for the Lagrange functional, we will again employ the Gateaux derivative-based method; see (5.60, 5.4.1). The corresponding first-order optimality conditions have the form

$$\\begin{aligned} {\\ln\\frac{W^{\*}(\\mathbf{u})}{W\_{0}(\\mathbf{u})}} & {+ 1 + \\lambda +} \\\\ \\left. + {\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{j},\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},\\, \\middle| \\, h = \\right. & {\\left. \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack \\right\\rangle = 0,} \\\\ {\\ln\\frac{G\_{j}^{\*}({\\overline{\\eta}}^{(j)})}{G\_{j}^{0}({\\overline{\\eta}}^{(j)})} + 1 + \\mu\_{j}} & {+ \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle = 0,} \\\\ {j =} & {\\overline{1,s}.} \\\\ \\end{aligned}$$

(5.70)

The solution of these equations within the Lagrange multipliers `λ`, `μ[1]`, …, `μ[s]`, and `${\\overline{\\theta}}^{(1)},\\ldots,{\\overline{\\theta}}^{(s)}$` is given by

$$\\begin{aligned} {W^{\*}(\\mathbf{u}) = W\_{0}} & {(\\mathbf{u})\\exp\\lbrack - 1 - \\lambda -} \\\\ {{\\sum\\limits\_{j = 1}^{s}\\left\\langle {\\overline{\\theta}}^{j},\\mathbf{D}^{(j)}\\lbrack\\mathbf{x}((t\_{j},\\tau\_{h}) \\right.},} & {\\,\\left| \\, r = \\overline{1,(j-1)}),\\mathbf{a}^{-} + A\\,\\mathbf{u}\\rbrack \\right\\rangle\\rbrack,} \\\\ {G\_{j}^{\*}({\\overline{\\eta}}^{(j)}) = G\_{j}^{0}({\\overline{\\eta}}^{(j)})} & {\\exp\\left\\lbrack {- 1 - \\mu\_{j} - \\left\\langle {\\overline{\\theta}}^{(j)},{\\overline{\\eta}}^{(j)} \\right\\rangle} \\right\\rbrack,} \\\\ & {j = \\overline{1,s}.} \\\\ \\end{aligned}$$

(5.71)

The Lagrange multipliers `λ` and `μ[1]`, …, `μ[s]` can be eliminated using the normalization conditions (5.28). Then formulas (5.4.2) yield the following entropy-optimal estimates for the PDFs of the RPM-Rel model parameters and measurement noises:
