
上述变换的物理解释是 `x`、`y` 对应于某点的笛卡尔坐标，而 `r`、`ϕ` 是其极坐标（图 14.3）。由公式 (14.14) 和 (14.15)，我们可以写出

```
r = x² + y²
```

```
ϕ = arctan(y / x)
```

将公式 (14.9) 调整以适应当前需求，并使用公式 (14.11)–(14.13)，我们得到

```
p_{x,y}(x,y) = (1 / 2π)(1 / 2) exp(-(x² + y²) / 2) * 2
             = (1 / √(2π)) exp(-x² / 2) * (1 / √(2π)) exp(-y² / 2)
```

其中我们用到了（问题 14.3）

```
|J(x,y;r,ϕ)| = 1/2
```

因此，我们已经证明了使用公式 (14.14) 和 (14.15) 中给出的变换，可以生成标准高斯分布的样本。

![Figure 14.3 (A) Relation of the Cartesian (x,y) to the polar coordinates (r,ϕ). (B, C) If r and ϕ are random variables following an exponential and a uniform in [0,2π] distribution, respectively, then x and y are independent and they both follow the standard Gaussian, as shown in (D) for the x-variable.](images/B9780443292385000202/gr003.jpg)

**图 14.3** (A) 笛卡尔坐标 (`x`,`y`) 与极坐标 (`r`,`ϕ`) 的关系。(B, C) 如果 `r` 和 `ϕ` 是随机变量，分别服从指数分布和 `[0,2π]` 上的均匀分布，则 `x` 和 `y` 相互独立，且均服从标准高斯分布，如 (D) 所示为 `x` 变量的情况。

一旦获得了标准高斯分布 `N(x|0, 1)` 的样本，一般高斯分布 `N(y|μ, σ²)` 的样本即可通过显而易见的变换得到

```
y = σx + μ
```
