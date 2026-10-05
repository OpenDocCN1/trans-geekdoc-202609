

## C.2 贝叶传播方程

由于每个序列 $x = \bar{x}$ 的关联 $y \leftarrow \bar{x}$ 都是随机进行的，且独立于 $\Delta_{xx}$，因此根据等式 289g，我们有 $\langle\psi(y,x)\rangle_{y\leftarrow x} \approx 1/v$。更精确地说，由于我们将已经参考序列 $\bar{x}$ 关联到 $\tilde{y}$：

$$\Psi_y = \langle\psi(y,x)\rangle_{y\leftarrow x} = \frac{m-1}{mv-1}\delta_{y,\tilde{y}} + \frac{m}{mv-1}(1-\delta_{y,\tilde{y}}). \quad (292)$$

因此：

$$\langle\tilde{\psi}(y)\rangle_\psi = \delta_{\tilde{y},y}B(0) + \Psi_y \sum_{k=1}^s B(k) \left( \sum_{x\in S} \Delta_{xx}=k} 1 \right) \quad (293)$$
$$= \delta_{\tilde{y},y}B(0) + \Psi_y \sum_{k=1}^s B(k) \langle n_k\rangle_S,$$

其中 $n_k$ 是 $S$ 中与 $x$ 的汉明距离 $\Delta_{xx}=k$ 的序列 $x$ 的数量。由于序列是随机采样的，数字 $n_1, ..., n_s$ 服从多元超几何分布：

$$P(n_1, ..., n_s) = \frac{\prod_{k=1}^s \binom{v-1}{n_k}}{\binom{mv-1}{s}} \quad (294)$$

该分布对以下项进行平均化：

$$\langle n_k\rangle_S = \frac{mv-1}{vs-1} \left( \frac{s}{k} \right) (v-1)^k = f \binom{s}{k}(v-1)^k, \quad (295)$$

其中

$$f = \frac{mv-1}{vs-1}. \quad (296)$$

因此：

$$\langle\tilde{\psi}(y)\rangle_\psi = \delta_{\tilde{y},y}B(0) + f \Psi_y \sum_{k=1}^s B(k) \left( \frac{s}{k} \right) (v-1)^k. \quad (297)$$

根据信念等式 286，我们看到：

$$\sum_{k=1}^s B(k) \left( \frac{s}{k} \right) (v-1)^k = \sum_{k=1}^s B(k) \left( \frac{s}{k} \right) (1-\epsilon) \left( 1 + \frac{\epsilon}{v} \right)^{s-k}$$
$$= \left[ 1 - \left( 1 - \epsilon + \frac{\epsilon}{v} \right)^s \right] = 1 - B(0), \quad (298)$$

得到：

$$\langle\tilde{\psi}(y)\rangle_\psi = \delta_{\tilde{y},y}B(0) + f \Psi_1 [1-B(0)]. \quad (299)$$

归一化常数为：

$$\langle Z_{\psi}\rangle_\psi = \sum_y \langle\tilde{\psi}(y)\rangle_\psi = B(0) + f [1-B(0)]. \quad (300)$$

## 附录：扩散过程中的相变

最后，我们得到 $Y$ 的平均信念：

$$\langle\bar{y}(y)\rangle_\psi = \frac{\langle\bar{y}(y)\rangle_\psi}{\langle Z_y\rangle_\psi} = \frac{\delta_{y,\bar{y}}B(0) + f\Psi_y[1-B(0)]}{B(0) + f[1-B(0)]} \quad (301)$$

我们有：

- 对于 $y = \bar{y}$
  $$\langle\bar{y}(\bar{y})\rangle_\psi = \frac{B(0) + f\frac{m-1}{mv-1}}[1-B(0)]}{B(0)+f[1-B(0)]} \quad (302)$$
- 对于 $y \neq \bar{y}$
  $$\langle\bar{y}(y)\rangle_\psi = f\frac{m}{mv-1}B(0) + f[1-B(0)] \quad (303)$$

**迭代层** 有两类平均消息：一种针对参考值 $\bar{y}$（等式 302），另一种针对 $y \neq \bar{y}$，且它们都通过 $B(0) = (1-\epsilon^s)$ 依赖于之前的信念。因此，较高层的平均信念结构与较低层等式 285 相同。我们接着定义了一个新的 $e'$：

$$1-e' = \frac{e'}{v} = \frac{\frac{(1-\epsilon^s)^s}{v} + f\frac{m}{mv-1}[1-(1-\epsilon^s)^s]}{(1-\epsilon^s)^s + f[1-(1-\epsilon^s)^s]} \quad (304)$$

$$p' = \frac{p^s + f\frac{m-1}{mv-1}(1-p^s)}{p^s + f(1-p^s)} = F(p) \quad (305)$$

其中 $p' = 1-e'/v$  $p = 1-\epsilon/v$。F(p) 对 $p$ 的导数为：

$$F'(p) = \frac{m(v-1)}{mv-1}\frac{fs^{s-1}}{[p^s+f(1-p^s)]^2} = fs\frac{p^{s-1}}{[p^s+f(1-p^s)]^2} + \mathcal{O}(\frac{1}{v}) \quad (306)$$

我们可以将图42 扩展到更高层，其中变量 $Y$ 替代变量 $X_i$ 等。等式 305 的固定点 $p=1$（对应 $\epsilon=0$）或 $p=1/v$（对应 $\epsilon=1$）。当 $F'(1) < 1$ 时，会出现额外的排斥固定点：

$$F'(1) < 1, \quad (307)$$

![](img/86150bd6d44cb578b97eba954b224_0.png)

**图43：** 左图：等式 30 的推断。对于 $sf > 1$，只有固定点 $p=F(p)=1/v$ 对应 $p_1=1$（吸引性）；对于 $sf < 1$，在 $1/v < p^* < 1$ 处有另一个（排斥）固定点，分离了 $p_1$ 和 $p_2$（均为吸引）。右图：使用 BP 迭代进行分类的相图。当 $sf < 1$ 时，BP 可以推理 $e < e^*(sf)$。这种转换由 $p^* = 1 - e^* + e/v$ 预测，其中 $p^* = F(p')$。实验数据 $v=2, s=2$：

$$\frac{v-1}{mv-1} fs < 1 \Rightarrow fs < 1 + \frac{1-m}{v-1} \quad (308)$$
$$\Rightarrow fs < 1 + O(\frac{1}{v}) \quad (309)$$

### C.2.1.2 向下迭代

当我们尝试从较高层变量 $Y$ 到较低层元元组 $X_1, \dots, X_s$ 重建关联 $\hat{y} \to \hat{X}_1, \dots, \hat{X}_s$ 时，我们考虑向下过程。变量 $X_1$ 接收到的消息（图42）：

$$\hat{v}_1(x_1) = \sum_{x_2, \dots, x_s \in \mathcal{A}} \Psi(y, x_1, \dots, x_s) v_y(y) \prod_{i=2}^s v_{X_i}(x_i) = \hat{v}_{X_1}(x_1) + \sum_{x_2 \dots \in \mathcal{D}_{\Delta x_i>0}} \Psi(y, x) \prod_{j \neq i}^s v_{X_j}(x_j) \quad (310)$$

**平均化** 为了分析地研究等式 310 的迭代，我们像 C.2.1.2 节向上迭代那样，在随机规则 $\Psi$ 的实现上计算平均消息 $\langle\hat{v}_i(x_i)\rangle$。我们称 $n_{X_1}$ 为具有 $X_1=x_1$ 的序列数量。规则 $n_{X_1}$ 服从多元超几何分布：

$$P(\{n_{X_i} \in \mathcal{A}\}) = \frac{\binom{v-1}{n_{X_1}}}{\dots} \quad (311)$$

得到平均值：

$$\langle n_{X_1}\rangle = \frac{mv-1}{vs-1} \dots \quad (312)$$
$$\langle n_{X_i \neq X_1}\rangle = \frac{mv-1}{vs-1} \quad (313)$$

### C.2.1.2 向下消息

通过规则 $\psi$ 的分配向下消息，我们得到：

- 对于 $x_1 \neq \bar{X}_1$：
  $$\langle v_i(x_1)\rangle_\psi = \sum_{y} v_i(y) \langle\sum_{x_2 \dots x_s \in S} \psi(y,x)\rangle_{y\leftarrow x} \prod_{i=2}^s \nu_t(x_i) = \frac{m-v_i(y)}{mv-1} \delta_{x_k \in S} \dots \frac{m-v_i(y)}{mv-1} f \quad (314)$$
  其中 $\delta_{x_k \in S} = \frac{n_{X_k \neq X_1}}{v^{s-1}-1}$，

- 对于 $x_1 = \bar{X}_1$：
  $$\langle v_i(X_1)\rangle_\psi = \prod_{i=2}^s \nu_t(i) \quad (315)$$

其中 $\delta_{x_k \in S} = \frac{n_{X_k \neq X_1}}{v^{s-1}}$.## C.2 贝叶传播方程

归一化因子为：

$$\langle Z_{\psi}\rangle_\psi = \sum_y \langle\tilde{\psi}(y)\rangle_\psi = B(0) + f [1-B(0)]. \quad (300)$$

## 附录：扩散过程中的相变

最后，我们得到 $Y$ 的平均信念：

$$\langle\bar{y}(y)\rangle_\psi = \frac{\langle\bar{y}(y)\rangle_\psi}{\langle Z_y\rangle_\psi} = \frac{\delta_{y,\bar{y}}B(0) + f\Psi_y[1-B(0)]}{B(0) + f[1-B(0)]} \quad (301)$$

我们有：

- 对于 $y = \bar{y}$
  $$\langle\bar{y}(\bar{y})\rangle_\psi = \frac{B(0) + f\frac{m-1}{mv-1}}[1-B(0)]}{B(0)+f[1-B(0)]} \quad (302)$$
- 对于 $y \neq \bar{y}$
  $$\langle\bar{y}(y)\rangle_\psi = f\frac{m}{mv-1}B(0) + f[1-B(0)] \quad (303)$$

**迭代层** 有两类平均消息：一种针对参考值 $\bar{y}$（等式 302），另一种针对 $y \neq \bar{y}$，且它们都通过 $B(0) = (1-\epsilon^s)$ 依赖于之前的信念。因此，较高层的平均信念结构与较低层等式 285 相同。我们接着定义了一个新的 $e'$：

$$1-e' = \frac{e'}{v} = \frac{\frac{(1-\epsilon^s)^s}{v} + f\frac{m}{mv-1}[1-(1-\epsilon^s)^s]}{(1-\epsilon^s)^s + f[1-(1-\epsilon^s)^s]} \quad (304)$$

$$p' = \frac{p^s + f\frac{m-1}{mv-1}(1-p^s)}{p^s + f(1-p^s)} = F(p) \quad (305)$$

其中 $p' = 1-e'/v$ $ $p = 1-\epsilon/v$。F(p) 对 $p$ 的导数为：

$$F'(p) = \frac{m(v-1)}{mv-1}\frac{fs^{s-1}}{[p^s+f(1-p^s)]^2} = fs\frac{p^{s-1}}{[p^s+f(1-p^s)]^2} + \mathcal{O}(\frac{1}{v}) \quad (306)$$

我们可以将图42 扩展到更高层，其中变量 $Y$ 替代变量 $X_i$ 等。等式 305 的固定点 $p=1$（对应 $\epsilon=0$）或 $p=1/v$（对应 $\epsilon=1$）。当 $F'(1) < 1$ 时，会出现额外的排斥固定点：

$$F'(1) < 1, \quad (307)$$

![](img/86150bd6d44cb578b97eba954b224_0.png)

**图43：** 左图：等式 30 的推断。对于 $sf > 1$，只有固定点 $p=F(p)=1/v$ 对应 $p_1=1$（吸引性）；对于 $sf < 1$，在 $1/v < p^* < 1$ 处有另一个（排斥）固定点，分离了 $p_1$ 和 $p_2$（均为吸引）。右图：使用 BP 迭代进行分类的相图。当 $sf < 1$ 时，BP 可以推理 $e < e^*(sf)$。这种转换由 $p^* = 1 - e^* + e/v$ 预测，其中 $p^* = F(p')$。实验数据 $v=2, s=2$：

$$\frac{v-1}{mv-1} fs < 1 \Rightarrow fs < 1 + \frac{1-m}{v-1} \quad (308)$$
$$\Rightarrow fs < 1 + O(\frac{1}{v}) \quad (309)$$

### C.2.1.2 向下迭代

当我们尝试从较高层变量 $Y$ 到较低层元元组 $X_1, \dots, X_s$ 重建关联 $\hat{y} \to \hat{X}_1, \dots, \hat{X}_s$ 时，我们考虑向下过程。变量 $X_1$ 接收到的消息（图42）：

$$\hat{v}_1(x_1) = \sum_{x_2, \dots, x_s \in \mathcal{A}} \Psi(y, x_1, \dots, x_s) v_y(y) \prod_{i=2}^s v_{X_i}(x_i) = \hat{v}_{X_1}(x_1) + \sum_{x_2 \dots \in \mathcal{D}_{\Delta x_i>0}} \Psi(y, x) \prod_{j \neq i}^s v_{X_j}(x_j) \quad (310)$$

**平均化** 为了分析地研究等式 310 的迭代，我们像 C.2.1.2 节向上迭代那样，在随机规则 $\Psi$ 的实现上计算平均消息 $\langle\hat{v}_i(x_i)\rangle$。我们称 $n_{X_1}$ 为具有 $X_1=x_1$ 的序列数量。规则 $n_{X_1}$ 服从多元超几何分布：

$$P(\{n_{X_i} \in \mathcal{A}\}) = \frac{\binom{v-1}{n_{X_1}}}{\dots} \quad (311)$$

得到平均值：

$$\langle n_{X_1}\rangle = \frac{mv-1}{vs-1} \dots \quad (312)$$
$$\langle n_{X_i \neq X_1}\rangle = \frac{mv-1}{vs-1} \quad (313)$$

### C.2.1.2 向下消息

通过规则 $\psi$ 的分配向下消息，我们得到：

- 对于 $x_1 \neq \bar{X}_1$：
  $$\langle v_i(x_1)\rangle_\psi = \sum_{y} v_i(y) \langle\sum_{x_2 \dots x_s \in S} \psi(y,x)\rangle_{y\leftarrow x} \prod_{i=2}^s \nu_t(x_i) = \frac{m-v_i(y)}{mv-1} \delta_{x_k \in S} \dots \frac{m-v_i(y)}{mv-1} f \quad (314)$$
  where $\delta_{x_k \in S} = \frac{n_{X_k \neq X_1}}{v^{s-1}-1}$，

- 对于 $x_1 = \bar{X}_1$：
  $$\langle v_i(X_1)\rangle_\psi = \prod_{i=2}^s \nu_t(i) \quad (315)$$

其中 $\delta_{x_k \in S} = \frac{n_{X_k \neq X_1}}{v^{s-1}}$.

归一化因子为：

$$\langle Z_{\psi}\rangle_\psi = \sum_y \langle\tilde{\psi}(y)\rangle_\psi = B(0) + f [1-B(0)]. \quad (300)$$

