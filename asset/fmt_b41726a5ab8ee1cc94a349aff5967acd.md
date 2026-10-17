
$$P_3 = \int_{0}^{2\pi} \int_{0}^{L} Z(x,\theta)^2 dx d\theta \quad (4152)$$

$$P_4 = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial X(x,\theta)}{\partial \theta}\right)^2 \frac{\partial X(x,\theta)}{\partial \theta} dx d\theta \quad (4153)$$

$$P_5 = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial X(x,\theta)}{\partial x}\right)^2 \frac{\partial X(x,\theta)}{\partial x} dx d\theta \quad (4154)$$

$$P_6 = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial X(x,\theta)}{\partial x}\right)^2 \frac{\partial Y(x,\theta)}{\partial \theta} dx d\theta \quad (4155)$$

$$P_7 = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial X(x,\theta)}{\partial x}\right)^2 \frac{\partial Y(x,\theta)}{\partial x} dx d\theta \quad (4156)$$

$$P_8 = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Y(x,\theta)}{\partial x}\right)^2 Z(x,\theta) dx d\theta \quad (4157)$$

$$P_9 = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Y(x,\theta)}{\partial \theta}\right)^2 \frac{\partial Y(x,\theta)}{\partial \theta} dx d\theta \quad (4158)$$

$$P_{10} = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Y(x,\theta)}{\partial \tilde{x}}\right)^2 \frac{\partial Y(x,\theta)}{\partial \tilde{x}} dx d\theta \quad (4159)$$

$$P_{11} = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Y(x,\theta)}{\partial \theta}\right)^2 Z(x,\theta) dx d\theta \quad (4160)$$

$$P_{12} = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Z(x,\theta)}{\partial \tilde{x}}\right)^2 \frac{\partial Z(x,\theta)}{\partial \theta} dx d\theta \quad (4161)$$

$$P_{13} = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Z(x,\theta)}{\partial \tilde{x}\theta}\right)^2 \frac{\partial Z(x,\theta)}{\partial \theta} dx d\theta \quad (4162)$$

$$P_{14} = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Z(x,\theta)}{\partial \tilde{x}^2}\right)^2 \frac{\partial Z(x,\theta)}{\partial \theta} dx d\theta \quad (4163)$$

$$P_{15} = \int_{0}^{2\pi} \int_{0}^{L} \left(\frac{\partial Z(x,\theta)}{\partial \tilde{x}^2}\right)^2 \frac{\partial Y(x,\theta)}{\partial \tilde{x}} dx d\theta \quad (4164)$$

$$N_1 = \frac{A_{11}}{2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial \tilde{x}}\right]^T \frac{\partial Y(x,\theta)}{\partial \tilde{x}} dx \tilde{x}d\theta + \frac{A_{12}}{2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right]^2 \left[\frac{\partial Y(x,\theta)}{\partial \theta}\right]^T dx \tilde{x}d\theta \quad (41665)$$

$$N_2 = \frac{A_{11}}{2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right]^2 \left[\frac{\partial Y(x,\theta)}{\partial \tilde{x}}\right]^T dx \tilde{x}d\theta + \frac{A_{12}}{2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial \tilde{x}}\right]^2 \left[\frac{\partial Y(x,\theta)}{\partial \theta}\right]^T dx \tilde{x}d\theta + A_{66} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial \tilde{x}}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right]^T \left[\frac{\partial Y(x,\theta)}{\partial \tilde{\theta}}\right]^T dx \tilde{x}d\theta \quad (41666)$$

通用圆柱形壳的受激振与自由振動

```
$N_3 = \frac{3A_{11}}{2R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial t}\right]^2 Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{11}}{R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Y(x,\theta)}{\partial \theta}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{11}}{2R^3} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial x}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial x}\right] \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{12}}{2R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial X(x,\theta)}{\partial x}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{66}}{R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial X(x,\theta)}{\partial x}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial x}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{66}}{2R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Y(x,\theta)}{\partial x}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{12}}{2R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Y(x,\theta)}{\partial x}\right]^2 Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{12}}{R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Y(x,\theta)}{\partial \theta}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial x}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{26}}{R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial x}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{11}}{R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial x}\right]^T \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right] Z(x,\theta) \text{d}x\text{d}\theta$
```

```
$+ \frac{A_{11}}{2R^2} \int_{0}^{2\pi} \int_{0}^{L} \left[\frac{\partial Z(x,\theta)}{\partial \theta}\right]^2 Z(x,\theta) \text{d}x\text{d}\theta$
```

(4.67)

为了计算方便，等式 (438) 转换为：

```
$\mathbf{I}\mathbf{q} + \mathbf{C}\dot{\mathbf{q}} + \mathbf{K}\mathbf{q} + \mathbf{N}\mathbf{q} = \mathbf{f}\cos(\Omega t)$
```

(4.68)

其中 $\mathbf{I}$ 是单位矩阵

```
$\mathbf{C} = \mathbf{M}^{-1}\mathbf{C}, \mathbf{K} = \mathbf{M}^{-1}\mathbf{K}, \mathbf{N} = \mathbf{M}^{-1}\mathbf{N}, \mathbf{f} = \mathbf{M}^{-1}\mathbf{f}$
```

(4.69)

FG 多孔结构

引入了以下无量纲参数：

```
$\omega^* = \Omega/\omega_0, \quad f_d = \frac{2f}{LRh\omega_0^2}$ (4.70)
```

其中 $\omega_0$ 表示 FG 多孔壳的基础阶频率。通过采用 Matcont 软件程序 [34] 执行伪弧长延续以获取非线性受激振动响应。

## 4.2 结果与讨论

接下来研究了具有 1:1 内共振的 FG 多孔圆柱壳的非线性受激振动。除非另有说明，几何和材料参数与 4.4.3 节相同。补充参数如下：

$$\epsilon = 0.0053, f_d = 0.0015.$$

根据 4.4.3 节，基础阶频率对应模 $(m=1, n=5)$。当激励频率等于模 $(m=1, n=5)$ 的自然频率时，驱动模 $Z_s(t)$ 被激发。1:1 共振可能发生在驱动模和伴随模之间，因为它们具有相同的自然频率。

为了准确高效地计算壳的非线性频率响应，应执行收敛性以确定模的数量。表 4.9 列出了不同的广义坐标组合。GC2 和 GC3 考虑了非对称模以及具有 $2 \times n$ 周向轴的模。

图 4.18 比较了不同广义坐标组合下 FG 圆柱壳的非线性频率响应。可以看到 GC2 和 GC3 的频率几乎重合。因此，GC 组合足以准确计算 FG 圆柱壳的非线性频率响应。

为了验证非线性受激振动的结果，针对简单支撑边界条件的等向性圆柱壳进行了对比研究如下：

### 表 4.9 广义坐标

| 广义坐标 |

| :--- |

| GC1 | $X_{1,0}^a, X_{1,1}^a, X_{1,2}^a, Y_{1,0}^b, Y_{1,1}^b, Y_{1,2}^b, Z_{1,0}^c, Z_{1,1}^c, Z_{1,2}^c$ |

| GC2 | $GC1 + Z_{1,0}^d, Z_{1,1}^e, Z_{1,2}^f$ |

| GC3 | $GC2 + Z_{3,2}^g$ |

![](img/90ed165a39fa708ec438fcda79319c25_140_0.png)

**图 4.18** 不同广义坐标组合下 FG 圆柱壳的非线性频率响应比较。(A) 驱动模 (B) 伴随模。

![](img/90ed165a39fa708ec438fcda79319c25_143_0.png)

**图 4.23** 具有不同孔隙率的光梯度多孔圆柱壳的激励振幅响应（--- 稳定解；-- 不稳定解；$e_1=0.5; \omega^*=1$）。

图 4.23 展示了具有不同孔隙率的 FG 多孔圆柱壳的激励振幅响应。当激励振幅较小时，驱动模式仅有一个稳定解。随着激励振幅的增加，稳定解发生分叉，且在靠近 0.01 处出现了另一个分支。随后，驱动模式的分支 1 变得不稳定。对于伴随模式，分支 1 始终为零。在同一分叉点处出现了分支 2。该分支 2 随着激励振幅的增加而增大。上述现象表明，1:1 内部共振的额外分支 2 的出现需要较大的激励振幅。可以看到，由于 PD-A 壳的分支 2 较先出现，PD-A 壳需要较低的激励振幅即可激发伴随模式的非零响应。

图 4.24 展示了具有不同孔隙系数的 FG 多孔圆柱壳的激励振幅响应。随着孔隙系数的增加，PD-A 壳 1:1 内部共振的激励阈值增加，PD-B 壳的阈值也增加。可以看到，PD-A 壳的最大孔位于壳的中表面，这增强了壳的刚度。然而，PD-B 壳的情况恰相反。孔隙系数对 PD-U 壳激励振幅响应的影响不显著。

图 4.25 和 4.26 分别展示了具有不同孔隙分布和系数的 FG 多孔圆柱壳在 $\omega^*=1$ 处的时间响应（对应图 4.21 中的分支 2）。显然，伴随模式与驱动模式之间的相位差为 $\pi/2$，这是行进波振动的典型特征。孔隙分布和孔隙系数主要影响时间响应的峰值，而对 FG 多孔圆柱形壳的振动周期和相位的影响不显著。

功能梯度多孔圆柱形壳的自由振动和受迫振动

![](img/90ed165a39fa708ec438fcda79319c25_144_0.png)

(A)

![](img/90ed165a39fa708ec438fcda79319c25_144_1.png)

![](img/90ed165a39fa708ec438fcda79319c25_144_2.png)

(B)

![](img/90ed165a39fa708ec438fcda79319c25_144_3.png)

![](img/90ed165a39fa708ec438fcda79319c25_144_4.png)

![](img/90ed165a39fa708ec438fcda79319c25_144_5.png)

(C)

**图 4.24** 具有不同孔隙系数的功能梯度多孔圆柱形壳的激励振幅响应（--- 稳定解；--- 不稳定解；$\omega^n=1$）：(A) PD-A；(B) PD-B；(C) PD-U。

FG 多孔复合结构

![](img/90ed165a39fa708ec438fcda79319c25_145_0.png)

**图 4.25** 具有不同孔隙分布的功能梯度多孔壳的时间响应（$e_1=0.5; \omega=1$）。

## 4.6 结论
