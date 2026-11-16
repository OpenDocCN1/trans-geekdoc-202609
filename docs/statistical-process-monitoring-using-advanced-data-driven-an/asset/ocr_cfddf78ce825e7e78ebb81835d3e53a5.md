power production in wind turbines from measurements of various meteorological conditions (wind direction, wind speed, etc.). In PLS, the input and output matrices, \(\mathbf{X} \in \mathbb{R}^{n \times m}\) and \(\mathbf{Y} \in \mathbb{R}^{n \times p}\), are expressed as follows [31,32]:

```
\(\begin{cases} \mathbf{X} = \sum_{i=1}^l \mathbf{tp}_i^T = \mathbf{T}\mathbf{P}^T + \mathbf{G}, \\ \mathbf{Y} = \sum_{i=1}^l \mathbf{uq}_i^T = \mathbf{U}\mathbf{Q}^T + \mathbf{F}, \end{cases}\)
```

where matrices \(\mathbf{T} \in \mathbb{R}^{n \times l}\) and \(\mathbf{U} \in \mathbb{R}^{n \times q}\) contain the retained principal components (latent variables) of the input and output data, respectively, matrices \(\mathbf{P} \in \mathbb{R}^{m \times l}\) and \(\mathbf{Q} \in \mathbb{R}^{p \times q}\) contain the input and output loading vectors, respectively, and matrices \(\mathbf{G}\) and \(\mathbf{F}\) are the input and output residual matrices, respectively. The model in Eq. (4.1) is usually called the "outer model". The representation of the input and output matrices (shown in the outer model (4.1)) is determined by maximizing the covariance between the input and output latent variables, i.e., \(\mathbf{T}\) and \(\mathbf{U}\). Then, the model relating the input and output principal components (called inner model) can be obtained as

```
\(\mathbf{U} = \mathbf{T}\mathbf{B} + \mathbf{H},\)
```

where \(\mathbf{B}\) is a matrix containing the model parameters relating the input and output principal components, and \(\mathbf{H}\) is a residual matrix.

However, the natural data from engineering and environmental processes cannot well meet the linearity assumption and often exhibits significant nonlinearity. Accordingly, nonlinear PLS models are required. Two families of nonlinear PLS modeling techniques can be distinguished. The first family consists of techniques where the input and output data matrices are projected onto nonlinear surfaces [33], while the relationship between \(\mathbf{T}\) and \(\mathbf{U}\) (shown in Eq. (4.2)) is assumed to be linear. Methods in this first nonlinear PLS family have received very limited attention in prediction and process monitoring. This is mainly because these methods do not retain the properties of the linear methodology, and the mapping of the input and output data matrices is costly and challenging [33]. In the second family of techniques, on the other hand, the input and output matrices are projected linearly, but the relationship between any input principal component \(t\) and any output principal component \(u\) is modeled using a nonlinear function, i.e.,

```
\(\mathbf{u} = f(\mathbf{t}) + \mathbf{h},\)
```

where \(f(\cdot)\) is a continuous nonlinear function relating \(\mathbf{u}\) to \(\mathbf{t}\), and \(\mathbf{h}\) is the residual.

Here, the inner relationship between the latent space of the input and output are mapped using a nonlinear function. This mapping helps capture the nonlinear relationship of the data set, allowing the decomposition of a multivariate regression problem into a few univariate regression problems. The linear PLS outer projection is used as a dimension-reduction tool to remove collinearity,