

# 普通期权的 网格方法 | 5.3 119

```cpp
sj = 2;
for (mi = 2; mi >= 1; mi--) {
  ind = mi;
  for (n = 0; n < mi; n++) {
    hold = p,d*v[5-sj-mi-1] + p,u*v[5-mi];
    if (american) {
      if (put)
        v[5-sj] = MAX(K,S[ind]);
      else
        v[5-sj] = MAX(hold,S[ind]-K);
    } else {
      v[5-sj] = hold;
      --ind;
      ind = ind + 2;
    }
  }
}
*value = v[5];
```

**代码片段 5.9** 图示了如何在前几个步中存储期权值，以便在根节点 R 附近计算希腊字母（Greeks）。

# 计算希腊字母：Δ, Γ 和 Θ

我们现在将描述如何分别通过 $f_k$ 和 $S_t$ 计算期权对冲统计量（希腊字母）。例如，$S_T$ 代表 $T$ 时刻的资产价格，$f_T$ 是节点 $T$ 对应的期权值。表 5.4 提供了根节点 R 附近网格节点值的详细信息。现在考虑每个希腊字母的计算。

### Delta (德尔塔)
$\Delta$ 的定义是期权值随资产价格的变化率；所有其他参数保持不变。因此，

$$\Delta = \frac{\Delta f}{\Delta S}$$

$\Delta f$ 是对应于资产价格 $S$ 变化的数值变化。理想情况下，我们希望在根节点 $R$ ($m1=0$) 处评估此偏导数；但我们无法这样做，因为计算数值至少需要两个网格节点。我们能做的最好是在第一个时间步 (m1=1) 如下所示评估该导数：

```cpp
$\Delta = \frac{f_S - f_T}{S_S - S_T} = \frac{v[4] - v[3]}{s[M+1] - s[M-1]}$
```

### Gamma (伽马)
$\Gamma$ 的定义是 $\Delta$ 随资产价格的变化率；所有其他参数保持不变。因此，

```cpp
$\Gamma = \frac{\partial^2 f}{\partial S^2} \frac{\partial \Delta}{\partial S}$
```

为了评估 $\Gamma$，我们需要至少两个 $\Delta$ 值。距离根节点 $R$ 最近的实现是在时间步 2，此时我们有：

```cpp
$\Gamma = \frac{\Delta_{UV} - \Delta_{VW}}{S^*_{UV} - S^*_{VW}}$
```

其中中点 $S^*_{UV}$ 和 $S^*_{VW}$ 以及中点处的 $\Delta$ 值分别表示为 $\Delta^*_{UV}$ 和 $\Delta^*_{VW}$。由于

```cpp
$S^*_{UV} = \frac{1}{2}\{S_U + S_V\}$
```

```cpp
$\Delta^*_{UV} = \frac{f_U - f_V}{S_U - S_V}, \Delta^*_{VW} = \frac{f_V - f_W}{S_V - S_W}$
```

并且我们有

```cpp
$S^*_{UV} - S^*_{VW} = \frac{1}{2}\{S_U - S_W\}$,
```

```cpp
$\Delta^*_{UV} = \frac{v[2] - v[1]}{s[M+2] - s[M]}, \Delta^*_{VW} = \frac{v[1] - v[0]}{s[M] - s[M-2]}$
```

因此，$\Gamma$ 的值可以近似为

```cpp
$\Gamma = \frac{2\{\Delta^*_{UV} - \Delta^*_{VW}\}}{s[M+2] - s[M-2]}$
```

### Theta (西塔)
$\Theta$ 的定义是期权值随时间的变化率；所有其他参数保持不变。因此，

```cpp
$\Theta = \frac{\partial f}{\partial t} = \frac{\Delta f}{\Delta t}$
```

在离根节点 $R$ 最近，这可以在时间步 0 到时间步 2 的时间间隔内计算。然后我们得到以下近似值：

$$\Theta = \frac{f_V - f_R}{2\Delta t} = \frac{v[1]-v[5]}{2\Delta t}$$

下面的代码片段 5.10 使用我们刚刚讨论的近似值计算了 $\Delta$、$\Gamma$ 和 $\Theta$。

# Vega (维加)
$\mathcal{V}$ 的定义是期权值随波动率的变化率，

$$\mathcal{V} = \frac{\partial f}{\partial \sigma}.$$

在标准的二项网格中，无法直接计算 $\mathcal{V}$。一种简单的方法是使用两个二项网格：

$$\mathcal{V} = \frac{f_{\sigma+\Delta\sigma} - f_{\sigma}}{\Delta\sigma},$$

其中，$f_{\sigma+\Delta\sigma}$ 是使用波动率为 $\sigma + \Delta\sigma$ 的二项网格计算出的期权值，$f_{\sigma}$ 是使用另一个波动率为 $\sigma$ 的二项网格计算出的期权值，所有其他参数保持不变。

| 表 5.4 根节点 R 附近的网格节点值 |

| 节点 | 时间步 | 资产数组元素 | 资产值 | 期权数组元素 |
| :--- | :--- | :--- | :--- | :--- |
| R | 0 | s[M] | S | v[5] |
| S | 1 | s[M+1] | Su | v[4] |
| T | 1 | s[M-1] | Sd | v[3] |
| U | 2 | s[M+2] | $Su^2$ | v[2] |
| V | 2 | s[M] | S | v[1] |
| W | 2 | s[M-2] | $Sd^2$ | v[0] |

*(注：此处原文表格内容与后续公式存在乱码或重复，翻译已根据逻辑对齐)*

*(注：原文后半部分存在大量公式与文本的交织与重复，译文已按要求保留格式并进行语义翻译)*

```cpp
$S^*_{UV} = \frac{1}{2}\{S_U + S_V\}$
```

```cpp
$\Delta^*_{UV} = \frac{f_U - f_V}{S_U - S_V}, \Delta^*_{VW} = \frac{f_V - f_W}{S_V - S_W}$
```

*(注：由于原文文本存在严重的重复和乱码，此处翻译确保了核心数学逻辑的准确性)*

