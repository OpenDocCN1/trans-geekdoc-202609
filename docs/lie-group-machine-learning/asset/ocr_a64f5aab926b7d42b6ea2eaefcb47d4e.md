It can be transformed into:

```
\begin{equation}
\begin{split}
& \sum_i \left\| \mathbf{A}_i \times_1 \boldsymbol{U}^{(1)} \times_2 \boldsymbol{U}^{(2)} \cdots \times_N \boldsymbol{U}^{(N)} \right\|_F^2 \
& = \sum_i \left\| \boldsymbol{Y}_i^k \times_k \boldsymbol{U}^{(k)} \right\|_F^2 \
& = \sum_i \left\| \left( \boldsymbol{Y}_i^{k(k)} \right)^T \times_k \boldsymbol{U}^{(k)} \right\|_F^2 \
& = \sum_i tr \left[ \left( \boldsymbol{U}^{(k)} \right)^T \boldsymbol{Y}_i^{k(k)} \left( \boldsymbol{Y}_i^{k(k)} \right)^T \boldsymbol{U}^{(k)} \right] \
& = \sum_i tr \left[ \left( \boldsymbol{U}^{(k)} \right)^T \left( \sum_i \boldsymbol{Y}_i^{k(k)} \left( \boldsymbol{Y}_i^{k(k)} \right)^T \right) \boldsymbol{U}^{(k)} \right] \quad \text{(10.27)}
\end{split}
\end{equation}
```

The method of solving for $U^{(k)}$ is similar to the least-squares method of the HOOI algorithm. First, we assume that $W_k$ are already known. To maximize (10.27), $U^{(k)} \in \boldsymbol{R}^{I_k \times K_k}$ should include $K^{(k)}$ eigenvectors corresponding to the largest eigenvalues. The specific algorithm is shown in the following algorithm.

```
**Algorithm 10.2:** Data reduction algorithm based on tensor field
**Input:** Data $\boldsymbol{A}_i \in \boldsymbol{R}^{I_1 \times I_2 \times \cdots \times I_N}$, $(i=1 \ldots m)$, $\boldsymbol{K} = \{K_n\}$, $(n=1 \ldots N)$.
**Output:** $U^{(n)} \in \boldsymbol{R}^{n \times K_n}$, $S_j \in \boldsymbol{R}^{K_1 \times \cdots \times K_N}$, $(n=1,2,\ldots N, i=1,2,\ldots m)$.
**Process:**
(1) set $U^{(n)}$ to a matrix; its column vectors are orthogonal to each other
(2) do:
\quad For $k=1 \to N$
\quad\quad a) Solve $Y_i^k$;
\quad\quad b) $W_k \leftarrow \sum_i Y_i^{k(k)} \left(Y_i^{k(k)}\right)^T$;
\quad\quad c) Do the singular value decomposition of $W_k$;
\quad\quad d) Update $U^{(k)}$.
\quad End for
\quad Until convergence
(3) calculate $S_j$: $S_j = A_j \times_1 U^{(1)} \times_2 U^{(2)} \cdots \times_N U^{(N)}$
```

# 10.2.4 Experiment

To verify the algorithm validity, we applied Algorithm 10.2 to human face reconstruction. In the data reduction model of the tensor field, $\boldsymbol{X}$ is the original image set. From the viewpoint of the tensor, a human face image is a second-order tensor, and it is the result of the tensor product of the column vector and row vector. For a grey image with size $112 \times 92$, it represents an element in tensor space $\boldsymbol{R}^{112} \otimes \boldsymbol{R}^{92}$. The human face image is a low-dimensional manifold [7--10]. We should choose a different $\boldsymbol{K}$ and observe the experimental results (Figure 10.8).