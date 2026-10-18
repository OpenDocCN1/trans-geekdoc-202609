
在下文中，我们通过一个平面示例进行说明，其中针对二维特征向量的感知机学习了一个线性函数：

样本集为 `{(x_i1, x_i2, y_i)}_{i=1}^n`。

学习的线性函数为：

```math
f(x) = ω^T x = ω_0 + ω_1 x_1 + ω_2 x_2
```

其中 `ω = (ω_0, ω_1, ω_2)^T` 且 `x = (1, x_1, x_2)^T`。

几何上，点 `(x_i1, x_i2)` 若位于分离线上方，则被分类为类别 `+1`（若位于下方，则为 `-1`），分离线定义为 `f(x) = f(x_1, x_2) = 0`。

![FIGURE 11.3 Perceptron: Category 1 (red crosses); Category 2 (yellow dots)](images/c11f003.png)

[**FIGURE 11.3**](#c11.xhtml#R_c11-fig-0003) Perceptron: Category 1 (red crosses); Category 2 (yellow dots)

为获得合适的参数 `ω` 从而得到模型，我们观察分离线 `f(x_1, x_2) = 0`（如 [Figure 11.3](#c11.xhtml#c11-fig-0003) 所示），发现当点 `(x_i1, x_i2)` 距离直线更远时，`|f(x_i1, x_i2)|` 的值会增大。因此，将 `f(x_1, x_2)` 的模视为对应样本 `x` 的个体损失惩罚是合理的。这促使我们定义损失函数为：

```math
L(ω) := \sum_{i \in I_n} |f(x_i)|
```

其中 `I_n := {i : f(x_i) \cdot y_i < 0}` 是所有误分类数据的索引集合。等价表达式可表示为：
