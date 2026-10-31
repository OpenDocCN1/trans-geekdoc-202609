| Scaling technique | Scaling factor $d_j$ |
|---|---|
| Auto | $\sigma_j$ |
| Pareto | $\sqrt{\sigma_j}$ |
| Range | $max(\mathbf{X}_j) - min(\mathbf{X}_j)$ |
| VAST | $\sigma_j^2 / \bar{\mathbf{X}}_j$ |

Table 15.1 Few selected common data scaling criteria. $\sigma_j$ is the standard deviation, $max(\mathbf{X}_j)$ is the maximum value, $min(\mathbf{X}_j)$ is the minimum value, and $\bar{\mathbf{X}}_j$ is the mean observation of the $j$th state-space variable $\mathbf{X}_j$.

# 15.2.1 Data Preprocessing

Combustion data sets typically contain variables of different numerical ranges (e.g., both temperature, which can range from hundreds up to thousands, and mass (or mole) fractions of chemical species, which take values in the range $Y_i \in \langle 0,1\rangle$). Scaling the data set is crucial in order to balance the importance of all state-space variables (Parente & Sutherland 2013). The data set $\mathbf{X}$ can be centered and scaled as follows:

$\tilde{\mathbf{X}} = (\mathbf{X} - \bar{\mathbf{X}})\mathbf{D}^{-1}, \qquad (15.4)$

where $\tilde{\mathbf{X}}$ contains the mean observations of each variable, $\mathbf{D}$ is the diagonal matrix of scales, where the $j$th element $d_j$ from the diagonal is the scaling factor corresponding to the $j$th state-space variable $\mathbf{X}_j$. A few of the common scaling criteria are collected in Table 15.1. The result is a centered and scaled data matrix $\tilde{\mathbf{X}}$. Other preprocessing means can include outlier detection or data sampling. For the remainder of this chapter, we will assume that $\tilde{\mathbf{X}}$ represents the matrix that has been adequately preprocessed.

# 15.3 Feature Extraction Using Dimensionality Reduction Techniques

Dimensionality reduction techniques offer a way to represent high-dimensional combustion data sets in a new, lower-dimensional basis. Such data representations are referred to as low-dimensional manifolds. Techniques such as PCA, NMF, or autoencoders can extract those manifolds in an empirical way from the training data sets. This approach belongs to the family of ELDMs (Pope 2013, Yang et al. 2013), and it is based on the idea that compositions occurring in combustion systems lie close to a low-dimensional manifold. In addition, these techniques offer a way to extract meaningful features by exploiting the fact that the new basis can be better suited to represent certain physical phenomena underlying the original data. In this section, we review a few popular dimensionality reduction techniques, and we present their potential to detect features in combustion data sets.

# 15.3.1 Description of the Analyzed Data Set

In this section, we apply various dimensionality reduction techniques on a numerical data set from a DNS simulation of a CO/H₂ turbulent jet (Sutherland et al. 2007)