# 4.2 Projections onto Subspaces

Each sample has two features and we can write these as vectors,

$$\mathbf{v}_1 = \begin{pmatrix} v_{11} \ v_{12} \end{pmatrix} \quad$ and $\quad$ \mathbf{v}_2 = \begin{pmatrix} v_{21} \ v_{22} \end{pmatrix}.$$

The *length of a vector* is the square root of the sum of the squares of the coordinates.

$|\mathbf{v}|| = \sqrt{v_{11}^2 + v_{22}^2}.$$

This is also known as the Euclidean norm or $L_2$ norm. Between two vectors an *inner product*, also known as *scalar product* or *dot product* is defined:

$$\mathbf{v}_1 \cdot \mathbf{v}_2 = (\mathbf{v}_1, \mathbf{v}_2) = v_{11}v_{21} + v_{12}v_{22}.$$

More generally, this can be viewed as a *matrix product* between the *transpose* of the first vector and the second vector.

$$\mathbf{v}_1 \cdot \mathbf{v}_2 = \mathbf{v}_1^T \mathbf{v}_2 = \begin{pmatrix} v_{11} & v_{12} \end{pmatrix} \begin{pmatrix} v_{21} \ v_{22} \end{pmatrix} = v_{11}v_{21} + v_{12}v_{22}.$$

A $1 \times 2$ matrix times a $2 \times 1$ matrix is a $1 \times 1$ matrix.

A common technique is to reduce a higher dimension to a lower one where it can be solved more easily. More generally, many Machine Learning techniques can be viewed as transforming vector spaces, where the data lies, in spaces where information within the data can be extracted more easily. In this case, we reduce the two-dimensional problem to a one-dimensional one by projecting onto a line through zero or one in the direction of a vector $\mathbf{w}$. The formula for the *projection of a vector* $\mathbf{v}$ onto $\mathbf{w}$* is given by

$$\proj_{\mathbf{w}}(\mathbf{v}) = \frac{\mathbf{w}^T \mathbf{v}}{\|\mathbf{w}||^2}.$$

Figure 4.2 illustrates this.

We then select a *threshold* $b$, also known as *bias* that for $\mathbf{v}$

+   - $\$\mathbf{w}^T \mathbf{v} < b \quad \quad$ \implies \quad \quad$ \mathbf{v} \in C_0$,$
- $\$\mathbf{w}^T \mathbf{v} > b \quad \quad$ \implies \quad \quad$ \mathbf{v} \in C_1$.

In Figure 4.2 the bias has to be 0 for $\mathbf{v}_1$ being in class $C_0$ and $\mathbf{v}_2$ being in class $C_1$.

The task is to find the direction $\mathbf{w}$ and separation threshold $b$, w is also known as the vector of weights. The naming is because in the inner product each component of $\mathbf{v}$ is multiplied by a component of $\mathbf{w}$. Since each component of $\mathbf{v}$ is a feature, the components in $w$ signify how much each feature contributes to separating the data. Some features might not be useful for classification after all and then have small weights. The line normal to $\mathbf{w}$ through