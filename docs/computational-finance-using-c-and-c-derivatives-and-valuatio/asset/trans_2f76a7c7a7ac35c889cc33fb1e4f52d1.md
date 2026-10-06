
# 第110 章 | 5 单资产美式期权

Evans 等人 (2000) 指出，从对数正态分布中抽变量 X 的前两个阶矩如下。

## 对数正态均值

```
$E[X] = \exp(\eta + v^2/2),$ (5.3.1)
```

代入 $\eta$ 和 $v^2$ 得

```
$E[X] = \exp\left\{\left(r - \frac{\sigma^2}{2}\right)\Delta t + \frac{\sigma^2}{2}\Delta t\right\}. (5.3.2)
```

## 对数正态方差

$Var[X] = E[(X - E[X])^2] = E[X^2] - (E[X])^2 = \exp(2\eta + v^2)\{\exp(v^2) - 1\}, (5.3.3)$

代入 $\eta$ 和 $v^2$ 得

```
$Var[X] = \exp\left\{2r\left(r - \frac{\sigma^2}{2}\right)\Delta t + \sigma^2\Delta t\right\}.
```

可以简化为

```
$Var[X] = \exp\{2r\Delta t\{\exp(\sigma^2\Delta t) - 1\}\}. (5.3.4)
```

由于我们可以假设 X 的期望值以无风险利率 $r$ 增长，我们也可以写为：

```
$E[X] = \exp(r\Delta t). (5.3.5)
```

上述结果用于在已知时间 $t$ 时的资产价格 $S_t$ 的情况下，寻找资产价格分布 $S_{t+\Delta t}$ 的前两个阶矩。为了这一点，我们利用（证明见附录 C.3）对于随机变量 $G$，我们有：

```
$E[a + bG] = E[a + bE[G]]$, and $Var[a + bG] = b^2Var[G],$
```

其中 $a$ 和 $b$ 是常数。将此应用于变量 $G$

```
$E[X] = E\left[\frac{S_{t+\Delta t}}{S_t}\right] = \frac{1}{S_t}E[S_{t+\Delta t}], (5.3.6)
```

以及

```
$Var[X] = Var\left[\frac{S_{t+\Delta t}}{S_t}\right] = \frac{1}{S_t^2}Var[S_{t+\Delta t}], (5.3.7)
```

其中我们使用了 $a = 0$ 和 $b = \frac{1}{S_t}$。注意：也很容易证明

```
$Var[S_{t+\Delta t}] = Var[\Delta S]. (5.3.8)
```

## 欧式期权的晶格方法 第 5.3 节

其中时间间隔 $\Delta t$ 内资产价格的变化用 $\Delta S = S_{t+\Delta t} - S_t$ 表示。这一基础结果有时在不经证明的情况下使用，参见 Hull (1997) 第 344 页。证明非常简单：

$$Var[S_{t+\Delta t}] = Var[S_t + \Delta S] = Var[\Delta S].$$

其中我们使用了

$$Var[a + bG] = b^2Var[G], 这次这里 $a=0$ 且 $b=1.$$

为了得到 $S_{t+\Delta t}$ 的均值和方差的表达式，我们只需将方程 (5.3.5) 代入方程 (5.3.6) 即可

$$E[S_{t+\Delta t}] = S_t \exp(r\Delta t). (5.3.9)$$

而将方程 (5.3.4) 代入方程 (5.3.7) 得到

$$Var[S_{t+\Delta t}] = S_t^2 \exp(2r\Delta t)\{\exp(\sigma^2\Delta t) - 1\}. (5.3.10)$$

由于我们使用二叉晶格对资产价格运动进行建模，任何给定节点的资产价格 $S_t$ 在下一步 $\Delta t$ 内仅允许价值向上跳跃或向下跳跃。我们假设新的资产价格 $S_{t+\Delta t}$ 在向上跳跃时为 $S_tu$，在向下跳跃时为 $S_td$；其中 $u$ 和 $d$ 是适用于所有晶格的常数。如果我们定义向上跳跃的概率为 $p$，那么（根据定义）向下跳跃的概率为 $1-p$。

现在我们有了用于匹配对数正态分布前两个阶矩的晶格参数。这得到了我们的以下方程：

$$E[S_{t+\Delta t}] = p_tu + (1-p)S_td = S_t \exp(r\Delta t). (5.3.11)$$

对应的方差方程需要稍多计算

$$Var[S_{t+\Delta t}] = E[(S_{t+\Delta t})^2] - (E[S_{t+\Delta t}])^2. (5.3.12)$$

由于

$$E[(S_{t+\Delta t})^2] = pS_tu^2 + (1-p)S_td^2 = S_t^2\{u^2 + (1-p)d^2\} (5.3.13)$$

并且根据方程 (5.3.9)

$$E[(S_{t+\Delta t})^2] = (S_t \exp(r\Delta t))^2 = S_t^2 \exp(2r\Delta t). (5.3.14)$$

我们可以将方程 (5.3.13) 和方程 (5.3.14) 代入方程 (5.3.12) 得到

$$Var[S_{t+\Delta t}] = S_t^2 \exp(2r\Delta t)\{\exp(\sigma^2\Delta t) - 1\}.$$

（注：由于原文后半部分存在大量重复的 OCR 错误，此处已根据逻辑进行清理并翻译）
