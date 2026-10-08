![](bbox=[0.2385, 0.1835, 0.7615, 0.2835])

(a)

(b)

(c)

![](bbox=[0.2385, 0.3235, 0.7615, 0.4235])

(d)

(e)

(f)

Figure 4.6: Classification using different features.

class means

$\mu = \frac{1}{K} \sum_{i=1}^{K} \mu_i.$

The **between-class scatter** is defined as

$\Sigma_b = \frac{1}{K} \sum_{i=1}^{K} (\mu_i - \bar{\mu})(\mu_i - \bar{\mu})^T$

The separation between classes in the direction of **w** is given

$\s(\mathbf{w}) = \frac{\mathbf{w}^T \Sigma_b \mathbf{w}}{\mathbf{w}^T \Sigma_w \mathbf{w}}$

To separate $K$ classes we need to find directions $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ for which $s(\mathbf{w})$ is maximal. This is equivalent to maximizing

$\mathbf{S}(\mathbf{W}) = \frac{[\mathbf{W}^T \Sigma_b \mathbf{W}]}{[\mathbf{W}^T \Sigma_w \mathbf{W}]}$

where $\mathbf{W}$ denotes the matrix whose columns are the vectors $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ and $|\cdot|$ denotes the determinant of the matrix. If the number of features $M$ is greater or equal to the number of classes $K$, it can be shown that $S(\mathbf{W})$ is maximal if $\mathbf{w}_1, \dots, \mathbf{w}_{K-1}$ are the generalized eigenvectors corresponding to the $K-1$ largest generalized eigenvalues of the generalized eigenvalue problem

$\Sigma_B \mathbf{w} = \lambda \Sigma_W \mathbf{w}.$