

$J(\mathbf{\varphi}) = \mathbb{E} \left[ \middle| y_{n} - \mathbf{\varphi}^{H}{\widetilde{\mathbf{x}}}_{n}|^{2} \right],$

![Equation](images/B9780443292385000111/si316.png)

遵循类似于第 [5.3.1](#Chp005_177-248_B9780443292385000111.xhtml#s0030) 节的标准论证，关于 `φ` 的最小值由以下方程的根给出：

$\Sigma_{\widetilde{x}}\mathbf{\varphi} - \begin{bmatrix} \mathbf{p} \\ \mathbf{q}^{\ast} \\ \end{bmatrix} = 0\text{~or~}\mathbb{E} \left[ {\widetilde{\mathbf{x}}}_{n}{\widetilde{\mathbf{x}}}_{n}^{H} \right]\mathbf{\varphi} = \mathbb{E} \left[ {\widetilde{\mathbf{x}}}_{n}y_{n}^{\ast} \right].$

![Equation](images/B9780443292385000111/si317.png)

### 广义线性 LMS

采用 Robbins–Monro 方案并将 `μ[n]` 的值固定为常数，我们得到

$\mathbf{\varphi}_{n} = \mathbf{\varphi}_{n - 1} + \mu{\widetilde{\mathbf{x}}}_{n}e_{n}^{\ast},e_{n} = y_{n} - \mathbf{\varphi}_{n - 1}^{H}{\widetilde{\mathbf{x}}}_{n}.$

![Equation](images/B9780443292385000111/si318.png)

将 `φ[n]` 和 ${\widetilde{\mathbf{x}}}_{n}$ 分解为其分量，即得广义线性 LMS。

#### 算法 5.4：广义线性 LMS

*   **初始化**
    1.  `θ[−1] = 0`, `v[−1] = 0`
    2.  选择 `μ`。

