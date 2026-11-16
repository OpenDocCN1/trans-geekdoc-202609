directions of the FDMN in a vector

$\underline{n} = (n_K^1, ..., n_K^{3(2^{K-1})}, n_{K-1}^1, ..., n_{K-1}^{2^{K-2}}, ..., n_2^1, n_2^2, n_1^1)$, (5.64)

where we used the fact that the $k$-th layer contains $2^{k-1}$ normals if $k < K$, and the $K$-th layer contains $3(2^{K-1})$ normals. Because the homogenization blocks in the $K$-th layer are rank-three CLMs, the number of normals is different from the other layers. Each normal $n_k^i$ in the k-th layer for $k < K$ is constructed using two angles $a_k^i$ and $b_k^i$ via

$n_k^i = \sin(b_k^i) \cos(a_k^i) e_1 + \sin(b_k^i) \sin(a_k^i) e_2 + \cos(b_k^i) e_3$. (5.65)

However, for the normals $n_K^i$ in the $K$-th layer, the procedure is different. To avoid singular effective properties during the evaluation of the FDMN in accordance with the discussion in sections 5.2.3 and A.2, we ensure that the three layering normals of a rank-three CLM block are not mutually non-orthogonal and mutually non-collinear as follows. First, for each rank-three CLM block $\mathcal{C}_3^i$, we compute the components $Q_{op}^i$ of the orthogonal tensor $Q^i$ in the standard basis $\{e_i\}$ using three Euler angles $c_K^i, d_K^i, e_K^i \in [0, 2\pi]$ via

$Q_{op}^i = G_{om}^i T_{mn}^i W_{np}^i$ (5.66)

$G_{om}^i = \begin{bmatrix} 1 & 0 & 0 \\ 0 & \cos(c_K^i) & -\sin(c_K^i) \\ 0 & \sin(c_K^i) & \cos(c_K^i) \end{bmatrix}$, (5.67)

$T_{mn}^i = \begin{bmatrix} \cos(d_K^i) & 0 & \sin(d_K^i) \\ 0 & 1 & 0 \\ -\sin(d_K^i) & 0 & \cos(d_K^i) \end{bmatrix}$, (5.68)

$W_{np}^i = \begin{bmatrix} \cos(e_K^i) & -\sin(e_K^i) & 0 \\ \sin(e_K^i) & \cos(e_K^i) & 0 \\ 0 & 0 & 1 \end{bmatrix}$. (5.69)