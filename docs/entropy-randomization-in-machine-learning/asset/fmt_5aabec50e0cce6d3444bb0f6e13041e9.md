
| *S* || 5 || *a*[0] || \-0.3191 || 0.1600 || \-0.2210 || 0.2210 |

| *a*[1] || \-0.2690 || 0.0804 |

| *a*[2] || \-0.1893 || 0.1498 |

| *a*[3] || \-0.1686 || 0.1679 |

| *a*[4] || \-0.2009 || 0.1333 |

| *a*[5] || \-0.2527 || 0.0863 |

| *a*[6] || 0.9226 || 1.2945 |

| *a*[7] || \-0.2073 || 0.2157 |

| *T* || 4 || *b*[0] || 0.0341 || 0.4649 || \-0.7110 || 0.7110 |

| *b*[1] || \-0.6822 || 0.4936 |

| *b*[1] || \-0.1626 || 0.9894 |

| *b*[2] || \-0.8443 || 0.3193 |

| *b*[3] || \-0.8135 || 0.3945 |

| *R* || 4 || *c*[0] || \-0.3217 || 0.4938 || \-0.4661 || 0.4661 |

| *c*[1] || 0.1180 || 1.2049 |

| *c*[1] || \-0.5728 || 0.6302 |

| *c*[2] || \-0.3641 || 1.1894 |

| *c*[3] || \-0.6541 || 0.4912 |

|  |

Consequently, there are three time series for each zone, each containing 35 values. We divide them into two groups as follows:

*   the training collections ($n = \\overline{0,24}$)

    $$\\begin{array}{r} {{\\mathfrak{C}}\_{tn}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)}\\lbrack n\\rbrack,R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  

    $$\\begin{array}{r} {\\mathfrak{D}\_{tn}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)\\lbrack n\\rbrack},R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  

    and

    $$\\begin{array}{r} {\\Im\_{tn}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)\\lbrack n\\rbrack},R^{(r)}\\lbrack n\\rbrack} \\right)} \\\\ \\end{array}$$  

    for zones *C*, *D* and *I*, respectively;

*   the testing collections ($n = \\overline{25,34}$)

    $$\\begin{array}{r} {{\\mathfrak{C}}\_{ts}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)}\\lbrack n\\rbrack,R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  

    $$\\begin{array}{r} {\\mathfrak{D}\_{ts}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)\\lbrack n\\rbrack},R^{(r)}\\lbrack n\\rbrack} \\right),} \\\\ \\end{array}$$  

    and

    $$\\begin{array}{r} {\\Im\_{ts}\\lbrack n\\rbrack = \\left( {S^{(r)}\\lbrack n\\rbrack,T^{(r)}\\lbrack n\\rbrack,R^{(r)}\\lbrack n\\rbrack} \\right)} \\\\ \\end{array}$$  

    for zones *C*, *D*, and *I*, respectively.

### 11.4.5Entropy-Randomized machine learning of *LDRR*

#### 11.4.5.1Formation of data sets to train *LDRR*

The available dataset is divided in a proportion of 70% to 30% for model training and testing, respectively. The training procedure will be performed separately for *LDRR-LA*, *LDRR-T* and *LDRR-P*.

To train the model, we use the data from the training collection (${\\mathfrak{C}}\_{tn}\\lbrack n\\rbrack,\\,\\mathfrak{D}\_{tn}\\lbrack n\\rbrack,\\,\\Im\_{tn}\\lbrack n\\rbrack,\\,\\, n = \\overline{0,24}$).

From the historical data we construct the column vectors

$$\\begin{aligned} & {\\mathbf{S}\_{(n - p)}^{(r)} = \\left\\{ 1,S^{r}\\lbrack n - 1\\rbrack,\\ldots,S^{(r)}\\lbrack n - p\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\mathbf{S}\_{(p)}^{(r)} = \\left\\{ S^{(r)}\\lbrack p\\rbrack,\\ldots,S^{(r)}\\lbrack 24\\rbrack \\right\\},} \\\\ & {\\mathbf{T}\_{(n - p)}^{(r)} = \\left\\{ 1,T^{(r)}\\lbrack n - 1\\rbrack,\\ldots,T^{(r)}\\lbrack n - p\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\mathbf{T}\_{(p)}^{(r)} = \\left\\{ T^{(r)}\\lbrack p\\rbrack,\\ldots,T^{(r)}\\lbrack 24\\rbrack \\right\\},} \\\\ \\end{aligned}$$  

(11.62)

$$\\begin{aligned} & {\\mathbf{R}\_{(n - p)}^{(r)} = \\left\\{ 1,R^{(r)}\\lbrack n - 1\\rbrack,\\ldots,R^{(r)}\\lbrack n - p\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\mathbf{R}\_{(p)}^{(r)} = \\left\\{ R^{(r)}\\lbrack p\\rbrack,\\ldots,R^{(r)}\\lbrack 24\\rbrack \\right\\},} \\\\ & {\\text{\\quad\\quad}\\text{\\quad\\quad}\\text{\\quad\\quad}n = \\overline{p,24},} \\\\ \\end{aligned}$$  

(11.63)

and the matrices

$$\\begin{array}{r} {S\_{p}^{(r)} = \\left( \\begin{array}{l} \\mathbf{S}\_{(0)} \\\\ \\cdots \\\\ \\mathbf{S}\_{(24 - p)} \\\\ \\end{array} \\right),\\quad T\_{p}^{(r)} = \\left( \\begin{array}{l} \\mathbf{T}\_{(0)} \\\\ \\cdots \\\\ \\mathbf{T}\_{(24 - p)} \\\\ \\end{array} \\right),\\quad R\_{p}^{(r)} = \\left( \\begin{array}{l} \\mathbf{R}\_{(0)} \\\\ \\cdots \\\\ \\mathbf{R}\_{(24 - p)} \\\\ \\end{array} \\right).} \\\\ \\end{array}$$  

(11.64)

#### 11.4.5.2ERML algorithm

We apply the randomized machine learning method (see Section 3) to estimate the PDFs of the model parameters and measurement noises. The ERML algorithm for *LDRR-LA* has the form

$$\\begin{aligned} & {\\mathcal{H}\\lbrack P(\\mathbf{a},Q(\\xi)\\rbrack = - {\\int\_{\\mathcal{A}}\\,}P(\\mathbf{a})\\,\\ln P(\\mathbf{a})\\, d\\mathbf{a} -} \\\\ & \\left. {\\sum\\limits\_{n = p}^{24}{\\int\_{\\Xi\_{n}}\\,}}Q\_{n}(\\xi\\lbrack n\\rbrack)\\,\\ln Q\_{n}(\\xi\\lbrack n\\rbrack)\\, d\\xi\\lbrack n\\rbrack\\Rightarrow\\max \\right. \\\\ \\end{aligned}$$  

(11.65)

subject to the constraints

$$\\begin{aligned} {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})\\, d\\mathbf{a} = 1,} & {\\quad{\\int\_{\\Xi\_{n}}Q\_{n}}(\\xi\\lbrack n\\rbrack)\\, d\\xi\\lbrack n\\rbrack = 1,} \\\\ {{\\int\_{\\mathcal{A}}P}(\\mathbf{a})D\_{(n - p)}^{(r)}\\,\\mathbf{a}\\, d\\mathbf{a} +} & {{\\int\_{\\Xi\_{n}}Q}(\\xi\\lbrack n\\rbrack)\\xi\\lbrack n\\rbrack\\, d\\xi\\lbrack n\\rbrack = S^{(r)}\\lbrack n\\rbrack,} \\\\ & {\\text{\\quad\\quad}n = \\overline{p,24},} \\\\ \\end{aligned}$$  

(11.66)

with the block matrix

$$\\begin{array}{r} {D\_{(n - p)}^{(r)} = \\left\\lbrack {\\mathbf{S}\_{(n - p)}^{(r)},\\, T\_{(p)}^{(r)}\\lbrack n\\rbrack,\\, R\_{(p)}^{(r)}\\lbrack n\\rbrack} \\right\\rbrack.} \\\\ \\end{array}$$  

(11.67)

The solution of this problem, parametrized by the Lagrange multipliers *θ* = {*θ*[*p*],…,*θ*[24]}, is given by

$$\\begin{aligned} & {P^{\*}(\\mathbf{a},\\theta) = \\frac{\\exp\\left( {- \\left\\langle \\theta,D\_{(n - p)}^{(r)}\\,\\mathbf{a} \\right\\rangle} \\right)}{\\mathcal{P}(\\theta)},} \\\\ & {\\mathcal{P}(\\theta) = {\\int\_{\\mathcal{A}}\\exp}\\left( {- \\left\\langle \\theta,D\_{(n - p)}^{(r)}\\,\\mathbf{a} \\right\\rangle} \\right)\\, d\\mathbf{a}.} \\\\ \\end{aligned}$$  

(11.68)

The measurement noise for *LDRR-LA* has the entropy-optimal PDFs

$$\\begin{aligned} & {Q\_{n}^{\*}(\\xi\\lbrack n\\rbrack,\\theta\_{n}) = \\frac{\\exp( - \\xi\\lbrack n\\rbrack\\theta\_{n})}{\\mathcal{Q}\_{n}(\\theta\_{n})},} \\\\ & {\\mathcal{Q}\_{n}(\\theta\_{n}) = {\\int\_{\\Xi\_{n}}\\exp}( - \\xi\\lbrack n\\rbrack\\,\\theta\_{n})d\\,\\xi\\lbrack n\\rbrack.} \\\\ \\end{aligned}$$  

(11.69)

The Lagrange multipliers *θ* are calculated from the system of equations

$$\\begin{aligned} {\\mathcal{P}^{- 1}(\\theta)\\int\_{\\mathcal{A}}\\exp} & {\\left( {- \\left\\langle \\theta,D\_{(n - p)}^{(r)}\\,\\mathbf{a} \\right\\rangle} \\right)\\, D\_{(n - p)}^{(r)}\\mathbf{a}\\, d\\,\\mathbf{a} +} \\\\ {+ \\mathcal{Q}\_{n}^{- 1}(\\theta)\\int\_{\\Xi}} & {\\exp( - \\xi\\lbrack n\\rbrack\\,\\theta\_{n})\\, d\\xi\\lbrack n\\rbrack = S^{(r)}\\lbrack n\\rbrack,} \\\\ & {\\quad n = \\overline{p,24}.} \\\\ \\end{aligned}$$  

(11.70)

For *LDRR-T* and *LDRR-P*, the RML algorithm differs from (11.4.5.2, 11.4.5.2): it is necessary to estimate the joint PDFs *W*(**b**, *μ*) and *F*(**c**, *ζ*) of the model parameters and random input sequences as well as the PDFs *E*(*η*) and *G*(*χ*) of the measurement noises.

Adapting the ERML algorithm for *LDRR-T*, we obtain the following optimization problem:

$$\\begin{aligned} & {\\mathcal{H}\\lbrack W(\\mathbf{b},\\mu),E(\\eta)\\rbrack = - {\\int\_{\\mathcal{B}{\\cap \\mathcal{M}}}\\,}W(\\mathbf{b},\\mu)\\,\\ln W(\\mathbf{b},\\mu)\\, d\\mathbf{b}\\, d\\mu -} \\\\ & \\left. \\text{\\quad\\quad} - {\\sum\\limits\_{n = p}^{24}{\\int\_{\\mathcal{E}\_{n}}\\,}}E\_{n}(\\eta\\lbrack n\\rbrack)\\,\\ln E\_{n}(\\eta\\lbrack n\\rbrack)\\, d\\eta\\lbrack n\\rbrack\\Rightarrow\\max \\right. \\\\ \\end{aligned}$$  

(11.71)

subject to the constraints
