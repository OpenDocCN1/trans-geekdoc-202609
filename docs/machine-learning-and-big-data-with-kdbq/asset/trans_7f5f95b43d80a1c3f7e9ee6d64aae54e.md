

# 傅叶变换 305

复数的三角形式给如下：

```
z = r(cos\phi + i\sin\phi). (15.11)
```

我们实现了极坐标分解，它返回一个包含半径和角度的字典：

```
.quantQ.polar:{[cx]
// cx -- 复数
// 半径部分
r: sqrt cx.re^2 + cx.im^2;
// 角度部分
phi: atan2(cx.im, cx.re);
if (cx.re == 0 && cx.im == 0) phi = 0;
else if (cx.im > 0) phi = 0.5 * .quantQ.pi;
else if (cx.im < 0) phi = -0.5 * .quantQ.pi;
'radius angle!(r,phi);
};
```

让我们来计算几个例子：

```
.quantQ.complex.polar[cx1]
```

| 半径 | 1 |
| :--- | :--- |
| 角度 | 0 |

```
.quantQ.complex.polar[cx2]
```

| 半径 | 1 |
| :--- | :--- |
| 角度 | 1.570796 |

```
.quantQ.complex.polar[re:0, im:0]
```

| 半径 | 0 |
| :--- | :--- |
| 角度 | 0 |

为了完整起见，我们提供了一个函数，利用三角形式将极坐标转换为标准形式（直角形式）：

```
.quantQ.complex.polar2Canonical:{[polar]
// polar -- 极坐标形式的复数
:re = polar.radius * cos(polar.angle);
im = polar.radius * sin(polar.angle);
};
```

并验证其功能：

```
.quantQ.complex.polar2Canonical[radius:2, angle:(0.25+3.14152)]
```

# 306 数据科学

```
re | 1.414239
im | 1.414188
```

同样定义欧拉公式也是方便的：

$e^{i\phi} = \cos\phi + i\sin\phi, \quad (15.12)$

如下：

```
.quantQ.complex.realExp:[phi]
// phi -- 角度分
:re = cos(phi);
im = sin(phi);
);
```

得到：

```
.quantQ.complex.realExp[0.25+3.14152]
```

```
re | 0.7071196
im | 0.7070939
```

该函数仅针对实数参数定义，然后我们使用名称 RealExp。
当欧拉公式被视为复数的指数时，它是非常有用的：

$u = e^c = e^{a+bi} = e^a * e^{bi}, \quad (15.13)$

这随后基于指数函数的变换的基础。因此，我们将复杂的 exp 逻辑实现为：

```
.quantQ.complex.exp:{[cx]
// cx -- 复数
:exp = exp(cx.re) * .quantQ.complex.realExp(cx.im);
};
```

并在上面进行说明：

```
.quantQ.complex.exp[cx1]
```

```
re | 2.718282
im | 0
```

以及

```
.quantQ.complex.exp[cx3]
```

```
re | 0.898172
im | 0.01535226
```

有了复数 exp 的实现，我们需要复数的等效对数。欧拉公式允许我们以直接的方法获得它：

$log(z) = log(re^{i\phi}) = log(r) + i\phi. \quad (15.14)$

# 傅叶变换

然而，这个解决方案并不是唯一的。歧义源于余弦和正弦函数的周期性，或者说来自复平面上的旋转 $e^{i\pi} = e^{3i\pi} = e^{5i\pi} = \dots$ 这导致了对数的多值定义：

$\log(z) = log(r) + i(\phi + 2\pi k) \text{ 其中 } k \in \mathbb{Z}. \quad (15.15)$

复对数函数有两个参数：第一个参数是复数 $z$，而第二个参数是上一个对话中定义的分支割 $k$。分支割的默认值为 0。

```
.quantQ.complex.log:{[cx,k]}
// cx 复数
// k 分支割
polar = .quantQ.complex.polar cx;
:re = log(polar.radius);
im = polar.angle + 2 * .quantQ.pi * k;
};
```

```
.quantQ.complex.log[cx1;0]}
```

| re | 0 | im | 0 |
| :--- | :--- | :--- | :--- |

```
.quantQ.complex.log[cx1;1]}
```

| re | 0 | im | 6.283185 |
| :--- | :--- | :--- | :--- |

最后，我们检查等式 $z = e^{\log z}$：

```
.quantQ.complex.exp[.quantQ.complex.log[cx1;1]]
```

| re | 1 | im | -2.449924 |
| :--- | :--- | :--- |

差异源于舍入误差。
复数对数的公式验证如下：

$\log(i) = \frac{\pi}{2}i. \quad (15.16)$

```
.quantQ.complex.log[cx2;0]}
```

| re | 0 | im | 1.570796 |
| :--- | :--- | :--- |

这被了。在实现代数概念时，值得提到准备一些等式以便测试。在我们看来，提供的等式适用于处理复数。

# 308 数据科学

最后，我们提供了一个非数学工具函数，将实数转换为复数定义：

```
.quantQ.complex.real2Complex:{[real]
// 实数
:re = real;
im = 0;
};
```

给出：

```
.quantQ.complex.real2Complex[1]
```

| re | 1 | im | 0 |
| :--- | :--- | :--- |

# 15.2 离散傅叶变换

我们现在有了处理复数的的形式。我们可以引入离散傅叶变换 (DFT)。DFT 是应用于采样点的傅叶分析的特例。我们从引入 DFT 开始，然后进行其离散版本。参考文献，建议读者阅读 Arfken (1985) 或 Flannery 等 (1988) 以获得更实用的方法。

傅叶变换由连续函数 $f(t)$ 组成，将其分解为频率分量 Bracewell (1986) 或 Grafakos (2008)。DFT 将函数从时域转换为频域。时域中的 DFT 仅仅是频域中的乘法。这是信号处理中非常有用的性质。DFT 比我们能负担的更多，因此我们将 DFT 解释为允许我们将时间分解为频率分量并领先频率。在金融时间序列中，这可能对应于均值回归。让我们定义 DFT。设 $f$ 为可积函数 $f : R \to C$，则其傅叶变换定义为：

```
f(\zeta) = \int_{-\infty}^{\infty} f(t)e^{-2\pi i\zeta t}dt \quad (15.17)
```

其中 $\zeta$ 为任意实数。变量 $\zeta$ 对应频率。让我们进一步定义逆 DFT，即从频域转换为时域：

```
f(t) = \int_{-\infty}^{\infty} f(\zeta)e^{2\pi i\zeta t}d\zeta \quad (15.18)
```

上述定义假设我们拥有 $f$ 在 $(-\infty, \infty)$ 的完整知识。在应用中，我们观察 $f$ 的等距样本 $f_0, f_1,\dots,f_{N-1}$。样本点可以是复数。DFT 可以被视为序列 $F_0, F_1, F_2,\dots,F_{N-1}$：

```
F_k = \sum_{n=0}^{N-1} f_n e^{\frac{2\pi kn}{N}} \quad (15.19)
```

DFT 的分量可以解释为输入序列与频率为 $\frac{k}{N}$ 的复正弦波的相关性。它过滤了给定频率幅的贡献。此外，每个系数 $F_k$ 都是编码 $\frac{2ik}{N}$ 原序列复周期分量 $e^n$ 的幅度和相位。DFT 定义在域 $k \in 0, 1, \dots, N-1$ 上。变换可以扩展到整个域，将序列视为 $N$ 周期的，即每 $N$ 个点重复一次。

让我们通过示例说明 DFT。首先，实现一个接受复数序列并返回一个 DFT 的函数：

```
.quantQ complex.dft:[complex n;k]
// 复数序列
// n 序列长度
// til 序列索引
// k DFT系数
:sum: .quantQ.complex.mult[csx;flip] .quantQ.complex.realExp neg (2 *
  .quantQ.pi * k * til)
);
```

然后迭代获取完整的 DFT 系数：

```
.quantQ.complex.dft:[csx]
// 要转换的复数序列
::quantQ.complex.dft[n til N] peach count csx;
);


注意使用 peach 在使用从线程查询 (q - s n) 时提供多线程处理。

让我们定义一个复数序列：

```
csSeries: flip 'reflip (0.2421429 0.3013791; 0.1102202)
- 0.9201851;0.6466032 0.1531531;0.8917427 0.3049351;0.0598165
- 0.2161336;0.7835583 0.1152005;0.244422 0.502301;0.236067
- 0.82064;0.4140276 0.2774816;0.9143396;0.6609365);
```

