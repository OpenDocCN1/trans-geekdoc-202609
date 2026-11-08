
其中 `D^{(l)}` ![Equation](images/F000248si37.png) 包含隐藏层激活函数相对于预激活输入的偏导数。该矩阵通常是对角的，因为激活函数通常以逐元素的方式操作。`W^{T(l+1)}` ![Equation](images/F000248si38.png) 项来源于 `a^{(l+1)}(h^{(l)}) = W^{(l+1)} h^{(l)} + b^{(l+1)}` ![Equation](images/F000248si39.png) 这一事实。因此，第 `l` 层网络参数的第 `k` 个向量的梯度可以利用以下形式的矩阵乘积计算

$\\frac{\\partial L}{\\partial\\mathbf{\\theta}\_{k}^{(l)}} = - \\mathbf{H}\_{k}^{({l - 1})}\\mathbf{D}^{(l)}\\mathbf{W}^{T{({l + 1})}}\\cdots\\mathbf{D}^{(L)}\\mathbf{W}^{T{({L + 1})}}\\Delta^{({L + 1})}.$

![Equation](images/F000248si40.png)

给定这些方程，`f(x)` ![Equation](images/F000248si41.png) 的定义，一个损失函数，以及任何正则化项，以这种通用方式表述的深度网络可以使用梯度下降进行优化。`Δ^{(l)}` ![Equation](images/F000248si42.png) 的递归定义反映了算法如何将信息从损失向后传播。
