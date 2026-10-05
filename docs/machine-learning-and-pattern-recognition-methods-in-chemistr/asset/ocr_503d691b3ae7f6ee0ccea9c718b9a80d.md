# Machine learning and pattern recognition methods in chemistry

![](bbox=[0.296, 0.098, 0.673, 0.281])

![](bbox=[0.216, 0.363, 0.763, 0.473])

**Fig. 1.3** Schematic representation of the multi-way P-ALS algorithm for (top) finding the rows of the spectral matrix, **S**, and (bottom) finding the rows of the concentration matrix, **C** (Richards et al., 2008).

$$\mathbf{y} = \begin{bmatrix} 0.7094 & 0.8147 & 0.9575 & 0.4218 \ 0.7544 & 0.9058 & 0.9649 & 0.9157 \ 0.2760 & 0.1270 & 0.1576 & 0.7922 \ 0.6797 & 0.9134 & 0.9706 & 0.9595 \ 0.6551 & 0.6324 & 0.9572 & 0.6557 \ 0.1626 & 0.0975 & 0.4854 & 0.0357 \ 0.1190 & 0.2785 & 0.8003 & 0.0357 \ 0.4984 & 0.5469 & 0.1419 & 0.9340 \end{bmatrix} = \begin{bmatrix} 0.8184 \ -0.0115 \ 0.0421 \end{bmatrix} (1.4)$

In this example, $\mathbf{y}$ represents the first column of the augmented data $\mathbf{A}_c$, $\mathbf{X}$ represents the augmented concentration matrix $\mathbf{C}_c$, and $\mathbf{b}$ is the first column of $\mathbf{S}^T$. Suppose an equality constraint is required in the first coefficient