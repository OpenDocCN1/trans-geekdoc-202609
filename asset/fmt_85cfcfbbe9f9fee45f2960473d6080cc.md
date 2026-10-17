
## 数学推导与矩阵微积分

### 雅可比矩阵定义

$$
\begin{bmatrix}
\frac{\partial f_{1}}{\partial x_{1}} & \frac{\partial f_{2}}{\partial x_{1}} & \cdots & \frac{\partial f_{m}}{\partial x_{1}} \\
\frac{\partial f_{1}}{\partial x_{2}} & \frac{\partial f_{2}}{\partial x_{2}} & \cdots & \frac{\partial f_{m}}{\partial x_{2}} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{\partial f_{1}}{\partial x_{n}} & \frac{\partial f_{2}}{\partial x_{n}} & \cdots & \frac{\partial f_{m}}{\partial x_{n}}
\end{bmatrix} \in \mathbb{R}^{n \times m}
$$

雅可比矩阵由不同多元实值函数的梯度向量累积而成，因此梯度的四则运算和链式法则也适用。

### 向量值函数的导数运算

设 $f, g$ 为从 $\mathbb{R}^{n}$ 到 $\mathbb{R}^{m}$ 的两个向量值函数，则：

$$D(\alpha f + \beta g)(x) = \alpha Df(x) + \beta Dg(x)$$

设 $g$ 为从 $\mathbb{R}^{m}$ 到 $\mathbb{R}^{k}$ 的向量值函数，$f$ 为从 $\mathbb{R}^{k}$ 到 $\mathbb{R}^{n}$ 的向量值函数。对于 $\mathbb{R}^{m}$ 中的点 $x$，设 $g(x)$ 的值为 $z$。如果向量值函数和自变量等均为列向量形式，则：

$$(f \circ g)'(x) = D(f \circ g)(x) = f'(z)g'(x) = Df(z)Dg(x)$$

如果向量值函数和自变量等均为行向量形式，则：

$$(f \circ g)'(x) = D(f \circ g)(x) = g'(x)f'(z) = Dg(x)Df(z)$$

向量 $x = (x_1, x_2, \cdots, x_n)$ 可以看作其自身的多元向量值函数，其导数为单位矩阵 $I$：

$$
\frac{dx}{dx} = \begin{bmatrix}
1 & 0 & \cdots & 0 \\
0 & 1 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & 1
\end{bmatrix} = I
$$

根据导数的四则运算规则，对于向量 $x$ 和 $b$，$\nabla_x(\alpha x + \beta b) = \alpha I$。

### 示例 4：复合函数求导验证

在上述示例 4 中，如果将 $E(y, \hat{y})$ 视为 $y$ 的函数，该函数可视为两个函数 $z = y - \hat{y}$ 和 $E(z) = \frac{1}{2}z^2$ 的复合函数。$E(y, \hat{y})$ 关于 $y$ 的梯度为：

$$E'(z) = z^T$$
$$z'(y) = (y - \hat{y})' = I$$
$$\nabla_y E(y, \hat{y}) = E'(z)z'(y) = z^T z'(y) = z^T I = z^T = (y - \hat{y})^T$$

### 示例 5：线性变换复合

设

$$
z(x) = \begin{bmatrix} z_1(x) \\ z_2(x) \end{bmatrix} = \begin{bmatrix} 2x_1 + 4x_2 + 7x_3 \\ 3x_1 + 5x_2 + 4x_3 \end{bmatrix}
$$

是 $x$ 的函数，且

$$y = \begin{bmatrix} 4z_1 + 3z_2 \end{bmatrix}$$

是 $z$ 的函数，则 $f(x) = y(z(x))$ 是 $y(z)$ 和 $z(x)$ 的复合函数，根据复合函数求导规则，有：

$$
f'(x) = y'(z)z'(x) = (4,3)\begin{bmatrix} 2 & 4 & 7 \\ 3 & 5 & 4 \end{bmatrix} = (17,31,40)
$$

展开 $f(x)$ 的完整表达式：

$$f(x) = 4(2x_1 + 4x_2 + 7x_3) + 3(3x_1 + 5x_2 + 4x_3) = 17x_1 + 31x_2 + 40x_3$$

可以验证上述结果是正确的。

如果约定梯度写成列向量形式，链式法则将按相反顺序书写：

$$
y'(z) = \begin{bmatrix} 4 \\ 3 \end{bmatrix} \quad
z'(x) = \begin{bmatrix} 2 & 3 \\ 4 & 5 \\ 7 & 4 \end{bmatrix} \quad
f'(x) = z'(x)y'(z) = \begin{bmatrix} 2 & 3 \\ 4 & 5 \\ 7 & 4 \end{bmatrix}\begin{bmatrix} 4 \\ 3 \end{bmatrix} = \begin{bmatrix} 17 \\ 31 \\ 40 \end{bmatrix}
$$

在今后推导这些公式时，必须注意梯度等向量是列向量还是行向量。

### 示例 6：矩阵乘法导数

$$
z = \begin{bmatrix} z_1 & z_2 & \cdots & z_n \end{bmatrix} = \begin{bmatrix} x_1 & x_2 & \cdots & x_m \end{bmatrix} \cdot \begin{bmatrix}
w_{11} & w_{12} & \ldots & w_{1n} \\
w_{21} & w_{22} & \ldots & w_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
w_{m1} & w_{m2} & \ddots & w_{mn}
\end{bmatrix}
$$

$$
= \begin{bmatrix}
w_{11} x_1 + w_{21} x_2 + \cdots + w_{m1} x_m, &
w_{12} x_1 + w_{22} x_2 + \cdots + w_{m2} x_m, &
\cdots, &
w_{1n} x_1 + w_{2n} x_2 + \cdots + w_{mn} x_m
\end{bmatrix}
$$

因为 $\frac{\partial z_i}{\partial x_j} = w_{ji}$，所以 $\frac{\partial z_i}{\partial x} = w_{.i}$ 是矩阵 $W$ 的第 $i$ 列，故 $\frac{\partial z}{\partial x} = W$。

如果还有另一个变量 $y$，$z$ 关于 $y$ 的梯度为 $\frac{dy}{dz} = (\frac{\partial y}{\partial z_1}, \frac{\partial y}{\partial z_2}, \cdots, \frac{\partial y}{\partial z_n})^T$，则

### 链式法则与偏导数

$$
\frac{dy}{dx} = \frac{\partial y}{\partial z_{1}} \frac{\partial z_{1}}{\partial x} + \frac{\partial y}{\partial z_{2}} \frac{\partial z_{2}}{\partial x} + \cdots + \frac{\partial y}{\partial z_{n}} \frac{\partial z_{n}}{\partial x} = \frac{dz}{dx}\frac{dy}{dz} = \left(\frac{\partial z_{1}}{\partial x},\frac{\partial z_{2}}{\partial x},\cdots,\frac{\partial z_{n}}{\partial x}\right)\left(\frac{\partial y}{\partial z_{1}},\frac{\partial y}{\partial z_{2}},\cdots,\frac{\partial y}{\partial z_{n}}\right)^{T} = W \frac{dy}{dz}
$$

因为 $\frac{\partial z_{j}}{\partial w_{ij}} = x_{i}$，$\frac{\partial z_{k}}{\partial w_{ij}} = 0, k \neq j$，

示例：

$$
\frac{dz_{1}}{dW} = \begin{bmatrix}
x_{1} & 0 & \ldots & 0 \\
x_{2} & 0 & \ldots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
x_{m} & 0 & \ldots & 0
\end{bmatrix}
$$

如果存在另一个变量 $y$，$z$ 的梯度为 $\frac{dy}{dz} = (\frac{\partial y}{\partial z_{1}},\frac{\partial y}{\partial z_{2}},\cdots,\frac{\partial y}{\partial z_{n}})^{T}$，则

$$
\frac{dy}{dw_{ij}} = \frac{\partial y}{\partial z_{1}} \frac{\partial z_{1}}{\partial w_{ij}} + \frac{\partial y}{\partial z_{2}} \frac{\partial z_{2}}{\partial w_{ij}} + \cdots + \frac{\partial y}{\partial z_{n}} \frac{\partial z_{n}}{\partial w_{ij}} = \frac{\partial y}{\partial z_{j}}\frac{\partial z_{j}}{\partial w_{ij}} = \frac{\partial y}{\partial z_{j}}x_{i} = x_{i}\frac{\partial y}{\partial z_{j}}
$$

因此：

$$
\frac{dy}{dW} = \begin{bmatrix}
x_{1}\frac{\partial y}{\partial z_{1}} & x_{1}\frac{\partial y}{\partial z_{2}} & \ldots & x_{1}\frac{\partial y}{\partial z_{n}} \\
x_{2}\frac{\partial y}{\partial z_{1}} & x_{2}\frac{\partial y}{\partial z_{2}} & \ldots & x_{2}\frac{\partial y}{\partial z_{n}} \\
\vdots & \vdots & \ddots & \vdots \\
x_{m}\frac{\partial y}{\partial z_{1}} & x_{m}\frac{\partial y}{\partial z_{2}} & \ldots & x_{m}\frac{\partial y}{\partial z_{n}}
\end{bmatrix} = x \frac{dy}{dz}^{T}
$$

### 变量定义

设定

$$
W = \begin{bmatrix}
w_{11} & w_{12} & \ldots & w_{1n} \\
w_{21} & w_{22} & \ldots & w_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
w_{m1} & w_{m2} & \ldots & w_{mn}
\end{bmatrix}
\quad
x = \begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}
\quad
b = \begin{bmatrix}
b_{1} \\
b_{2} \\
\vdots \\
b_{m}
\end{bmatrix}
\quad
\hat{z} = \begin{bmatrix}
\hat{z}_{1} \\
\hat{z}_{2} \\
\vdots \\
\hat{z}_{m}
\end{bmatrix}
$$

$z = W x + b$，即：

$$
z = \begin{bmatrix}
z_{1} \\
z_{2} \\
\vdots \\
z_{m}
\end{bmatrix} = \begin{bmatrix}
w_{11} & w_{12} & \ldots & w_{1n} \\
w_{21} & w_{22} & \ldots & w_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
w_{m1} & w_{m2} & \ldots & w_{mn}
\end{bmatrix} \cdot \begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix} + \begin{bmatrix}
b_{1} \\
b_{2} \\
\vdots \\
b_{m}
\end{bmatrix} = \begin{bmatrix}
w_{11} x_{1} + w_{12} x_{2} + \cdots + w_{1n} x_{n} + b_{1} \\
w_{21} x_{1} + w_{22} x_{2} + \cdots + w_{2n} x_{n} + b_{2} \\
\vdots \\
w_{m1} x_{1} + w_{m2} x_{2} + \cdots + w_{mn} x_{n} + b_{m}
\end{bmatrix}
$$

### 雅可比矩阵计算

若 $z$ 视为 $x = (x_1, x_2, \cdots, x_n)$ 的多元向量值函数，则 $\frac{dz}{dx}$ 的雅可比矩阵为：

$$
f'(x) = \frac{dz}{dx} = \begin{bmatrix}
w_{11} & w_{12} & \cdots & w_{1n} \\
w_{21} & w_{22} & \cdots & w_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
w_{m1} & w_{m2} & \cdots & w_{mn}
\end{bmatrix} \in \mathbb{R}^{m \times n}
$$

若 $z$ 视为 $b = (b_1, b_2, \cdots, b_m)$ 的多元向量值函数，则 $\frac{dz}{db}$ 的雅可比矩阵为：

$$
f'(b) = \frac{dz}{db} = \begin{bmatrix}
1 & 0 & \cdots & 0 \\
0 & 1 & \cdots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \cdots & 1
\end{bmatrix} \in \mathbb{R}^{m \times m}
$$

若 $z$ 视为 $W = (w_{11}, w_{12}, \cdots, w_{1n}, \cdots, w_{m1}, w_{m2}, \cdots, w_{mn})$ 的多元向量值函数，则 $\frac{dz}{dW}$ 的雅可比矩阵为：

$$
f'(W) = \frac{dz}{dW} = \begin{bmatrix}
x_{1} & \cdots & x_{n} & 0 & \cdots & 0 & \cdots & 0 & \cdots & 0 \\
0 & \cdots & 0 & x_{1} & \cdots & x_{n} & \cdots & 0 & \cdots & 0 \\
\vdots & & & & & & \ddots & & & \vdots \\
0 & \cdots & 0 & 0 & \cdots & 0 & \cdots & x_{1} & \cdots & x_{n}
\end{bmatrix}
$$
