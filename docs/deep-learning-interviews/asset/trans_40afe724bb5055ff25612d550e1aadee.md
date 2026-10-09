
## 3.3.3 遗传病检测

表 3.1：遗传病检测的概率值。

| 参数 | 描述 |
| :--- | :--- |
| $P(B|A) = 0.95$ | 如果存在遗传病 [A]，检测呈阳性结果 [B] 的概率（检测概率）。 |
| $P(\overline{B}|A) = 1 - 0.95 = 0.05$ | 如果存在遗传病 [A]，检测呈阴性结果 [$\overline{B}$] 的概率。 |
| $P(B|\overline{A}) = 0.05$ | 如果不存在遗传病 [$\overline{A}$]，检测呈阳性结果 [B] 的概率（虚警概率）。 |

### SOL-45 (CH.SOL-3.16)

我们首先逐一列举概率：

$P(\mathit{Dercum}\mid \mathit{female}) = 0.05,\tag{3.36}$

$P(\mathit{Dercum}\mid \mathit{male}) = 0.0025,\tag{3.37}$

$P(\mathit{male}) = P(\mathit{female}) = 0.5.\tag{3.38}$

我们需要求 $P(\mathit{female}\mid\mathit{Dercum})$。利用贝叶斯公式：

$P(\mathit{female}\mid\mathit{Dercum}) = \dfrac{P(\mathit{Dercum}\mid\mathit{female})P(\mathit{female})}{P(\mathit{Dercum})}.\tag{3.39}$

然而，我们缺少项 $P(\mathit{Dercum})$。为了找到它，我们应用全概率定律：

$\begin{aligned} P(\mathit{Dercum}) & = P(\mathit{Dercum}\mid \mathit{female})P(\mathit{female}) \\
& + P(\mathit{Dercum}\mid \mathit{male})P(\mathit{male}) \\
& = 0.05 \cdot 0.5 + 0.0025 \cdot 0.5 \\
& = 0.02625. \end{aligned}$

最后，回到公式 (3.39)：

$P(\mathit{female}\mid\mathit{Dercum}) = \dfrac{0.05 \cdot 0.5}{0.02625} \approx 0.9524\tag{3.40}$

*注：如何用单个数学方程达到这个结果？*

### SOL-46 (CH.SOL-3.17)

为了解决这个问题，我们引入以下事件：

- **AI**：AI 预测股票期权状态为 1。
- **State 1**：股票期权状态为 1。
- **State 0**：股票期权状态为 0。

直接应用贝叶斯公式得出：

$$ P(\text { State } 1|\text { AI })= \frac{P(\mathrm{AI} | \text { State } 1) P(\text { State } 1)}{P(\mathrm{AI} | \text { State } 1) P(\text { State } 1)+P(\mathrm{AI} | \text { State } 0 ) P(\text { State } 0 )} \tag{3.41} $$

$$ = \frac{0.85 \cdot 2 / 3}{0.85 \cdot 2 / 3+0.15 \cdot 1 / 3} \approx 0.9189 . \tag{3.42} $$

### SOL-47 (CH.SOL-3.18)

为了解决这个问题，我们引入以下事件：

- **H**：人类。
- **M**：猴子。
- **C**：预测正确。

通过运用贝叶斯定理和全概率定律：

$P(H|C)=\frac{P(H\cap C)}{P(C)} \tag{3.43} $

$=\frac{P(C|H)P(H)}{P(C|H)P(H)+P(C|M)P(M)}$

$=\frac{\frac{1}{20}\cdot\frac{1}{2}}{\frac{1}{20}\cdot\frac{1}{2}+\frac{1}{15}\cdot\frac{1}{2}}$

$\approx 0.42.$

*注：如果这个结果看起来有些不对劲，请不要担心——这是理解条件概率的一个积极信号。*

### SOL-48 (CH.SOL-3.19)

为了解决这个问题，我们引入以下事件：

1. **RUS**：一名俄罗斯潜伏特工在说话。
2. **AM**：一名美国人在说话。
3. **L**：TTS 系统生成了“l”。

我们需要求 $P(\textit{RUS}|L)$ 的值。利用贝叶斯定理，我们可以写成：

$P(\textit{RUS}|L)=\frac{P(L|\textit{RUS})P(\textit{RUS})}{P(L)}.$ (3.44)

被告之俄罗斯人占与会者的 1/5，因此：

$P(\textit{RUS})=\frac{1}{5}.$ (3.45)

此外，因为“v-o-k-s-a-l”在总共六个字母中只有一个 l：

$P(L|\textit{RUS})=\frac{1}{6}.$ (3.46)

此外，因为“V-a-u-x-h-a-l-l”在总共八个字母中有两个 l：

$P(L|AM)=\frac{2}{8}$ (3.47)

应用全概率定律得出：

$\begin{gathered} P(L)=P(AM)P(L|AM)+P(RUS)P(L|RUS)\\ =\left(\frac{4}{5}\right)\left(\frac{2}{8}\right)+\left(\frac{1}{5}\right)\left(\frac{1}{6}\right)=\frac{7}{30} \tag{3.48}\end{gathered}$

利用贝叶斯定理，我们可以写成：

$P(RUS|L)=\frac{\frac{1}{5}\left(\frac{1}{6}\right)}{\frac{7}{30}}=\frac{1}{7}$ (3.49)

> **注：** 算法最有可能通过哪个字母发现俄罗斯潜伏特工？

### SOL-49 (CH.SOL-3.20)

已知：

$P(X \text{ 被错误接收为 } Z) = 1/7$.

利用贝叶斯定理，我们可以写成：

$\begin{aligned} P(Z_{trans}|Z_{received}) &= \frac{P(Z_{received}|Z_{trans})P(Z_{trans})}{P(Z_{received})} \tag{3.50} \end{aligned}$

应用全概率定律得出：

$\begin{aligned} P(Z_{received}) &= P(Z_{received}|Z_{trans})P(Z_{trans}) \\ &+P(Z_{received}|X_{trans})P(X_{trans}) \\ &=\frac{7}{8}\cdot\frac{3}{7}+\frac{1}{8}\cdot\frac{4}{7} \\ &=\frac{3}{8}+\frac{4}{56}=\frac{25}{56} \end{aligned}$

因此，使用贝叶斯公式，我们有：

$$\begin{aligned} P(Z_{trans}|Z_{received}) &= \frac{P(Z_{received}|Z_{trans})P(Z_{trans})}{P(Z_{received})} \\ &= \frac{\frac{7}{8} \frac{2}{7}}{\frac{25}{56}} \\ &= \frac{21}{25} = 0.84 . \end{aligned}\tag{3.51}$$

## 3.3.4 最大似然估计

### SOL-50 (CH.SOL-3.21)

对于独立同分布样本集 $X_{1}$，$\cdots$，$X_{n}$，似然函数是概率函数的乘积：

$$\begin{aligned} L(p) &= p(X_{1}=x_{1};p)p(X_{2}=x_{2};p)\cdots p(X_{n}=x_{n};p) \\ &= \prod_{i=1}^{n}\binom{n}{x_{i}}p^{x_{i}}(1-p)^{n-x_{i}} . \end{aligned}\tag{3.52}$$

*注：当 $X$ 是伯努利分布随机变量时，$X^{n}$ 的分布是什么？*

### SOL-51 (CH.SOL-3.22)

$p$ 的最大似然估计量 (MLE) 是使 $L(p)$ 最大化的所有可能 $p$ 值。也就是说，使得测量集 $X_{1}$，$\cdots$，$X_{n}$ 最可能的 $p$ 值。形式上：

$$\hat{p}=arg\,max_{0\leq p\leq 1}L(p)\tag{3.53}$$

*注：强烈鼓励好奇的学生从 $L(p)$ 推导 $\hat{p}$。注意 $L(p)$ 可以极大地简化。*

### SOL-52 (CH.SOL-3.23)

对数似然是似然函数的对数。直观地讲，在寻找 MLE $\hat{\gamma}$ 时，最大化似然函数 $L(\gamma)$ 等价于最大化 $\ln L(\gamma)$，因为 $\ln$ 是一个单调递增函数。通常，我们最大化 $\ln(f(\gamma))$ 而不是 $f(\gamma)$。一个常见的例子是当 $L(\gamma)$ 由正态分布的随机变量组成时。形式上，如果 $X_{1}, \cdots, X_{n}$ 是独立同分布的，每个都具有概率质量函数 (PMF) $f_{X_{i}}(x_{i} | \gamma)$，那么：

$f(\gamma)=\prod_{i=1}^{n} f_{X_{i}}\left(x_{i} | \gamma\right),$ (3.54)

$\ln(f(\gamma))=\sum_{i=1}^{n} \ln f_{X_{i}}\left(x_{i} | \gamma\right).$ (3.55)

### SOL-53 (CH.SOL-3.24)

在似然函数可微的情况下，寻找 MLE 的一般程序如下：

1. 首先对目标参数 $\gamma$ 求对数似然函数 $\ln\left(L(\gamma)\right)$ 的导数。
2. 将结果设为零。
3. 解方程找到满足以下条件的 $\hat{\gamma}$：
   $$\frac{\partial \ln L\left(\hat{\gamma} | x_{1}, \cdots x_{n}\right)}{\partial \gamma}=0 \tag{3.56}$$
4. 计算二阶导数以验证确实是最大值而不是最小值。

### SOL-54 (CH.SOL-3.25)

对数似然函数的一阶导数通常被称为费舍尔得分函数，定义如下：

$$\mathbf{u}(\gamma)=\frac{\partial\ln L(\gamma \mid x_{1},\cdots x_{n})}{\partial\gamma} \tag{3.57}$$

## 3.3.5 费舍尔信息量

### SOL-55 (CH.SOL-3.26)

**费舍尔信息量**是描述对数似然函数二阶导数（曲率）期望值的术语，定义如下：

$$\mathbf{I}(\gamma)= -E\left[\frac{\partial^{2}\ln L(\gamma \mid x_{1},\cdots x_{n})}{\partial\gamma^{2}}\right] \tag{3.58}$$

### SOL-56 (CH.SOL-3.27)

1. **给定 $L(\gamma)$：**
   $$\ln L(\gamma)= \ln \Big( \binom{n}{y} \Big)+y \ln (\gamma)+ (n - y) \ln (1 - \gamma). \tag{3.59}$$
2. **为了找到梯度，我们求一次导数：**
   $$g(\gamma)= \frac{d}{d\gamma} \ln L(\gamma) = \frac{y}{\gamma} - \frac{n-y}{1-\gamma} \tag{3.60}$$
3. **海森矩阵由对 $g(\gamma)$ 求导生成：**
   $$H(\gamma)= -\frac{y}{\gamma^2} - \frac{n-y}{(1-\gamma)^2} \tag{3.61}$$
4. **费舍尔信息量计算如下：**
   $$I(\gamma) = -E[H(\gamma)] = \frac{n}{\gamma(1-\gamma)} \tag{3.62}$$

