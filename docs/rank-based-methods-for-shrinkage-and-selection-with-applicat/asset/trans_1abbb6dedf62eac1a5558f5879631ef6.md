

![](img/f3b106d7e76ae3afcec8895afa28732c_148_0.png)

图 3.2 使用最优 c 和 URE 的缩减 R-估计器的 ADRE。

**证明：** 找出以下式子的根即可：

```
$$\frac{\partial \text{ADL}_2\text{-risk}(\hat{\delta}_n^{\text{ShrinkageR}}(c))}{\partial c} = \eta^2 \left[ 2c - 2(1 - c)\Delta^2 \right] = 0$$
```

这将导出 \(c = \Delta^2 / (1 + \Delta^2)\) 作为最优值。

因此，

```
$$\text{ADL}_2\text{-risk}(\hat{\delta}_n^{\text{ShrinkageR}}(c_{\text{opt}})) = \eta^2 \frac{\Delta^2}{1 + \Delta^2},$$
```

并且，由公式 (3.1.5) 可得出结论

```
$$\text{ADRE}(\hat{\delta}_n^{\text{ShrinkageR}}(c_{\text{opt}}) : \hat{\theta}_n^{\text{UR}}) = 1 + \frac{1}{\Delta^2}.$$
```

此外，

```
$$\text{ADL}_2\text{-risk}(\hat{\theta}_n^{\text{UR}}) - \text{ADL}_2\text{-risk}(\hat{\delta}_n^{\text{ShrinkageR}}(c_{\text{opt}})) = \frac{\eta^2}{1 + \Delta^2} \quad \forall \Delta^2.$$
```

因此，我们得出结论：\(\hat{\theta}_n^{\text{ShrinkageR}}(c_{\text{opt}})\) 优于 \(\hat{\theta}_n^{\text{UR}}\)。图 3.2 显示了不同 \(\Delta^2\) 值的 ADRE 函数，这证实了上述结果。

## 3.4 脊型 R-估计器的 $\theta$

我们在上一节中考察了使用因子 $c$ 的一般缩减估计器。作为缩减 R-估计器的一个特例，令 $c = 1/(1+\lambda)$，$\lambda > 0$，并使用此来定义位置参数的脊型 R-估计器如下

\(\hat{\theta}^{\text{ridgeR}}_n(\lambda) = \frac{1}{1 + \lambda} \hat{\theta}^{\text{UR}}_n.\)

**定理 3.4** 在局部备择假设 $K_{(n)}$ 下，$\theta$ 的脊型 R-估计器（即 $\hat{\theta}^{\text{ridgeR}}_n(\lambda)$）的 ADB、ADV 和 ADL$_2$-风险为

ADB \(\left(\hat{\theta}^{\text{ridgeR}}_n(\lambda)\right) = -\eta \frac{\lambda}{1 + \lambda} \Delta,$
ADV \(\left(\hat{\theta}^{\text{ridgeR}}_n(\lambda)\right) = \eta^2 \frac{1}{(1 + \lambda)^2},$
ADL$_2$-风险 \(\left(\hat{\theta}^{\text{ridgeR}}_n(\lambda)\right) = \eta^2 \frac{1}{(1 + \lambda)^2} (1 + \lambda^2 \Delta^2).$

**证明：** 该结果可通过在定理 3.3 中考虑 $c = 1/(1 + \lambda)$ 而轻易得出。

求解

\(\frac{d \text{ADL}_2\text{-risk} \left( \hat{\theta}^{\text{ridgeR}}_n(\lambda) \right)}{d\lambda} = \eta^2 \frac{2\lambda \Delta^2(1 + \lambda) - 2(1 + \lambda^2 \Delta^2)}{(1 + \lambda)^3}
= \eta^2 \frac{2\lambda \Delta^2 - 2}{(1 + \lambda)^3} = 0 \quad (3.4.1)\)

得出 $\lambda_{opt} = \Delta^{-2}$。然后，对于 $\lambda_{opt}$，ADL$_2$-风险由下式给出

\(\text{ADL}_2\text{-risk} \left( \hat{\theta}^{\text{ridgeR}}_n(\lambda_{opt}) \right) = \eta^2 \frac{\Delta^2}{1 + \Delta^2}.\)

$\hat{\theta}^{\text{UR}}_n$ 和 $\hat{\theta}^{\text{ridgeR}}_n(\Delta^{-2})$ 的 ADL$_2$-风险比值由 $\Delta^2/(1 + \Delta^2)$ 给出，适用于 $\Delta^2 \in \mathbb{R}^+$。由此可见，由

\(\text{ADRE}\left( \hat{\theta}^{\text{ridgeR}}_n(\lambda_{opt}) : \hat{\theta}^{\text{UR}}_n \right) = 1 + \frac{1}{\Delta^2}. \quad (3.4.2)\)

可知 $\hat{\theta}^{\text{ridgeR}}_n(\lambda_{opt})$ 优于 $\hat{\theta}^{\text{UR}}_n$。

表 3.1 显示了不同 $\Delta^2$ 值的 ADRE 值。它证实了脊估计与无约束 R-估计相比的更好性能。

**表 3.1** 不同 $\Delta^2$ 值的脊 ADRE 值

| $\Delta^2$ | 0 | 0.01 | 0.05 | 0.1 | 0.5 | 1 | 2 | 5 | 10 | 20 | 50 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ADRE | $\infty$ | 101 | 21 | 11 | 3 | 2 | 1.5 | 1.2 | 1.1 | 1.05 | 1.02 |

## 3.5 $\theta$ 的预检验 R-估计器

在统计文献中，Bancroft (1944, 1964, 1965) 引入了参数的预检验估计，用于在怀疑对感兴趣参数存在某些“不确定先验信息”（UPI）时估计模型参数。该方法涉及基于适当统计量对 UPI 进行统计检验，并决定是否接受模型参数。

此处考虑由原假设 $\mathcal{H}_0 : \theta = 0$ 表示的 UPI。如果怀疑 $\theta$ 为 0，则应使用受限 R-估计器（$\hat{\theta}_n^{\text{RR}} = 0$）。在实际中，关于此先验信息 $\theta = 0$ 可能存在一定程度的不确定性。关于 UPI 的这种疑虑可以通过使用“费雪方案”来消除，即检验原假设 $\mathcal{H}_0 : \theta = 0$ 与备择假设 $\mathcal{H}_A : \theta \neq 0$（或局部备择 $K_{(n)} : \theta = n^{-1/2}\delta$，其中 $\delta$ 为固定值）。基于该检验结果，根据 $\mathcal{H}_0$ 的拒绝或接受，我们选择 $\hat{\theta}_n^{\text{UR}}$ 或 $\hat{\theta}_n^{\text{RR}}$。因此，遵循 Bancroft (1944)，我们引入预检验 R-估计器（PTRE），记为 $\hat{\theta}_n^{\text{PTR}}(\alpha)$，如下

$\hat{\theta}_n^{\text{PTR}}(\alpha) = \hat{\theta}_n^{\text{UR}} I(\mathcal{L}_n > \chi_1^2(\alpha)) \quad (3.5.1)$

其中 $\mathcal{L}_n$ 是用于检验 $\mathcal{H}_0 : \theta = 0$ 的检验统计量，定义为

$\mathcal{L}_n = \frac{n(\hat{\theta}_n^{\text{UR}})^2}{\hat{\eta}^2}. \quad (3.5.2)$

在原假设下，$\mathcal{L}_n$ 服从具有一个自由度（d.f.）的卡方分布，而 $\chi_1^2(\alpha)$ 是具有一个自由度的中心 $\chi^2$ 分布的 $\alpha$ 水平上临界值。如果 $\alpha = 1$，则始终选择 $\hat{\theta}_n^{\text{UR}}$；如果 $\alpha = 0$，则选择 $\hat{\theta}_n^{\text{RR}}$。由于 $0 < \alpha < 1$，在重复样本中，$\hat{\theta}_n^{\text{PTR}}$ 将产生 $\hat{\theta}_n^{\text{UR}}$ 和 $\hat{\theta}_n^{\text{RR}}$ 的组合。请注意，PTRE 过程仅导致两个值的选择，即 $\hat{\theta}_n^{\text{UR}}$ 或 $\hat{\theta}_n^{\text{RR}}$。此外，PTRE 依赖于显著性水平 $\alpha$。

**注释 3.1** 对于检验统计量，我们需要 $\hat{\eta}$。一个一致估计量是中位数绝对偏差（MAD），如在第 1 章中讨论的那样。更一般地，我们先前表明

$\eta^2 = \frac{A_\phi^2}{\gamma^2(\phi, f)}, \quad \gamma(\phi, f) = \int_{-\infty}^{\infty} f(x) d\Phi(F(x))$.

为了估计 $\gamma(\phi, f)$，我们使用

$\hat{\gamma}(\phi, f) = \int_{-\infty}^{\infty} f_n(x) d\Phi(F_n(x)) \quad (3.5.3)$

其中 \( f_n(x) \) 和 \( F_n(x) \) 分别是 \( f(x) \) 和 \( F(x) \) 的估计量。然后，

```
\(\hat{\eta}^2 = \frac{A_n^2}{\hat{\gamma}^2(\phi, f)}, \quad A_n^2 = n^{-1} \sum_{i=1}^n a_n^+(i)^2.\) (3.5.4)
```

还要注意的是

```
\(\frac{\sqrt{n}\hat{\theta}_n^{UR}}{\hat{\eta}} \sim N(0, 1),\) (3.5.5)
```

并且，由公式 (3.2.3) 可知

```
\(\frac{T_n(0)}{A_n} \sim N(0, 1).\) (3.5.6)
```

然后，

```
\(\mathcal{L}_n = \frac{T_n^2(0)}{A_n^2} = \left( \frac{\sqrt{n}\hat{\theta}_n^{UR}}{\hat{\eta}} \right)^2 + o_p(1).\) (3.5.7)
```

此结果将在后续定理中使用。

### 定理 3.5 在局部备择假设下，\(\theta\) 的预检验 R-估计器的 ADB 和 ADL$_2$-风险如下：

```
\(\text{ADB}(\hat{\theta}_n^{PTR}(\alpha)) = -\eta \Delta \mathcal{H}_3(\chi_1^2(\alpha), \Delta^2), \quad \text{ADL}_2\text{-risk}(\hat{\theta}_n^{PTR}(\alpha)) = \eta^2 \rho_{PT}(\alpha, \Delta^2),\)
```

where

```
\(\rho_{PT}(\alpha, \Delta^2) = 1 - \mathcal{H}_3(\chi_1^2(\alpha), \Delta^2) + \Delta^2 \left( 2\mathcal{H}_3(\chi_1^2(\alpha), \Delta^2) - \mathcal{H}_5(\chi_1^2(\alpha), \Delta^2) \right) .\)
```

这里，\(\mathcal{H}_\nu(\cdot, \Delta^2)\) 是具有 \(\nu\) 个自由度和非中心性参数 $\Delta^2$ 的 \(\chi^2\) 分布的累积分布函数（c.d.f.）。

**证明：** 如果将 PTRE 的定义与缩减 R-估计器相结合，可以轻易发现选择 \(c = I(\mathcal{L}_n > \chi_1^2(\alpha))\) 证实 PTRE 是缩减 R 族的一个成员。有人可能认为，通过将此 \(c\) 的选择代入定理 3.3 可以轻易得出该估计器的 ADB 和 ADL$_2$-风险，但这里的问题是 \(c\) 不是固定的。它是一个随机变量。因此，我们必须遵循公式 (3.1.3) 和 (3.1.4)。公式 (3.5.1) 中的 PTRE 可以重写为

