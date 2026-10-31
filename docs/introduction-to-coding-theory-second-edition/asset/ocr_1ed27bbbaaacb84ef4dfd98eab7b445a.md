Then $A \cdot \mathbf{x}(\delta) = \mathbf{b} - \delta \cdot \mathbf{c}_j + \delta \cdot \mathbf{c}_j = \mathbf{b}$. Put

$\delta_1 = Min_{k,\alpha_{kj}>0}\left(x_k^{(0)}/\alpha_{kj}\right). \tag{15.3}$

If $\mathbf{x}_0$ is degenerate, then it is possible that $\delta_1 = 0$. In the nondegenerate case, $\delta_1 > 0$. The next vertex is $\mathbf{x}_1 = \mathbf{x}(\delta_1)$ (see Definition 15.2). First of all it is clear that we have an admissible point, by the choice of $\delta_1$. Is $\mathbf{x}_1$ really a vertex? Certainly $wt(\mathbf{x}_1) \le m$, as we have only one new nonzero coordinate when compared with $\mathbf{x}_0$, but at least one nonzero coordinate $l$ of $\mathbf{x}_0$ leads to a vanishing coordinate in $\mathbf{x}_1$.

The columns indexed by $Z' = Z - \{l\} \cup \{j\}$ form a basis of $\mathbf{x}_1$. In fact, the cardinality is right. Each vector is expressible in terms of the $\mathbf{c}_k$, where $k \in Z$ (because $Z$ is a basis). As $\mathbf{c}_l$ is expressible in terms of $\mathbf{c}_j$ and the $\mathbf{c}_k$, $k \in Z \setminus \{l\}$, it follows that we have a generating set, and thus a basis.

If $\mathbf{x}_0$ is degenerate and $j$ is chosen appropriately ($\delta_1 = 0$), then $\mathbf{x}_1 = \mathbf{x}_0$ with a new basis. Now express now the columns of $A$ with respect to the new basis given by $Z'$ in analogy with Equation 15.1:

$\mathbf{c}_i = \sum_{k \in Z'} \alpha'_{ki} \cdot \mathbf{c}_k,\; i = 1,2,\dots,n.$

Comparing the two expressions, the new structure constants are obtained from the old ones:

$\alpha'_{jl} = 1/\alpha_{ij}$  
$\alpha'_{ji} = \alpha_{li}/\alpha_{ij}$  
$\alpha'_{kl} = -\alpha_{kj}/\alpha_{ij}\quad (k \in Z,\;k \ne l)$  
$\alpha'_{ki} = \alpha_{ki} - \dfrac{\alpha_{li}\alpha_{kj}}{\alpha_{ij}}\quad (k \in Z,\;k \ne l). \tag{15.4}$

Let $\mathbf{x} \in \mathcal{M}$. By definition $\sum_{i=1}^n x_i \cdot \mathbf{c}_i = \mathbf{b}$. The same thing holds for the vertex $\mathbf{x}_0$. Compare: $\displaystyle \sum_{k \in Z} x_k^{(0)}\mathbf{c}_k = \mathbf{b} = \sum_{i=1}^n x_i \sum_{k \in Z} \alpha_{ki}\mathbf{c}_k.$ Comparing coefficients and observing that, for $k,i \in Z$, the coefficient $\alpha_{ki}$ is nonzero only if $k=i$, we obtain $\displaystyle x_k = x_k^{(0)} - \sum_{i \notin Z} \alpha_{ki}x_i \quad (k \in Z). \tag{15.5}$