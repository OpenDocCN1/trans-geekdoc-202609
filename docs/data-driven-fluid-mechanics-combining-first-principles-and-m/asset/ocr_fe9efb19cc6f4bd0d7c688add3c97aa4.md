# 8.2.2 Projections in Space or Time

in Section 8.2.5. The space domain is sampled over a grid $(x_i, y_i) \in \mathbb{R}^{n_x \times n_y}$, with $x_i = i\Delta x$, $i \in [0, n_x - 1]$ and $y_j = j\Delta x$, $y \in [0, n_y - 1]$.

In a vector quantity, for example, a velocity field $U[u(x_i), v(x_i)]$, we consider that the reshaping stacks all the components one below the other producing a state vector of size $n_s = n_C n_x n_y$, where $n_C = 2$ is the number of velocity components. Therefore, the snapshot of the data at a time $t_k$ is a vector $\mathbf{d}_k[i] \in \mathbb{R}^{n_s \times 1}$, while the temporal evolution of the data at a location $\mathbf{i}$ is a vector $\mathbf{d}_i[k] \in \mathbb{R}^{n_t \times 1}$. We then have $D[\mathbf{i}, k = c] = \mathbf{d}_c[\mathbf{k}] \in \mathbb{R}^{n_s \times 1}$ and $D[\mathbf{i} = \mathbf{c}, k] = \mathbf{d}_c[l] \in \mathbb{R}^{1 \times n_t}$.

Every linear operation on a discrete 1D signal, represented as a column vector, can be carried out via matrix multiplication. This is true for convolutions, changes of bases (i.e., linear transforms), and filtering. Understanding the matrix formalism of these operations brings at least three benefits. First, the notation is simplified by replacing summations on sequences with matrix-vector multiplications. Second, the efficiency and compactness of computer codes for signal processing are largely augmented,$^4$ by avoiding the nested “for” loops implied in the summation notation. Third, the linear algebra representation of these operations offers a valuable geometrical interpretation.

Consider the problem of decomposing a column vector $\mathbf{u} \in \mathbb{R}^{n_u \times 1}$ into a linear combination of basis vectors $\{\mathbf{b}_1, \mathbf{b}_2, \dots, \mathbf{b}_{n_b}\}$ of equal dimensions. This means

$$u[k] = \mathbf{u} = \sum_{r=1}^{n_u} c_r \mathbf{b}_r \iff \mathbf{u} = \mathbf{B} \mathbf{u}_B,\tag{8.1}$$

where $\mathbf{B} = [\mathbf{b}_1, \mathbf{b}_2, \dots \mathbf{b}_{n_b}] \in \mathbb{C}^{n_u \times n_b}$ is the basis matrix having all the elements of the basis along its columns, and $\mathbf{u}_B = [c_1, c_1, \dots, c_{n_b}]^T$ is the set of coefficients in the linear combination, that is, the representation of the vector in the new basis. Computing the transform of a vector with respect to a basis $\mathbf{B}$ means solving a linear system of algebraic equations. Such a system can have no solution, one solution, or infinite solutions depending on $n_b$ and $n_u$.

If $n_b < n_u$, as it is the case in model-order reduction, the system is overdetermined and there is no solution.$^5$ In this case, we look for the approximated solution $\tilde{\mathbf{u}}_B$ that is obtained by projecting $\mathbf{u}$ onto the column space of $\mathbf{B}$. This is provided by the well-known least-squares approximation, which gives$^6$

$$\mathbf{u} = \mathbf{B} \mathbf{u}_B \implies \tilde{\mathbf{u}}_B = (\mathbf{B}^\dagger \mathbf{B})^{-1} \mathbf{B}^\dagger \mathbf{u} \implies \tilde{\mathbf{u}} = \mathbf{B} (\mathbf{B}^\dagger \mathbf{B})^{-1} \mathbf{B}^\dagger \mathbf{u} = \mathcal{P}_B \mathbf{u}.\tag{8.2}$$

The least-squares solution minimizes $\|\mathbf{u} - \mathbf{B} \mathbf{u}_B\|_2 = \|\mathbf{e}\|_2$; the minimization imposes that the error vector $\mathbf{e}$ is orthogonal to the column space of $\mathbf{B}$. In the machine learning terminology, the matrix $\mathcal{P}_B = \mathbf{B} (\mathbf{B}^\dagger \mathbf{B})^{-1} \mathbf{B}^\dagger$ is an autoencoder that maps a