
$L(\mathbf{\theta}_{1},\ldots,\mathbf{\theta}_{M}) = - \sum\limits_{n = 1}^{N}\sum\limits_{m = 1}^{M}y_{nm}\ln\phi_{nm},$

which is the generalization of the cross-entropy cost function for the case of *M* classes. Minimization with respect to **θ**[*m*], *m* = 1, …, *M*, takes place iteratively. To this end, the following gradients are used (Problems [7.10](#Chp007_293-342_B9780443292385000135.xhtml#o0055)–[7.12](#Chp007_293-342_B9780443292385000135.xhtml#o0065)):

$\frac{\partial\phi_{nm}}{\partial t_{j}} = \phi_{nm}(\delta_{mj} - \phi_{nj}),$

where *δ*[*m**j*] is one if *m* = *j* and zero otherwise. Also,

$\nabla_{\mathbf{\theta}_{j}}L(\mathbf{\theta}_{1},\ldots,\mathbf{\theta}_{M}) = \sum\limits_{n = 1}^{N}(\phi_{nj} - y_{nj})\mathbf{x}_{n}.$

The respective Hessian matrix is an (*lM*) × (*lM*) matrix, comprising *l* × *l* blocks. Its (*k*, *j*) block element is given by
