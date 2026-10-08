In a good regression model, the regressors correlate minimally with each other, but are each highly correlated with the regressor. The aim is to find a linear combination of few regressors which summarize and explain the data without too much loss of information. This section and the following show how to obtain new regressors from the dictionary.

Principal regression uses the principal components of D as regressors instead of the columns of D. In particular, let $d_1, \dots, d_M$ denote the columns of D. In this case, $d_i$ is the $i^{th}$ basis function evaluated at $x_1, \dots, x_n$. In the following, we assume the columns are standardized, that is, they mean 0 and length 1. The first assumption is valid, since the measures are centred, and the second assumption is valid, since regressors are invariant to scaling. Any scaling will be absorbed in the multiplicative coefficient.

The correlation between the $i^{th}$ and $j^{th}$ regressors evaluated at the $N$ measuring points is

$d_i^T d_j$.

The correlation matrix of all regressors is $D^T D$.

A set of regressors is generated as linear combinations of basis functions from the dictionary, say

$v_1(\mathbf{x}) + \dots + v_M(\mathbf{x})$.

Evaluating this at the $N$ sampling points, we arrive at a linear combination of the columns of **D**.

$v_1 d_1 + \dots + v_M d_M = \mathbf{v}$.

where $\mathbf{v} = (v_1, \dots, v_M)^T$ is chosen such that $D\mathbf{v} \neq 0$. The zero vector would make a very poor regressor.

The correlation between two linear combinations is

$\frac{\mathbf{v}_1^T D^T \mathbf{v}_2}{\|\mathbf{v}_1\|\|\mathbf{v}_2\|}$

where $v_1$ and $v_2$ are such that $D\mathbf{v}_1 \neq 0$ and $D\mathbf{v}_2 \neq 0$. Here here to divide the lengths, since $D\mathbf{v}_1$ and $D\mathbf{v}_2$ no longer have length 1.

Now, the matrix $D^T D$ is symmetric and positive semi-definite. Hence it has $M$ nonnegative eigenvalues and corresponding orthonormal eigenvectors. Thus choosing $\mathbf{v}_1$ and $\mathbf{v}_2$ to be eigenvectors of $D^T D$, the new regressors are uncorrelated, since

$\mathbf{v}_1^T D^T \mathbf{v}_2 = \lambda_2 \mathbf{v}_1^T \mathbf{v}_2 = 0$.

The eigenvectors corresponding to $K$ nonzero eigenvalues are chosen. The new design matrix $\hat{D}$ has columns $D\mathbf{v}_1, \dots, D\mathbf{v}_K$. The corresponding functions span a $K$-dimensional subspace of the original model space, and are uncorrelated.