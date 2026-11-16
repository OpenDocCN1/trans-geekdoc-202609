of the jump vector $\underline{b}$ is orthogonal to the $i$-th entry $\boldsymbol{n}_i$ of the vector of layering normals $\underline{n}$, i.e.,

\(\boldsymbol{b}_i \cdot \boldsymbol{n}_i = 0.\)

Hence, we construct the block diagonal matrix $\underline{\underline{N}} : (\mathbb{R}^3)^{\otimes N_n} \to (\mathbb{R}^3)^{\otimes N_n}$ consisting of $N_w$ blocks $\boldsymbol{N}_i$ on the main diagonal, which are defined as

\(\boldsymbol{N}_i = \beta_i \boldsymbol{n}_i \otimes \boldsymbol{n}_i, \quad i \in \{1, ..., N_w\}\)

with the constant $\beta_i \in \mathbb{R}_{>0}$. By definition, it holds that

\(\boldsymbol{N}_i \boldsymbol{b}_i = \boldsymbol{0},\)

and the jump vector $\underline{b}$ is in the kernel of $\underline{\underline{N}}$ such that

\(\underline{\underline{N}} \underline{b} = \underline{0}.\)

Thus, we add equations (5.87) and (5.91), such that the solution $\Delta \underline{b}_n$ of the resulting update rule

\((\underline{\underline{H}} + \underline{\underline{N}}) \Delta \underline{b}_n = \underline{A}^\top \underline{W} \underline{\tau} (\bar{\underline{D}} + \underline{A} \underline{b}) ,\)

is unique. However, floating point precision may cause issues during the addition of the operators $\underline{\underline{H}}$ and $\underline{\underline{N}}$, if numbers of largely different magnitudes are summed. To remedy this issue, the scalars $\beta_i$ need to be chosen according to the magnitude of the entries in the matrix $\underline{\underline{H}}$. Furthermore, some input weights $w_{K+1}^i$ might become equal to, or close to zero during training, which might render the system matrix $(\underline{\underline{H}} + \underline{\underline{N}})$ ill-conditioned. Thus, it might be difficult to obtain accurate update directions $\Delta \underline{b}_n$ by solving equation (5.92). While it is generally possible to prune the FDMN tree (Liu and Wu, 2019) by removing phases with vanishing or almost vanishing volume fractions, this might collapse the rank-3 CLMs of the bottom FDMN layer into layered materials of