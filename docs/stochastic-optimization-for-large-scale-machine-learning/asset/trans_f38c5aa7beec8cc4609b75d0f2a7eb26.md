

$$\\begin{array}{l} \\begin{array}{l} {\\underset{w^{i,j},b^{i,j},\\xi^{i,j}}{\\min}\\quad\\frac{1}{2}{(w^{i,j})}^{T}w^{i,j} + C{\\sum\\limits\_{t}\\xi\_{t}^{i,j}}} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.10)

$$\\begin{array}{l} \\begin{array}{l} {\\text{s}.\\text{t}.\\quad({(\\text{w}^{\\text{i},\\text{j}})}^{\\text{T}}\\text{x+b}^{\\text{i},\\text{j}}) \\geq \\text{1-}\\xi^{\\text{i},\\text{j}},\\quad\\text{for}\\,\\text{y=i},} \\\\ {({(w^{i,j})}^{T}x + b^{i,j}) \\leq - 1 + \\xi^{i,j},\\quad\text{for}\\, y = j,} \\\\ {\\xi\_{i,j} \\geq 0,} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.11)

where `t` ∈ `X[i, j]` and `X[i, j]` is the set of data points with labels `i` and `j`.

![FIGURE 2.5 One versus One multi-class classification technique: An example of three classes A, B and C in two dimensions.](Images/fig2_5.jpg)

FIGURE 2.5 One versus One multi-class classification technique: An example of three classes A, B and C in two dimensions.

### 2.3.5  Least Squares SVM (1999)

Least Squares SVM (LSSVM, \[127\]) proposes a least squared version of SVM with equality constraints. Due to equality constraints, it solves a set of linear equations to find the solution, unlike standard SVM which solves quadratic programming. In LSSVM, number of support vectors is proportional to number of errors. LSSVM is given by

$$\\begin{array}{l} \\begin{array}{l} {\\underset{w,b,\\xi}{\\min}\\quad\\frac{1}{2}\\| w\\|^{2} + \\frac{C}{2}{\\sum\\limits\_{i = 1}^{l}\\xi\_{i}^{2}},} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.12)

$$\\begin{array}{l} \\begin{array}{l} {\\text{s}.\\text{t}.\\quad\\text{y}\_{\\text{i}}\\left( {\\text{w}^{\\text{T}}\\text{x}\_{\\text{i}}\\text{+b}} \\right)\\text{=1-}\\xi\_{\\text{i}},\\quad\\text{i=1},\\text{2},...,\\text{l}.} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.13)

LSSVM has been extended by \[[80](#bib.xhtml#refbib_80)\] which assigns a degree of importance to each training data point, this idea is similar to Fuzzy SVM \[86\].

### 2.3.6  `ν`-SVM (2000)

`ν`-SVM\[116\] proposes a new SVM formulation for classification and regression problems where a new parameter `ν` is introduced. `ν` roughly controls the fraction of support vectors. In addition to that, `ν` also helps to eliminate one of the other free parameters of the algorithm, `ϵ` (accuracy parameter) in regression and `C` (regularization coefficient) in the classification. Primal formulation for `ν`-SVM is:

$$\\begin{array}{l} \\begin{array}{l} {\\underset{w,b,\\xi,\\rho}{\\min}\\quad\\tau(w,\\xi,\\rho) = \\frac{1}{2}\\| w\\|^{2} - \\nu\\rho + \\frac{1}{l}{\\sum\\limits\_{i}\\xi\_{i}}} \\\\ {\\text{s}\\text{.t}\\text{.}\\quad\\quad y\_{i}\\left( {x\_{i}^{T}w + b} \\right) \\geq \\rho - \\xi\_{i}} \\\\ {\\xi\_{i} \\geq 0,\\quad\\rho \\geq 0,\\quad\\nu \\in \\left\\lbrack {0,1} \\right\\rbrack} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.14)

Dual problem for `ν`-SVM:

$$\\begin{array}{l} \\begin{array}{l} {\\underset{\\alpha}{\\max}\\quad W(\\alpha) = - \\frac{1}{2}{\\sum\\limits\_{ij}\\alpha\_{i}}\\alpha\_{j}y\_{i}y\_{j}x\_{i}^{T}x\_{j}} \\\\ {\\text{s}\\text{.t}\\text{.}\\quad 0 \\leq \\alpha\_{i} \\leq \\frac{1}{l},\\quad 0 = {\\sum\\limits\_{i}\\alpha\_{i}}y\_{i},\\quad{\\sum\\limits\_{i}\\alpha} \\leq \\nu} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.15)

Decision function is:

$$\\begin{array}{l} \\begin{array}{l} {h(x) = sign\\left( {{\\sum\\limits\_{i}\\alpha\_{i}}y\_{i}x^{T}x\_{i} + b} \\right)} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.16)

On comparing with original soft margin dual problem, `ν`-SVM has two differences: Additional constraints and the linear term $\\sum\\limits\_{i}\\alpha\_{i}$ disappears from objective function in eq. (2.15).

### 2.3.7  Smooth SVM (2001)

Smooth SVM\[77\] proposes a new smooth formulation for SVM, to handle its non-differentiability issue. Smooth SVM is a strongly convex and infinitely differentiable. It enjoys globally, quadratically convergent solutions using a fast Newton-Armijo algorithm. It uses Newton's method for obtaining the step direction and Armijo rule for determining the step size.

Suppose there are `l` training points in `n` dimensional space represented by `l` × `n` matrix `A` with membership of each data `A[i]` in classes +1 and -1 is represented by the diagonal `l` × `l` matrix `D` with values +1 or -1 on the diagonal. The standard SVM with some `ν` > 0 and linear Kernel `A`^(*T`)*`A`, is given by

$$\\begin{array}{l} \\begin{array}{l} {\\underset{{({w,\\gamma,y})} \\in {\\mathbb{R}}^{n + 1 + l}}{\\min}\\quad\\nu\\mathbf{1}^{T}y + \\frac{1}{2}\\left\\| w \\right\\|^{2}} \\\\ {\\text{s}\\text{.t}\\text{.}\\quad D\\left( {Aw - \\mathbf{1}\\gamma} \\right) + y \\geq \\mathbf{1},\\quad y \\geq 0} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.17)

where `w`, `γ` are parameters and `y` is the slack variable. The standard SVM is first modified to get the following SVM:

$$\\begin{array}{l} \\begin{array}{l} {\\underset{w,\\gamma,y}{\\min}\\quad\\frac{\\nu}{2}y^{T}y + \\frac{1}{2}\\left( {\\left\\| w \\right\\|^{2} + \\gamma^{2}} \\right)} \\\\ {\\text{s}\\text{.t}\\text{.}\\quad D\\left( {Aw - \\mathbf{1}\\gamma} \\right) + y \\geq \\mathbf{1},\\quad y \\geq 0.} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.18)

From the constraints of problem (2.18), we get,

$$\\begin{array}{l} \\begin{array}{l} {y = \\left( {\\mathbf{1} - D\\left( {Aw - \\mathbf{1}\\gamma} \\right)} \\right)\_{+},} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.19)

where (.)[+] function replaces negative components of a vector with zeros. So, substituting the value of `y` in eq. (2.18), equivalent SVM is obtained as:

$$\\begin{array}{l} \\begin{array}{l} {\\underset{w,\\gamma}{\\min}\\quad\\frac{\\nu}{2}\\|\\left( {\\mathbf{1} - D\\left( {Aw - \\mathbf{1}\\gamma} \\right)} \\right)\_{+}\\|^{2} + \\frac{1}{2}\\left( {\\left\\| w \\right\\|^{2} + \\gamma^{2}} \\right)} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.20)

The objective function of this problem is not twice differentiable so `x`[+] is replaced with a smooth approximation, given by

$$\\begin{array}{l} \\begin{array}{l} {p(x,\\alpha) = x + \\frac{1}{\\alpha}log\\left( {1 + e^{- \\alpha x}} \\right),\\quad\\alpha > 0,} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.21)

where `α` is the smoothing parameter and `e` is the exponential constant. So, using eq. (2.21) in eq. (2.20), it gives the Smooth SVM as:

$$\\begin{array}{l} \\begin{array}{l} {\\underset{w,\\gamma}{\\min}\\,\\frac{\\nu}{2}\\| p\\left( {\\mathbf{1} - D\\left( {Aw - \\mathbf{1}\\gamma} \\right),\\alpha} \\right)\\|^{2} + \\frac{1}{2}\\left( {\\left\\| w \\right\\|^{2} + \\gamma^{2}} \\right)} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.22)

The decision function for Smooth SVM is given by `sign(w`^(*T`)*`x − γ)`.

### 2.3.8  Proximal SVM (2001)

Proximal SVM (PSVM, \[45\]) classifies data points on the basis of proximity to the two parallel planes (called as proximal planes). Standard SVM classifies points using a separating hyperplane which assigns them to one of the half spaces generated by it (separating hyperplane). [Figure 2.6](#03chap_02.xhtml#f2_6). depicts the bounding planes in standard SVM and proximal planes of PSVM. The performance of PSVM on test dataset, is comparable to the standard SVM but its training speed on the training dataset, is considerably faster than the Standard SVM \[45\]. Primal form of PSVM is given by

![FIGURE 2.6 Standard SVM versus Proximal SVM.](Images/fig2_6.jpg)

FIGURE 2.6 Standard SVM versus Proximal SVM.

$$\\begin{array}{l} \\begin{array}{ll} & {\\underset{(w,\\gamma,y)}{\\min}\\quad\\nu\\frac{1}{2}\\| y\\|^{2} + \\frac{1}{2}\\left( {w^{T}w + \\gamma^{2}} \\right)} \\\\ {\\text{s}\\text{.t}\\text{.}} & {D\\left( {Aw - \\mathbf{1}\\gamma} \\right) + y = \\mathbf{1}} \\\\ \\end{array} \\\\ \\end{array}$$  

(2.23)

