where

$$\boldsymbol{A} = \begin{bmatrix} 6 & 4 & 3 \\ 6 & 0 & 9 \\ 0 & 8 & 0 \end{bmatrix}$$

and $\sum_{i=1}^3 x_i = 1$.

We start by rephrasing the problem into solving a homogeneous system of linear equations. Let $\boldsymbol{x}$ be in $\mathbb{R}^3$. We notice that $\boldsymbol{A}\boldsymbol{x} = 12\boldsymbol{x}$ is equivalent to $(\boldsymbol{A} - 12I)\boldsymbol{x} = \boldsymbol{0}$, which can be rewritten as the homogeneous system $\tilde{\boldsymbol{A}}\boldsymbol{x} = \boldsymbol{0}$, where we define

$$\tilde{\boldsymbol{A}} = \begin{bmatrix} -6 & 4 & 3 \\ 6 & -12 & 9 \\ 0 & 8 & -12 \end{bmatrix}.$$

The constraint $\sum_{i=1}^3 x_i = 1$ can be transcribed as a fourth equation, which leads us to consider the following linear system, which we bring to reduced row echelon form:

$$\begin{bmatrix} -6 & 4 & 3 & | & 0 \\ 6 & -12 & 9 & | & 0 \\ 0 & 8 & -12 & | & 0 \\ 1 & 1 & 1 & | & 1 \end{bmatrix} \sim \begin{bmatrix} 0 & -8 & 12 & | & 0 \\ 2 & -4 & 3 & | & 0 \\ 0 & 2 & -3 & | & 0 \\ 1 & 1 & 1 & | & 1 \end{bmatrix} \sim \begin{bmatrix} 0 & 0 & 0 & | & 0 \\ 2 & 0 & -3 & | & 0 \\ 0 & 2 & -3 & | & 0 \\ 1 & 1 & 1 & | & 1 \end{bmatrix} \sim \begin{bmatrix} 1 & 0 & -\tfrac{3}{2} & | & 0 \\ 0 & 1 & -\tfrac{3}{2} & | & 0 \\ 1 & 1 & 1 & | & 1 \end{bmatrix} \sim \begin{bmatrix} 1 & 0 & -\tfrac{3}{2} & | & 0 \\ 0 & 1 & -\tfrac{3}{2} & | & 0 \\ 0 & 0 & 4 & | & 1 \end{bmatrix} \sim \begin{bmatrix} 1 & 0 & 0 & | & \tfrac{3}{8} \\ 0 & 1 & 0 & | & \tfrac{3}{8} \\ 0 & 0 & 1 & | & \tfrac{1}{4} \end{bmatrix}$$

Therefore, we obtain the unique solution

$$\boldsymbol{x} = \begin{bmatrix} \tfrac{3}{8} \\ \tfrac{3}{8} \\ \tfrac{1}{4} \end{bmatrix} = \frac{1}{8} \begin{bmatrix} 3 \\ 3 \\ 2 \end{bmatrix}.$$