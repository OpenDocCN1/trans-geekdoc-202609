
计算组合 `x*`, `y*`, `z*`, `ϕ*`, `w*`，其结果为联合概率的最大值：

```
P(x, y, z, ϕ, w) = P(z|y, x, ϕ, w)P(y|x, ϕ, w)P(ϕ|x, w)P(x|w)P(w) = P(z|y)P(y|x)P(ϕ|x, w)P(x)P(w),
```

这是贝叶斯网络（BN）施加的因子分解。

![Figure 15.28 (A) The Bayesian network of Example 15.4; (B) its moralized version, where the two parents of ϕ have been connected; and (C) a possible factor graph.](images/B9780443292385000214/gr028.jpg)

**Figure 15.28** (A) [Example 15.4](#Chp015_755-803_B9780443292385000214.xhtml#enun0115)的贝叶斯网络；(B) 其道德化版本，其中 `ϕ` 的两个父节点已被连接；(C) 一个可能的因子图。

为了应用最大乘积规则，我们首先对图进行道德化，然后形成因子图版本，如 [Figs. 15.28](#Chp015_755-803_B9780443292385000214.xhtml#f0165) B 和 C 所示。因子节点实现以下势函数（因子函数）：

```
f_a(x, y) = P(y|x)P(x),
f_b(y, z) = P(z|y),
f_c(ϕ, x, w) = P(ϕ|x, w)P(w),
```

显然：

```
P(x, y, z, ϕ, w) = f_a(x, y)f_b(y, z)f_c(ϕ, x, w).
```

注意，在这种情况下，归一化常数 `Z = 1`。因此，根据之前的定义，这些因子函数取值为：
