
$\\begin{array}{crrrr} {|{3}} & 1 & {1|} & {|11} & {1|} \\\\ {|{- 1}} & 3 & {1|} & {|{1}} & {11|} \\\\ \\end{array}$

![Equation](Images/F000084si94.png)

As usual, the characteristic equation when solved will render the eigenvalues. Taking `det(AA' − λ I)` and setting this quantity equal to zero gives the following characteristic equation: `λ² –22λ + 120=0`. Therefore, the eigenvalues are `λ[1]`\=12 and `λ[2]`\=10. The corresponding eigenvectors are `v[1]`\=(a b)′ and `v[2]`\=(c d)′. For the larger eigenvalue, `[AA' –12·I]` `v[1]`\=0; this shows that `a`=`b`. Using the fact that all eigenvectors must be normalized `a² + b²`\=1 shows that `v[1]` = (1/2^(1/2)1/2^(1/2))’![Equation](Images/F000084si95.png). In a similar fashion, the second eigenvector is `v[2]` = (1/2^(1/2)−1/2^(1/2))’![Equation](Images/F000084si96.png). Observe that these eigenvectors are orthogonal. Since the eigenvalue `λ[1]`![Equation](Images/F000084si97.png) is the largest, the matrix for `U` is found using as columns `v[1]`![Equation](Images/F000084si98.png) followed by `v[2]`![Equation](Images/F000084si99.png). So, 2^(1/2)![Equation](Images/F000084si100.png) `U`=
$\\begin{matrix} {|1} & {1|} \\\\ {|1} & {{- 1}|} \\\\ \\end{matrix}.$
![Equation](Images/F000084si101.png)

In order to find `V`, the eigenvalues and the eigenvectors must be determined for `A′A`, which is:
$\\begin{matrix} {|10} & 0 & {2|} \\\\ {|{0}} & 10 & {4|} \\\\ {|{2}} & 4 & {2|} \\\\ \\end{matrix}$
![Equation](Images/F000084si102.png)
Like before, the characteristic equation, `det(A′A−λ I)=0`, has as solutions the eigenvalues. To find this equation, consider the determinant:
$\\begin{matrix} {|{10 - \\lambda}} & 0 & {{ 2}|} & {10 - \\lambda} & 0 \\\\ {|{ 0\\mspace{23mu}}} & {10 - \\lambda} & {{ 4}|} & 0 & {10 - \\lambda} \\\\ {|{ 2\\mspace{23mu}}} & 4 & {{2 - \\lambda}|} & 2 & 4 \\\\ \\end{matrix}$
![Equation](Images/F000084si103.png)
Multiply elements on minus 45° on all three angles and add them together to obtain sum1. Next, multiply elements on plus 45° and then add them together to obtain sum2. Finally subtract sum2 from sum1, and this is the determinant. Evaluating the determinant (10 −`λ`)(10−`λ`)(2 −`λ`)−4(10 −`λ`)−16(10−`λ`)=0, Accordingly (10 −`λ`) \[(10−`λ`)(2 −`λ`)−20\]=0=(10−`λ`) \[`λ`²–12 `λ`\]=0. It follows that the eigenvalues are `λ[1]`\=12, `λ[2]`\=10, and finally, `λ[3]`\=0. The corresponding eigenvectors are found as before by taking (`A′A−λ I`) v)=0. For `v[1]`\=(a b c)′, set the following equal to zero:
$\\begin{array}{llll} {10 - \\lambda\_{1}} & { 0} & {{ 2}|} & {|a|} \\\\ {|0} & {10 - \\lambda\_{1}} & {{4|} \\cdot} & {{|b|} = 0} \\\\ {|2} & 4 & {{2 - \\lambda\_{1}}|} & {|c|} \\\\ \\end{array}$
![Equation](Images/F000084si104.png)
This gives −2 a + 2 c=0, −2 b + 4 c=0, and 2 a.+ 4 b + 2 c=0; the solution is a=1, b=2, and c=1. Next, normalizing gives the eigenvector `v[1]` = 1/6^(1/2)![Equation](Images/F000084si105.png) (1 2 1)′. In a similar manner, using `λ[2]`\=10 in the aforementioned matrix instead of `λ[1]`![Equation](Images/F000084si106.png) results in the corresponding normalized eigenvector `v[2]` = 1/5^(1/2)![Equation](Images/F000084si107.png) (2 –1 0)′. Lastly, using the third eigenvalue leads to the final eigenvector `v[3]` = 1/30^(1/2)![Equation](Images/F000084si108.png) (1 2 –5)′. Notice that all these eigenvectors are mutually orthogonal. The three eigenvectors now become the columns 1, 2, and 3, in the order given to form the orthogonal matrix `V`. The transpose of this matrix is needed; therefore `V′`=
$\\begin{array}{lll} {|{1/6}^{1/2}} & {2/6}^{1/2} & {{{ 1}/6}^{1/2}|} \\\\ {|{2/5}^{1/2}} & {{- 1}/5}^{1/2} & {{}0|} \\\\ {|{1/30}^{1/2}} & {2/30}^{1/2} & {{{- 5}/30}^{1/2}|} \\\\ \\end{array}$
![Equation](Images/F000084si109.png)
The only matrix left to find is `D`. It consists of the square root of the nonzero eigenvalues on the main diagonal, that is, starting on the top left corner and along a minus forty-five degree line. The square roots of these eigenvalues from largest to smallest populate this line. The only other thing is that `A`=`U D V′`; the dimensions must agree. Since the matrix dimensions are for `A`, two by three; for `U`, two by two; for `D`, two by two; and finally for `V′`, three by three, accordingly a row or column of zeros is needed to make the dimensions hold. Thus, in this example, an extra column of zeros is needed in the SVD, so `D`=
$\\begin{array}{lll} {|12^{1/2}} & 0 & {0|} \\\\ {|{0.}} & 10^{1/2} & {{0|}.} \\\\ \\end{array}$
![Equation](Images/F000084si110.png)
This is the singular value decomposition for `A`. The columns of `U` are the left singular vectors, and the columns of `V` are called the right singular vectors.

A final word on the SVD is that it provides an interesting geometric interpretation when operating on a vector x. Let `A`=`U D V′`, an m by n vector. A major assumption will be that `U` and `V` are in the special orthogonal Lie group `SO(m, R)` and `SO(n, R)`, respectively. Therefore, they represent rotation matrices; their determinants are equal to one. In this case, first when `U` is applied to x, a rotation of x occurs. Let `U(x)=y`. Next, when `D` operates on y, if `D` is a scalar matrix, then `D` enlarges or shrinks y and changes the dimension. Otherwise, it enlarges certain tuples within y, compresses other tuples within y, and changes the dimension. Use `D(y)=z`. Finally, `V∗` applies a rotation to z, yielding w. Accordingly, `V∗(z)=w`. A most interesting case is when n=m=2. Illustrations of the procedure can graphically be provided in this situation.

## References
* [Hollings and Lawson, 2017](#Ch005_83-101_B9780443136979000084.xhtml#BIB_1) Hollings C, Lawson M. *Wagner’s Theory of Generalized Heaps* Springer books 2017;.
* Horn and Johnson, 1991 Horn R, Johnson C. 978-0521-46713-1 *Topics in Matrix Anylysis* Cambridge U. Press 1991;.
* [Hornegger, 2021.](#Ch005_83-101_B9780443136979000084.xhtml#BIB_3) Hornegger, H., 2021. Pattern Recognition Lab, Lecture Pattern Recognition.
* [Hotelling, 1933](#Ch005_83-101_B9780443136979000084.xhtml#BIB_4) Hotelling H. Analysis of a complex of statistical variables into principal components. *J Educa Psychol.* 1933;24(6):417–441.
* [Loeve, 1977](#Ch005_83-101_B9780443136979000084.xhtml#BIB_5) Loeve M. GTM *Probability*. vol. 45 Springer 1977;.
* [Marsden, 2003](#Ch005_83-101_B9780443136979000084.xhtml#BIB_6) Marsden. *Differential Forms and STOKES Theorem* Caltech 2003;.
* [Pearson, 1901](#Ch005_83-101_B9780443136979000084.xhtml#BIB_7) Pearson, 1901. On lines and planes of closes fit to systems of points in space. Philosophical Magazine.
* [Scholkopf et al., 1999](#Ch005_83-101_B9780443136979000084.xhtml#BIB_8) Scholkopf, et al. *Kernel principal component analysis*. *Advances in Kernel Methods-support Vector Learning* MIT Press 1999;.
* [Stewart, 1992](#Ch005_83-101_B9780443136979000084.xhtml#BIB_9) Stewart, G., 1992. On the early history of the singular value decomposition, IMA o reorient # 952.
* [Thompson, 2014](#Ch005_83-101_B9780443136979000084.xhtml#BIB_10) Thompson, D., 2014. Nonlinear Dimensionality Reduction KPCA, JPL-Caltech Virtual Summer School Big Data Analytics.
* [Yano, 1957](#Ch005_83-101_B9780443136979000084.xhtml#BIB_11) Yano, K., 1957. The theory of Lie derivatives and its applications, North=-Holland, 978-0-7204-2104-0.
* [Zubelevich, 2012](#Ch005_83-101_B9780443136979000084.xhtml#BIB_12) Zubelevich O. *Elementary Proof of the Cartan Magic Formula* University of Texas 2012;.

# Chapter 6

# Quantum annealing and adiabatic quantum computing

## Abstract
