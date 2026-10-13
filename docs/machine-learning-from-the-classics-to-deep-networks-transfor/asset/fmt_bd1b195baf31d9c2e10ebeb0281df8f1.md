
## 5. – *P̃*[*n*] = *β*^(−1)*P̃*[*n*−1] − *β*^(−1)**k**[*n*]**z**[*n*]^(*H*)

*   •  **End For**

Setting **v**[*n*] = 0 and replacing ${\\widetilde{\\mathbf{x}}}\_{n}$ with **x**[*n*] and **φ**[*n*] with **θ**[*n*], the linear complex-valued RLS results.

## 6.10 Computational aspects of the LS solution

The literature concerning the efficient solution of the LS method as well as the computationally efficient implementation of the RLS is huge. In this section, we will only highlight some of the basic directions that have been followed over the years. Most of the available software packages implement such efficient schemes.

A major direction in developing various algorithmic schemes was to cope with the numerical stability issues, as we have already discussed in [Remarks 6.2](#Chp006_249-291_B9780443292385000123.xhtml#enun0025). The main concern is to guarantee the symmetry and positive definiteness of *Φ*[*n*]. The path followed toward this end is to work with the square root factors of *Φ*[*n*].

### Cholesky factorization

It is known from linear algebra that every positive definite symmetric matrix, such as *Φ*[*n*], accepts the following factorization:

*Φ*[*n*] = *L*[*n*]*L*[*n*]^(*T*)

where *L*[*n*] is lower triangular with positive entries along its diagonal. Moreover, this factorization is unique.

Concerning the LS task, one focuses on updating the factor *L*[*n*], instead of *Φ*[*n*], in order to improve numerical stability. Computation of the Cholesky factors can be achieved via a modified version of the Gauss elimination scheme [22].

### *QR* factorization

A better option for computing square factors of a matrix, from a numerical stability point of view, is via the *QR* decomposition method. To simplify the discussion, let us consider *β* = 1 and *λ* = 0 (no regularization). Then the positive definite (sample) covariance matrix can be factored as

*Φ*[*n*] = *U*[*n*]^(*T*)*U*[*n*].

From linear algebra [22], we know that the (*n* + 1) × *l* matrix *U*[*n*] can be written as a product

*U*[*n*] = *Q*[*n*]*R*[*n*],
