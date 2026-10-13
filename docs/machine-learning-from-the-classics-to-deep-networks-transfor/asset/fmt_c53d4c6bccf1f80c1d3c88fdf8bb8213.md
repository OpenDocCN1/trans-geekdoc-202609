
$$
\mathbf{e}_{l}^{b}(n) := \begin{bmatrix} e_{0}^{b}(n) \\ e_{1}^{b}(n) \\ \vdots \\ e_{l - 1}^{b}(n) \end{bmatrix} = U^{H}\begin{bmatrix} u_{n} \\ u_{n - 1} \\ \vdots \\ u_{n - l + 1} \end{bmatrix} = U^{H}\mathbf{u}_{l}(n),
$$

![Equation](images/B978044329238500010X/si354.png) (4.81)

where

$$
U^{H} := \begin{bmatrix} 1 & 0 & 0 & \cdots & 0 \\ -a_{1}(0) & 1 & 0 & \cdots & 0 \\ \vdots & \vdots & \vdots & \vdots & 0 \\ -a_{l}(l - 1) & -a_{l}(l - 2) & \cdots & \cdots & 1 \end{bmatrix}
$$

![Equation](images/B978044329238500010X/si355.png)

and

$$
\mathbf{a}_{m} := [a_{m}(0), a_{m}(1), \dots, a_{m}(m-1)]^{T}, \quad m = 1, 2, \dots, l.
$$

![Equation](images/B978044329238500010X/si356.png)

*   Due to the orthogonality of the involved backward errors,
