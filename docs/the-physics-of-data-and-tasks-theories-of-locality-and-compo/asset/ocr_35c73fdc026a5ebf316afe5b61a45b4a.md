# A.3 MERCER'S DECOMPOSITION OF CONVOLUTIONAL AND LOCAL KERNELS 153

Finally, we prove the expansion of Equation 37 from the definition of $\mathcal{K}^{CN}$,

```
$\mathcal{K}^{CN}(x,y) = \frac{s^2}{d^2} \sum_{i,j \in P} C(x_i, y_j) \quad (124)$
= \frac{s^2}{d^2} \sum_{i,j \in P} \Lambda_{ij} \phi_p(x_i)\phi_p(y_j)\n= \lambda_1 \frac{s^2}{d} \sum_{i \in P} \phi_1(x_i)\phi_1(y_j)\n+ \sum_{\rho > 1} \lambda_{ho} \left( \sqrt{\frac{s}{d}} \sum_{i \in P} \Phi_{ho}(x_i) \right) \left( \sqrt{\frac{s}{d}} \sum_{j \in P} \Phi_{ho}(y_j) \right)\n= \sum_{\rho} \Lambda_{ho} \Phi_{ho}(x)\Phi_{ho}(y).$.
```

PROOF OF LEMMA 2.3-4

Proof. We start again by proving the orthonormality of the $d$-dimensional eigenfunctions $\Phi_{ho,j}$ in terms of the $s$-dimensional eigenfunctions $\phi_{ho}$ of the constituent kernel as Equation 40, for $ho, \sigma \neq 1$,

```
$\Phi_{ho,i}(x), \Phi_{\sigma,j}(y) = \int p(d^dx)\Phi_{ho,i}(x)\Phi_{\sigma,j}(y) = \delta_{ho,\sigma}\delta_{i,j}, \quad (125)$
```

from the orthonormality of the eigenfunctions $\Phi_{ho}$ when $i=j$ and assumption $i$, if $\int p(s^sy)p(d^dx)\phi_{ho}(x)=0$ for all $\rho > 1$, when $i \neq j$. Moreover, if $\Phi_1(x)=1, \int p(d^dx)\Phi_{\sigma,i}(x)=0$ and $\int p(d^dx)\Phi_1(x)\Phi_1(x)=1$. Then, we prove that the eigenfunctions and the eigenvalues defined in Equation 40 satisfy the kernel eigenproblem. For $\rho=1$,

```
$\int p(d^dx)\mathcal{K}^{LC}(x,y) = \int p(d^dy)\sum_{i \in P} \frac{s}{d} \lambda_1 = \frac{s}{d} \sum_{i \in P} \lambda_1 = \Lambda_1, \quad (126)$
```

where we used $\int p(s^sy)C(x,y)=\lambda1$, from assumption $i$. For $\rho > 1$,

```
$\int p(d^dx)\mathcal{K}^{LC}(x,y)\Phi_{ho}(y) = \int p(d^dy)\sum_{j \in P} \frac{s}{d} C(x_j,y_j)\Phi_{ho}(y_j). \quad (127)$
```

Splitting the sum over $j$ in the term for which $j=i$ and the remaining ones, the RHS can be written as

```
$\frac{s}{d} \int p(d^dy_i)C(x_i,y_i)\Phi_{ho}(y_i) + \frac{s}{d} \sum_{j \neq i \in P} \int p(d^dy_j)C(x_j,y_j)\Phi_{ho}(y_j). \quad (128)$
```