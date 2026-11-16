

## 2.2.2.1 Principal component analysis

### Feature extraction with PCA

PCA, a dimensionality-reduction approach, is an increasingly popular modeling framework for discovering relevant and crucial features from multivariate data. The foundation of PCA can be tracked back to Pearson (1901) [24] and Hotelling (1933) [25]. By projecting process variables into a lower-dimensional subspace, PCA reveals the inherent cross-correlation among process variables [26]. In this regard, PCA latent variables or principal components (PCs) (also called scores), which consist of linear combinations of physical variables, can efficiently describe a process in a reduced subspace. PCA-based methods are currently more commonly applied in data compression [27], pattern recognition, data smoothing, classification [28], and fault detection [29].

PCA does not differentiate between input data X and output data Y. It is applied to one data set that contains all the process variables involved in the problem. Here, X is used to represent the whole data set. Let X = [x_1^T, ..., x_n^T]^T \in R^{n x m} be a dataset gathered from a process having n observations and m variables.

Let us first discuss an important point before going into any further in detail. When performing PCA on multivariate data, it is assumed that all the data are on a comparable scale. If scaling of the data is omitted, then certain variables in the data have to be adjusted to avoid the occurrence of misleading dominance. Scaling of data changes the covariance matrix and consequently affects the principal components. Scaling is important for both the variance and mean adjustments [30]. When the process variables are measured with different units, the purpose of the usual scaling is to make the variance the same (i.e., to give standard units), which gives a correlation matrix. Other variance-stabilizing transformations, such as log transformation, are used in the literature. The most commonly used scaling converts the variables to zero mean and unit variance. Each variable x_j \in R^n, j = 1, ..., m, should be scaled to have zero mean and unit variance prior to using PCA:

```
$$x_{j,s} = \frac{x_j - \mu_{x_j}}{\sigma_{x_j}}$$ (2.9)
```

From now on, we consider that autoscaled data is zero-mean centered with unit variance,

![](img/aa2f42c739937b682075082233e335bb_35_0.png)

The scaled data **X** can be expressed using singular value decomposition (SVD) as a product of two factors:

X = t_1 w_1^T + t_2 w_2^T + \cdots + t_m w_m^T = T W^T , \quad (2.10)

where T ∈ R^{n×m} represents a matrix of the principal components (PCs) and W ∈ R^{m×m} is the loading matrix. The PCs are linear combinations of the original data, and each PC is not correlated with the others. The loading matrix is frequently calculated through SVD of the covariance matrix S of the data X:

S = \frac{1}{n-1} X^T X = W \Lambda W^T \quad \text{with} \quad W W^T = W^T W = I_n , \quad (2.11)

where, Λ = diag(σ_1^2, ..., σ_m^2) is a matrix comprising eigenvalues of S arranged diagonally in decreasing magnitude. The eigenvalues λ_i are equal to the variance of the PC t_i, σ_i^2 (i.e., var(w_i^T X) = λ_i).

In the presence of cross-correlated multivariate data, X, the first l PCs (where k < m) are sufficient for preserving relevant information in the original data. One important step in PCA model development is to select the number of PCs.

### Criteria for selecting the number of principal components to use

A core step in designing LVR approaches is selecting by the number of LVs, l, to appropriately extract relevant information from the received data. In other words, the prediction performance of the designed LVR model is influenced by the choice of the number of LVs, l. Accordingly, an appropriate estimation of the number of LVs is necessary to avoid the problem of the model underfitting or overfitting the data. Some of these techniques are briefed below:

- **The scree test.** The scree plot displays the variance caught by every PC against the number of the PCs [31]. Then, the number of PCs to retain are obtained by finding the value of the eigenvalue λ corresponding to the profile with an elbow shape (i.e., the profile is no longer linear). This identification procedure is easy to visualize but it could be not easy for automatic implementation.

- **Parallel analysis.** Parallel analysis compares the variance profile to that obtained by assuming independent variables, to determine the number of PCs. Specifically, l is determined at the point where the two profiles cross [31, 32].

- **The cumulative percentage variance (CPV) procedure.** The CPV procedure has been commonly employed to find the number of PCs explaining a certain percentage of the total variance (e.g., 90%) [31]:

\( CPV(l) = \frac{\sum_{i=1}^l \lambda_i}{\sum_{i=1}^m \lambda_i} \times 100. \) (2.12)

This procedure is attractive since it is intuitive and easy to implement [31].

- **Cross-validation.** Basically, the key concept of the cross-validation mechanism is splitting the data in training datasets for model construction and testing datasets for model validation [33]. The model is verified using the test data, and residuals are generated by comparing the estimated values to the measured values. In the CV approach, the optimum number of PCs is determined by using Predictive Sum of Squares (PRESS) statistics [33],

\( PRESS_l = \sum_{i=1}^n (X_i - \hat{X}_i^l)^2, \) (2.13)

where \( l \) is the number of PCs vectors retained to calculate \( \hat{X} \), i.e., the dimension of the PCs. The dimensionality is determined by finding the number of PCs corresponding to the minimum of the PRESS [33].

Based on the PCA model, after selecting the appropriate number of PCs to include in the model, the data matrix **X** can be expressed as a sum of the approximated matrix, \( \widehat{\mathbf{X}} \), and residual data, **E** (Fig. 2.1),

\( \mathbf{X} = \mathbf{T}\mathbf{W}^T = \sum_{i=1}^k t_i w_i^T + \sum_{i=k+1}^m t_i w_i^T = \widehat{\mathbf{X}} + \mathbf{E}, \) (2.14)

where \( \mathbf{T} \in \mathbb{R}^{n \times m} \) represents a matrix of the principal components (PCs) and \( \mathbf{W} \in \mathbb{R}^{m \times m} \) is the loading matrix.

![](img/aa2f42c739937b682075082233e335bb_36_0.png)

**FIGURE 2.1 Schematic representation of PCA model.**

As described above, the orthogonal eigenvectors of the covariance matrix are equal to the loading matrix **W** = (**w**₁, **w**₂, ..., **w**ₘ), and eigenvalue λᵢ is the variance of score tᵢ. The loading matrix can be partitioned into two parts, \(\widehat{\mathbf{W}}\) and \(\widetilde{\mathbf{W}}\), i.e., **W** = [\(\widehat{\mathbf{W}}\) \(\widetilde{\mathbf{W}}\)]. Here \(\widehat{\mathbf{W}} = (\mathbf{w}_1, \mathbf{w}_2, ..., \mathbf{w}_l)\), represents the first l principal loading vectors (PCs) and \(\widetilde{\mathbf{W}} = (\mathbf{w}_{l+1}, \mathbf{w}_{l+2}, ..., \mathbf{w}_m)\) represents the remaining m − l PCs. The partition is shown below:

```
S = \frac{1}{n-1} \mathbf{X}^T \mathbf{X} = \left( \widehat{\mathbf{W}} \quad \widetilde{\mathbf{W}} \right) \left( \begin{array}{cc} \widehat{\Lambda} & 0 \\ 0 & \widetilde{\Lambda} \end{array} \right) \left( \begin{array}{c} \widehat{\mathbf{W}}^T \\ \widetilde{\mathbf{W}}^T \end{array} \right).
```

The data matrix **X** can be factorized as

```
\overline{\mathbf{X}} = \overbrace{[\widehat{\mathbf{T}} | \widetilde{\mathbf{T}}] [\widehat{\mathbf{W}} | \widetilde{\mathbf{W}}]^T}^{\mathbf{T} \mathbf{W}^T} = \widehat{\mathbf{T}}\widehat{\mathbf{W}}^T + \widetilde{\mathbf{T}}\widetilde{\mathbf{W}}^T = \overbrace{\widehat{\mathbf{X}} \widehat{\mathbf{W}} \widehat{\mathbf{W}}^T}^{\widehat{\mathbf{X}}} + \overline{\mathbf{X}} \left( \mathbf{I}_m - \widehat{\mathbf{W}} \widehat{\mathbf{W}}^T \right).
```

Here \(\widehat{\mathbf{T}} \in \mathbb{R}^{n \times l}\) is the PC matrix (\(n \times l\)), which describes the values of variables in the transformed (\(n \times l\)) basic space spanned by \(\widehat{\mathbf{W}}\), while \(l\) is chosen to capture most of the variability in the data, and no relevant information is lost in \(\mathbf{E}\). The matrices \(\widetilde{\mathbf{W}}\widetilde{\mathbf{W}}^T\) and \((\mathbf{I}_m - \widetilde{\mathbf{W}}\widetilde{\mathbf{W}}^T)\) span the principal component and residual subspaces, respectively. The row vectors in \(\overline{\mathbf{X}}\) and \(\mathbf{E}\) are orthogonal, i.e., \(\overline{\mathbf{X}}^T \mathbf{E} = \mathbf{0}\).

The residual matrix plays a core role in uncovering abnormal features in process monitoring. For the purpose of anomaly detection, we will evaluate the generated residuals based on the developed PCA reference model by univariate or multivariate statistical monitoring schemes. More details on process monitoring are given in the subsequent sections.

## 2.2.2.2 Principal component regression

PCR is an alternative to OLS regression for addressing the issue of ill-conditioning or collinearity in multivariate linear regression, which results in a poor estimation of the model parameters. PCR is a linear regression approach that can handle highly correlated process variables by latent variables as regressors in the regression. It can be implemented in two steps. The first step in PCR consists of projecting the input variables via PCA to account for collinearity and reduce their dimensions. To this end, SVD is frequently employed to compute the PCs. In the second step, OLS regression is conducted between the retained PCs and the response [14, 11] (Fig. 2.2).

To sum up, the key idea of PCR is to use uncorrelated l score vectors from the PCA instead of the l columns in **X**. Specifically, the multicollinearity among the predictor variables can be eliminated by using a subset of orthogonal PCs from the input data **X** via PCA. Then, OLS is performed between the response variable **Y** and the retained l PCs of **X**. From the PCA model, the matrix **X** can

