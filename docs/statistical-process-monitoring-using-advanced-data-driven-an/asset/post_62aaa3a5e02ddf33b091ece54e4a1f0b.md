
In a similar manner to the conventional PCA, the sample covariance matrix (with its elements are the inner product of all pairs of points \(\Phi(\mathbf{x}_i)\) and \(\Phi(\mathbf{x}_j)\)) in feature space, can be calculated as

$$
\mathbf{\Sigma}_{\mathbb{F}} = \frac{1}{n} \sum_{i=1}^n [\Phi(\mathbf{x}_i) - \mathbf{m}_{\Phi}] [\Phi(\mathbf{x}_i) - \mathbf{m}_{\Phi}]^T, \quad (4.13)
$$

where \(\mathbf{m}_{\Phi} = \sum_{i=1}^n \Phi(\mathbf{x}_i)/n\) is the sample mean in \(\mathfrak{F}\). Let us consider \(\overline{\Phi}(\mathbf{x}_i) = \Phi(\mathbf{x}_i) - \mathbf{m}_{\Phi}\) as the centered nonlinear mapping.

The principal components are found by solving the eigenvalue problem in \(\mathfrak{F}\) as

$$
\lambda \mathbf{v} = \mathbf{\Sigma}_{\mathbb{F}} \mathbf{v} = \frac{1}{n} \sum_{i=1}^n \left[ \overline{\Phi}(\mathbf{x}_i)^T \mathbf{v} \right] \overline{\Phi}(\mathbf{x}_i), \quad (4.14)
$$

where \(\lambda\) is an eigenvalue, \(\lambda > 0\), and \(\mathbf{v}\) is the corresponding eigenvector of the covariance matrix \(\mathbf{\Sigma}_{\mathbb{F}}\). The first PC in \(\mathfrak{F}\), which shows the largest variability in the data, is given along the direction of \(\mathbf{v}\) with the greatest eigenvalue, and the PC indicates the direction of \(\mathbf{v}\) with the lowest eigenvalue.

For nonzero \(\lambda\), \(\mathbf{v}\) could be expressed as a linear combination of \(\alpha_i, i = 1, \dots, n\), thus

$$
\mathbf{v} = \sum_{i=1}^n \alpha_i \overline{\Phi}(\mathbf{x}_i). \quad (4.15)
$$

Multiplying by \(\Phi(\mathbf{x}_j)\) on both sides of Eq. (4.14) gives

$$
\lambda (\Phi(\mathbf{x}_j) \mathbf{v}) = \Phi(\mathbf{x}_j) \mathbf{\Sigma}_{\mathbb{F}} \mathbf{v}. \quad (4.16)
$$

Now, expanding Eq. (4.14), we get

$$
\lambda \sum_{i=1}^n \alpha_i \overline{\Phi}(\mathbf{x}_i) \overline{\Phi}(\mathbf{x}_j) = \frac{1}{n} \sum_{i=1}^n \alpha_i \left( \overline{\Phi}(\mathbf{x}_i) \sum_{i=1}^n \alpha_i \overline{\Phi}(\mathbf{x}_j) \right) \left( \overline{\Phi}(\mathbf{x}_i) \overline{\Phi}(\mathbf{x}_j) \right). \quad (4.17)
$$

It should be noted that the eigenvalue problem in (4.14) can be solved using only scalar products of the mapped vector in \(\mathcal{F}\), and that it can be handled based on a kernel matrix. Therefore, the use of a kernel function can simplify the computational challenges in the higher-dimensional space \(\mathcal{F}\) to computing scalar products of vectors in \(\mathcal{F}\), which highlights the great power of kernel tricks [59].

The kernel function allows determining in an implicit manner the nonlinear mapping in \(\mathfrak{F}\). The kernel matrix \(\mathbf{K} \in \mathbb{R}^{n \times n}\) is expressed as

$$
\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \Phi(\mathbf{x}_i)^T \Phi(\mathbf{x}_j). \quad (4.18)
$$

Then, from Eq. (4.17), we will get

$$
n \lambda \mathbf{K} \boldsymbol{\alpha} = \mathbf{K}^2 \boldsymbol{\alpha}, \quad (4.19)
$$

where \(\boldsymbol{\alpha} = [\alpha_1, \dots, \alpha_n]\). Mean-centering in the feature space is essential before applying KPCA, which is done as follows:

$$
\overline{\mathbf{K}}(\mathbf{x}_i, \mathbf{x}_j) = \overline{\Phi}(\mathbf{x}_i)^T \overline{\Phi}(\mathbf{x}_j), \tag{4.20}
$$

$$
\overline{\mathbf{K}} = \mathbf{K} - \mathbf{K}\mathbf{1}_n - \mathbf{1}_n\mathbf{K} + \mathbf{1}_n\mathbf{K}\mathbf{1}_n, \tag{4.21}
$$

where \(\mathbf{1}_n\) is the following matrix:

$$
\mathbf{1}_n = \frac{1}{n} \begin{pmatrix} 1 & \dots & 1 \\ \vdots & \ddots & \vdots \\ 1 & \dots & 1 \end{pmatrix} \in \mathbb{R}^{n \times n}. \tag{4.22}
$$

To solve the eigenvalue decomposition problem in Eq. (4.19), KPCA now solves the reformed eigenvalue problem of the centered kernel as [29]

$$
n\lambda \boldsymbol{\alpha} = \overline{\mathbf{K}} \boldsymbol{\alpha} \tag{4.23}
$$

for nonzero eigenvalues (\(\lambda \neq 0\)). This is equivalent to applying the conventional PCA in feature space, \(F\). Thereby, performing PCA in \(F\) allows obtaining eigenvectors \(\boldsymbol{\alpha}_1, \dots, \boldsymbol{\alpha}_n\), with \(\lambda_1 \ge \lambda_2 \ge \dots \ge \lambda_n\) as the corresponding eigenvalues.

At last, we can represent the output as

$$
y_j = \sum_{i=1}^n \alpha_{ij}^k \overline{\mathbf{K}}(\mathbf{x}_j, x), \quad j = 1, \dots, d. \tag{4.24}
$$

Generally speaking, the performance of the KPCA-based method mainly depends on the selected kernel functions. Numerous kernels are designed in the literature [60], but, to the best of our knowledge, there is no automated way for kernel selection. In the existing techniques, the selection of a kernel function is usually done empirically or experimentally from an ensemble of candidates. Indeed, inappropriate performance could be achieved in the case of a poor kernel choice [61, 62]. Here are some of the most widely used kernel functions in the machine learning literature:

- Linear kernel,

$$
\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \langle \mathbf{x}_i, \mathbf{x}_j \rangle. \tag{4.25}
$$

- Polynomial kernels,

$$
\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \langle \mathbf{x}_i, \mathbf{x}_j \rangle^d, \quad d \in \mathbb{Z}^+. \tag{4.26}
$$

- Cosine kernels,

$$
\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \frac{\langle \mathbf{x}_i, \mathbf{x}_j \rangle}{\|\mathbf{x}_i\| \|\mathbf{x}_j\|}. \tag{4.27}
$$

- Sigmoid kernels,

$$
\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = \tanh(\beta_0 \langle \mathbf{x}_i, \mathbf{x}_j \rangle + \beta_1).\quad (4.28)
$$

- Radial basis functions (RBF),

$$
\mathbf{K}(\mathbf{x}_i, \mathbf{x}_j) = e^{-\frac{\|\mathbf{x}_i - \mathbf{x}_j\|^2}{2\delta^2}} = e^{-\gamma \|\mathbf{x}_i - \mathbf{x}_j\|^2}, \quad \gamma \in \mathbb{R}^+, \quad (4.29)
$$

where \(2\delta^2 = \frac{1}{\gamma}\) is the width of the Gaussian kernel, while \(d\), \(\beta_0\), and \(\beta_1\) are specified a priori before using the above kernel functions. It should be noted that similar results are obtained by the above kernels if the values of parameters are appropriately selected. The RBF, which is frequently used in fault-detection, offers more flexibility in selecting the associated parameter; it is also assumption-free with respect to relationships among the process variables.

## 4.3.5 KPCA-based fault detection procedures

KPCA monitoring is performed in two broad phases: model development and anomaly detection. The decision statistics (e.g., Hotelling's \(T^2\) and \(Q\)) and their detection thresholds are computed in the offline modeling phase. In the anomaly detection phase, the monitoring statistics are calculated based on the new testing measurements and compared with the previously established decision thresholds to verify the status of the process. An anomaly is flagged if a test statistic is above its detection threshold.

For anomaly-detection purposes, the \(T^2\) and SPE (squared prediction error) monitoring schemes can be computed by testing online measurements. To monitor the variation in the KPCA model, \(T^2\) scheme, which uses normalized squared scores, is employed. Its statistic is computed as

$$
T_f^2 = [t_1, \dots, t_p] \, \Lambda^{-1} [t_1, \dots, t_p]^T, \quad (4.30)
$$

where \(t_k \ (k=1, 2, \dots, p)\) are the retained \(p\) PCs, and \(\Lambda^{-1}\) is the inverse of the matrix of eigenvalues corresponding to the retained PCs.

The detection threshold for \(T^2\) is computed from the \(F\) distribution as

$$
T_\alpha^2 = \frac{p(m-1)}{(m-p)} F_{p, m-p, \alpha}, \quad (4.31)
$$

where \(F_{p, m-p, \alpha}\) is an F-distribution with \(p\) and \(m-p\) degrees of freedom and having a significance level of \(\alpha\).

The variations in the smallest \(m-p\) PCs can be monitored using the \(Q\) statistic. Indeed, the \(Q\) statistic is relevant to indicate the variability not described by the maintained PCs in the KPCA model:

$$
Q_f = \|\Phi(\mathbf{x}) - \Phi_p(\mathbf{x})\|^2 = \sum_{j=1}^m t_j^2 - \sum_{j=1}^p t_j^2. \quad (4.32)
$$
