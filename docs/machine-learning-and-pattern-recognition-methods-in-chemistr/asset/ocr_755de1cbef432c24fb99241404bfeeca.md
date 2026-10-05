appended. In this data arrangement strategy, different data matrices are sup- to have common vector spaces.

```
$[D_1; D_2; D_3; \dots; D_k] = [C_1; C_2; C_3; \dots; C_k] \mathbf{A}^T + [E_1; E_2; E_3; \dots; E_k] \= \mathbf{C}_{aug} \mathbf{A}^T + \mathbf{E}_{aug}\n(7.6)$
```

A column-wise augmented concentration matrix, i.e., $[C_1; C_2; C_3; \dots; C_k]$, is obtained to describe the concentration changes in the indi- individual data matrices. $\mathbf{A}^T$ contains spectral profiles of all constituents in all sub-matrices and $\mathbf{E}_{aug}$ is the residual matrix. Eq. (7.6) shows the augment- tion of K matrices with the same size of $I \times J$. $[D_1; D_2; D_3; \dots; D_k] = \mathbf{D}_{aug} \mathbf{A}^T$ has rows and columns. Considering the fact that $\mathbf{C}$, $\mathbf{A}$, and $\mathbf{C}$ are the component matrices related to the three modes, each of $D_k$ can be formulated as:

```
$D_k = \mathbf{C}_{diag}(C_k(k, :))\mathbf{A}^T, k = 1, \dots, k.\n(7.7)$
```

The outer product of the respective component matrices, $\mathbf{C}$ and $\mathbf{A}^T$ in the column and row space of $D_k$ with proper intensities, will generate each $D_k$ matrix. The $\mathbf{C}_l(k,:)$ matrix contains total concentration values of each component in the kth data set. Equation is a well-known representation of a series of matrices with the trilinearity properties. The abstract space of the $\mathbf{D}_{aug}$ can be estimated by the application of the SVD to the data matrix (r is the number of abstract factors in the $D_{aug}$):

```
$\mathbf{D}_{aug} = \mathbf{U}_{aug} S_{aug} \mathbf{V}_{aug}^T + \mathbf{E}_{aug} = \mathbf{X}_{aug} \mathbf{V}_{aug}^T + \mathbf{E}'_{aug} = \mathbf{U}_{aug} \mathbf{Y}_{aug}^T + \mathbf{E}''_{aug}\n(7.8)$
```

If $E_{aug}$ is almost as the $E_{aug}'$ the subspace spanned by the truncated $\mathbf{U}_{aug}$ is a good estimation of the subspace spanned by the $\mathbf{C}_{aug}$ ($\mathbf{C}_{aug}=\mathbf{U}_{aug}S$), the subspace spanned by the truncated matrix is a good estimation of the subspace spanned by the $\mathbf{A}^T$ ($\mathbf{A}=\mathbf{T}^{-1} \mathbf{X}_{aug}}$). $\mathbf{T}$ and $\mathbf{T}^{-1}$, as the transformation matrices, generate $\mathbf{C}_{aug}$ and $\mathbf{A}^T$ by the lin- combination of the $\mathbf{U}_{aug}$ and $\mathbf{V}_{aug}'$ respectively.

As a result of the bilinear structure of, $\mathbf{V}_{aug}$ and $\mathbf{U}_{aug}'$ spaces have a mutual duality relationship. Thus, each point in the column space of a data has a dual hyperplane in its row space, and vice versa. This mathematical relation provides an efficient tool to transfer the information of one space to its dual space. Consequently, in a powerful approach of unique solution or uniqueness, the condition is almost studied and visualized.