+   - The rank of $A_\Phi$ is the number linearly independent rows/columns. We use Gaussian elimination on $A_\Phi$ to determine the reduced row echelon form (Not necessary to identify the number of linearly independent rows/columns, but useful for the next questions.):
+   
+   $$
+   \begin{bmatrix}
+   1 & 0 & 0 \\
+   0 & 1 & 0 \\
+   0 & 0 & 1 \\
+   0 & 0 & 0
+   \end{bmatrix}.
+   $$
+   
+   From here, we see that $\mathrm{rk}(A_\Phi)=3$.
+   - $\ker(\Phi)=\mathbf{0}$ and $\dim(\ker(\Phi))=0$. From the reduced row echelon form, we see that all three columns of $A_\Phi$ are linearly independent. Therefore, they form a basis of $\mathrm{Im}(\Phi)$, and $\dim(\mathrm{Im}(\Phi))=3$.

2.18 Let $E$ be a vector space. Let $f$ and $g$ be two automorphisms on $E$ such that $f \circ g = \mathrm{id}_E$ (i.e., $f \circ g$ is the identity mapping $\mathrm{id}_E$). Show that $\ker(f)=\ker(g \circ f)$, $\mathrm{Im}(g)=\mathrm{Im}(g \circ f)$ and that $\ker(f)\cap\mathrm{Im}(g)=\{\mathbf{0}_E\}$.

Let $\boldsymbol{x}\in\ker(f)$. We have $g(f(\boldsymbol{x}))=g(\mathbf{0})=\mathbf{0}$ since $g$ is linear. Therefore, $\ker(f)\subseteq\ker(g\circ f)$ (this always holds).

Let $\boldsymbol{x}\in\ker(g\circ f)$. We have $g(f(\boldsymbol{x}))=\mathbf{0}$ and as $f$ is linear, $f(g(f(\boldsymbol{x})))=f(\mathbf{0})=\mathbf{0}$. This implies that $(f\circ g)(f(\boldsymbol{x}))=\mathbf{0}$ so that $f(\boldsymbol{x})=\mathbf{0}$ since $f\circ g=\mathrm{id}_E$. So $\ker(g\circ f)\subseteq\ker(f)$ and thus $\ker(g\circ f)=\ker(f)$.

Let $\boldsymbol{y}\in\mathrm{Im}(g\circ f)$ and let $\boldsymbol{x}\in E$ so that $\boldsymbol{y}=(g\circ f)(\boldsymbol{x})$. Then $\boldsymbol{y}=g(f(\boldsymbol{x}))$, which shows that $\mathrm{Im}(g\circ f)\subseteq\mathrm{Im}(g)$ (which is always true).

Let $\boldsymbol{y}\in\mathrm{Im}(g)$. Let then $\boldsymbol{x}\in E$ such that $\boldsymbol{y}=g(\boldsymbol{x})$. We have $\boldsymbol{y}=g((f\circ g)(\boldsymbol{x}))$ and thus $\boldsymbol{y}=(g\circ f)(g(\boldsymbol{x}))$, which means that $\boldsymbol{y}\in\mathrm{Im}(g\circ f)$. Therefore, $\mathrm{Im}(g)\subseteq\mathrm{Im}(g\circ f)$. Overall, $\mathrm{Im}(g)=\mathrm{Im}(g\circ f)$.

Let $\boldsymbol{y}\in\ker(f)\cap\mathrm{Im}(g)$. Let $\boldsymbol{x}\in E$ such that $\boldsymbol{y}=g(\boldsymbol{x})$. Applying $f$ gives us $f(\boldsymbol{y})=(f\circ g)(\boldsymbol{x})$ and as $\boldsymbol{y}\in\ker(f)$, we have $\mathbf{0}=\boldsymbol{x}$. This means that $\ker(f)\cap\mathrm{Im}(g)\subseteq\{\mathbf{0}\}$ but the intersection of two subspaces is a subspace and thus always contains $\mathbf{0}$, so $\ker(f)\cap\mathrm{Im}(g)=\{\mathbf{0}\}$.

2.19 Consider an endomorphism $\Phi : \mathbb{R}^3 \to \mathbb{R}^3$ whose transformation matrix (with respect to the standard basis in $\mathbb{R}^3$) is

$$A_\Phi = \begin{bmatrix}1 & 1 & 0 \\ 1 & -1 & 0 \\ 1 & 1 & 1\end{bmatrix}.$$

a. Determine $\ker(\Phi)$ and $\mathrm{Im}(\Phi)$.

The image $\mathrm{Im}(\Phi)$ is spanned by the columns of $A$. One way to determine a basis, we need to determine the smallest generating set of the columns of $A_\Phi$. This can be done by Gaussian elimination. However, in this case, it is quite obvious that $A_\Phi$ has full rank, i.e., the set of columns is already minimal, such that

$$\mathrm{Im}(\Phi)=\left[\begin{matrix}1\\1\\1\end{matrix},\begin{matrix}1\\-1\\1\end{matrix},\begin{matrix}0\\0\\1\end{matrix}\right]=\mathbb{R}^3$$