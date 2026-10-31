
Lie derivatives do not change the degree of the forms they act on. Another way of keeping the degree of the form invariant is to use both the interior and exterior operators since the former lowers the degree, while the latter raises the degree. The order of operation matters, and in any case, Cartan magic formula is an illustration of keeping the degree of the form invariant ([Marsden, 2003](#Ch005_83-101_B9780443136979000084.xhtml#bib5)).

For regular functions `f`, that is, 0 forms, both the exterior and Lie derivatives agree. However, the meaning of derivative is somewhat different for these two operators. A Lie derivative provides a rate of flow or change in a zero form, whereas the exterior derivative can be viewed as the inverse operation of integration ([Yano, 1957](#Ch005_83-101_B9780443136979000084.xhtml#bib10)).

## 5.5 矩阵的谱与 Frobenius 协变矩阵

In finite-dimensional Hilbert spaces `H`, the spectral characteristics of operators `T` are realized by matrices `M`. In particular, the spectral decomposition will be described for matrices with distinct eigenvalues. It involves a superposition of pairwise orthogonal projections onto the eigenspace `Va`, for eigenvalue `a`. So, `Va={a such that T v=a v, v nonzero in H}`.

Let `Pa` be an orthogonal projection onto `Va`. When `a1`, `a2`,…, `an` are the distinct eigenvalues of `T`, the spectral decomposition of `T` is `T=a1 Pa1+ a2 Pa2 +…+ an Pn`. Also, `T²\=a1² Pa1 + a2² Pa2 +…+ an² Pan`. This follows since `Paj` and `Pak` are orthogonal and projections are idempotent. Moreover, for any polynomial involving `T`, `p (T)=p (a1) Pa1 + p(a2) Pa2 +…+ p(an) Pan`. The functional calculus, indicated in later chapters, extends the decomposition from polynomials to continuous functions `f`. One of the most important formulas for functions of a matrix is given next.

The Lagrange-Sylvester interpolation formula is described for a matrix `A`, over the complex field. It is assumed that `A` is a `k` by `k` matrix with distinct eigenvalues. The objective is to find the function `f` of a matrix `A`, that is, `f (A)`. The value `f (A)` is the sum $\\sum\_{i = 1}^{k}{f\\left( {ai} \\right){Ai}}$![Equation](`Images/F000084si60.png`). In this sum, there appears the product of `f (ai)`, for distinct eigenvalues `ai` of `A`. This quantity multiplies the Frobenius covariants `Ai` ([Horn and Johnson, 1991](#Ch005_83-101_B9780443136979000084.xhtml#bib2)). Each of the `k` covariants `Ai` is found as a product `j=1` to `k` but `j` not equal to `i` of the quotient `(A−aj I)/(ai−aj)`.

### 示例 5.11

As an instance of this formula, consider `k=2` by 2 matrix `A`,

$\\begin{matrix} {|2} & {1|} \\\\ {|3} & {4|} \\\\ \\end{matrix}$

![Equation](`Images/F000084si61.png`)

The characteristic equation is `(2−*λ*) (4−*λ*)−3=*λ*²–6 *λ* + 5=0`. Then, the distinct eigenvalues are `a1=5` and `a2=1`. In this order, we will find the Frobenius covariants `A1` and `A2`. Since `k=2`, the product will only have one term for each Frobenius covariant. Thus for `A1`, `j` only will equal 2, and therefore `A1=(1/4)(A−I)`. In a similar fashion, for `A2`, `j` only equals 1, and consequently, `A2=−(1/4) (A−5I)`. These Frobenius covariants need to be calculated only once. From this, functions of `A` are found using `f (A)=f (5) A1 + f (1) A2`. This can be done for `f (A)` equal to *e*^(*A*)![Equation](`Images/F000084si62.png`), `sin (A)`, `cosh (A)`, and so on. As a simple check, `f (A)=A` will first be found. It is `5 A1–1 A2`. The corresponding Frobenius covariants are `4 A1` and `4 A2` given as follows in that order:

$\\begin{matrix} \\begin{matrix} {|\\begin{matrix} 1 & 1 \\\\ \\end{matrix}|} \\\\ {|\\begin{matrix} 3 & 3 \\\\ \\end{matrix}|} \\\\ \\end{matrix} & \\begin{matrix} {|\\begin{matrix} {- 3} & 1 \\\\ \\end{matrix}|} \\\\ {|\\begin{matrix} 3 & {- 1} \\\\ \\end{matrix}|} \\\\ \\end{matrix} \\\\ \\end{matrix}$

![Equation](`Images/F000084si63.png`)

Multiplying the first matrix above by `5/4` and the second matrix above by `−1/4` and adding them together sums to `A`.

As another simple example, *A*²![Equation](`Images/F000084si64.png`) will be found. It is `25 A1–1 A2=` $\\begin{array}{rrl} {\\left( {25/4} \\right){|{1 1}|}} & {- \\left( {1/4} \\right){|{- 3 1}|}} & {= \\ {|{7\\mspace{34mu} 6}|}} \\\\ {|{3 3}|} & {|{3 - 1}|} & {{|{18\\mspace{15mu} 19}|}.\\#} \\\\ \\end{array}$

![Equation](`Images/F000084si65.png`)

A similar formula involving the Frobenius covariants exists for the situation where there exists repeated eigenvalues ([Horn and Johnson, 1991](#Ch005_83-101_B9780443136979000084.xhtml#bib2)).

## 5.6 主成分分析

The Karhunen-Loeve transform (`KLT`), the Hotelling transform, and the principal component analysis (`PCA`) are different names for essentially the same transform method. In machine learning, the terminology is usually referred to as the `PCA`. It is a linear feature reduction technique, and it is often called an unsupervised decomposition algorithm. Being unsupervised, like the `k means` method illustrated in Example 2.1, [第 2.1 节](#Ch002_21-40_B9780443136979000266.xhtml#f0010), suggests that it needs an exhausting amount of computation in all applications. This is true. In general, `PCA` is a method for finding the vectors of greatest influence and then reducing the dimension of the data set by removing data related to less influential vectors. `PCA` is called an eigenproblem. The actual solution is centered about finding eigenvectors `v[j]`![Equation](`Images/F000084si66.png`) and their eigenvalues `λ[j]`![Equation](`Images/F000084si67.png`). All eigenvectors with the largest absolute value eigenvalues `λ[j]`![Equation](`Images/F000084si68.png`) are usually retained. Then, the method is to reduce the dimensionality of data by removing eigenvectors possessing small absolute valued eigenvalues. Actually, this is a form of data compression, also called source coding. From a statistical point of view, the `PCA` method is a method for determining the direction that maximizes the variance or correlation of the data.

The `PCA` was invented by [Pearson (1901)](#Ch005_83-101_B9780443136979000084.xhtml#bib6). Early on, the Hotelling transform was used in probability and statistics applications ([Hotelling, 1933](#Ch005_83-101_B9780443136979000084.xhtml#bib12)). Additionally, along with stochastic processes, the `KLT` ([Loeve, 1977](#Ch005_83-101_B9780443136979000084.xhtml#bib4)) found applications in engineering applications.

The reason for using eigenvectors is because they provide directions of principle components. Principal components are always orthogonal to each other, and intuitively they form orthogonal axes. The eigenvalues represent the units of spread captured by each principal components. The `PCA` does not just discard original data; it maps the data into a new feature space. It is in this space that the reduction is performed. As mentioned before, `PCA` is mainly used in dimension reduction, but it is sometimes used for data visualization as well as feature extraction. The algorithm helps identify variables that are dependent and remove them. That is, multicollinearity is identified and dealt with using `PCA`. `PCA` reduces the dimension set, but does not reduce much of the information content when components are discarded.
