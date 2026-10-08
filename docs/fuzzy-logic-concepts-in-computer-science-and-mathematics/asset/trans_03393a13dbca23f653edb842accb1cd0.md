
# 15.4 数值示例

在本节中，我们将对建议的度量进行数值验证。为了测试所提出度量的有效性，我们将借助示例对提议的距离度量进行计算。

设 $\mathbb{Q}, \mathbb{P}$ 和 $\mathbb{O}$ 是集合 $A=\{a_{1},a_{2},\ldots,a_{n-1},a_{n}\}$ 中的三个 IFS，则

$$
\begin{split}
\mathbb{Q} &= \langle 0,0.6,0.2 \rangle \langle 0,0.4,0.6 \rangle \langle 0.5,0.3 \rangle \\
\mathbb{P} &= \langle 0,0.8,0.1 \rangle \langle 0,0.7,0.3 \rangle \langle 0,0.6,0.1 \rangle \\
\mathbb{O} &= \langle 0,0.9,0.1 \rangle \langle 0,0.8,0.2 \rangle \langle 0.7,0.3 \rangle
\end{split}
$$

$$
\begin{split}
\hat{d}_{11}(\mathbb{Q},\mathbb{P}) &= 1 - \sum_{i=1}^{n} w_{i} \frac{\pi}{2} - \sin\frac{\pi}{2} \\
\hat{d}_{10}(\mathbb{Q},\mathbb{O}) &= 1 - \sum_{i=1}^{n} w_{i} \frac{\pi}{2} - \sin\frac{\pi}{2} \\
&= 0.014268
\end{split}
$$

同理，我们可以证明 $\hat{D}_{9}(\mathbb{Q}, \mathbb{P}), \hat{D}_{10}(\mathbb{Q}, \mathbb{O}), \hat{D}_{11}(\mathbb{Q}, \mathbb{O})$。

数值依据：从上述计算中可以得出以下结论。

1. $0 \leq \hat{D}_{i} (\mathbb{Q}, \mathbb{O}) \leq 1$。
2. $\hat{D}_{i} (\mathbb{Q}, \mathbb{O}) = 0 \iff \mathbb{Q} \equiv \mathbb{O}$。
3. $\hat{D}_{i} (\mathbb{Q}, \mathbb{O}) = \hat{D}_{i} (\mathbb{O}, \mathbb{Q})$。
4. $\hat{D}_{i} (\mathbb{Q}, \mathbb{P}) \leq \hat{D}_{i} (\mathbb{Q}, \mathbb{O}) + \hat{D}_{i} (\mathbb{O}, \mathbb{P})$。

表 15.1 展示了提议的距离度量和加权距离度量的数值。

**表 15.1** $\mathbb{Q}, \mathbb{O},$ 和 $\mathbb{P}$ 的提议距离度量

| 距离度量 | $\hat{d}_{10}(\mathbb{Q}, \mathbb{O})$ | $\hat{d}_{10}(\mathbb{O}, \mathbb{P})$ | $\hat{d}_{10}(\mathbb{Q}, \mathbb{P})$ |
|---|---|---|---|
| $\hat{d}_{10}(\mathbb{Q}, \mathbb{O})$ | 0.001614 | 0.014157 | 0.014268 |
| $\hat{d}_{10}(\mathbb{Q}, \mathbb{O})$ | 0.667305 | 0.670701 | 0.670644 |

### 15.5 应用

在这里，我们展示了与所提议的距离度量相关的应用，以证明该提议度量的可靠性。

#### 15.5.1 模式识别

假设有三个模式 $\mathbb{Q}, \mathbb{P}$ 和 $\mathbb{O}$，我们想确定以下哪个模式最接近 $\mathbb{Y}$，其中

$$
\mathbb{Q} = \langle 1.0/a_{1} \rangle, \langle 0.8,0/a_{2} \rangle, \langle 0.7,0.1/a_{3} \rangle, \quad \mathbb{P} = \langle 0.8,0.1/a_{1} \rangle, \langle 1.0/a_{2} \rangle, \langle 0.9,0.1/a_{3} \rangle,
$$

$$
\mathbb{O} = \langle 0.6,0.2/a_{1} \rangle, \langle 0.8,0/a_{2} \rangle, \langle 1.0/a_{3} \rangle.
$$

并设 $\mathbb{Y} = \langle 0.5,0.3/a_{1} \rangle, \langle 0.6,0.2/a_{2} \rangle, \langle 0.8,0.1/a_{3} \rangle$。

设权重 $w_{i}$ 分别为 0.5、0.3 和 0.2。

表 15.2 表明，$\mathbb{P}$ 表现出与 $\mathbb{Y}$ 最近的接近度，因为它显示了最小的距离，这表明 $\mathbb{Y}$ 是被确认的且最接近的模式。

**表 15.2** $\mathbb{Q}, \mathbb{P},$ 和 $\mathbb{O}$ 之间的距离度量

| 距离度量 | $\hat{d}(\mathbb{Q}, \mathbb{Y})$ | $\hat{d}(\mathbb{P}, \mathbb{Y})$ | $\hat{d}(\mathbb{O}, \mathbb{Y})$ |
| :--- | :--- | :--- | :--- |
| $\hat{d}_{10}(\mathbb{Q}, \mathbb{P})$ | 0.07 | **0.02** | 0.04 |
| $\hat{d}_{11}(\mathbb{Q}, \mathbb{P})$ | 0.08 | **0.02** | 0.03 |

#### 15.5.2 医疗诊断

假设一名患者已由医疗顾问根据五个症状进行检查，如体温（$a_1$）、疲劳（$a_2$）、胃部问题（$a_3$）、头痛（$a_4$）和胸痛（$a_5$），诊断集合 $O = \{\text{病毒性发烧, 伤寒, 胃部问题, 疟疾, 和胸部问题}\}$。利用患者提供的反馈，我们旨在识别与其症状或状况最相符的疾病。

$$
\begin{array}{l}
\mathbb{Q}_{1}=\left\{\left\langle\frac{0.4,0}{a_{1}}\right\rangle,\left\langle\frac{0.3,0.5}{a_{2}}\right\rangle,\left\langle\frac{0.1,0.7}{a_{3}}\right\rangle,\left\langle\frac{0.4,0.3}{a_{4}}\right\rangle,\left\langle\frac{0.1,0.7}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{2}=\left\{\left\langle\frac{0.7,0}{a_{1}}\right\rangle,\left\langle\frac{0.2,0.6}{a_{2}}\right\rangle,\left\langle\frac{0.0,0.9}{a_{3}}\right\rangle,\left\langle\frac{0.7,0}{a_{4}}\right\rangle,\left\langle\frac{0.1,0.8}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{3}=\left\{\left\langle\frac{0.3,0.3}{a_{1}}\right\rangle,\left\langle\frac{0.6,0.1}{a_{2}}\right\rangle,\left\langle\frac{0.2,0.7}{a_{3}}\right\rangle,\left\langle\frac{0.2,0.6}{a_{4}}\right\rangle,\left\langle\frac{0.1,0.9}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{4}=\left\{\left\langle\frac{0.1,0.7}{a_{1}}\right\rangle,\left\langle\frac{0.2,0.4}{a_{2}}\right\rangle,\left\langle\frac{0.8,0}{a_{3}}\right\rangle,\left\langle\frac{0.2,0.7}{a_{4}}\right\rangle,\left\langle\frac{0.2,0.7}{a_{5}}\right\rangle\right\} \\
\mathbb{Q}_{5}=\left\{\left\langle\frac{0.1,0.8}{a_{1}}\right\rangle,\left\langle\frac{0.0,0.8}{a_{2}}\right\rangle,\left\langle\frac{0.2,0.8}{a_{3}}\right\rangle,\left\langle\frac{0.2,0.8}{a_{4}}\right\rangle,\left\langle\frac{0.8,0.1}{a_{5}}\right\rangle\right\}
\end{array}
$$

并设 $\mathbb{O} = \{<0.8,0.1>, <0.6,0.1>, <0.2,0.8>, <0.6,0.1>, <0.1,0.6>\}$。

设权重 $w_i$ 分别为 0.15、0.2、0.1、0.25 和 0.3。

表 15.3 显示，$\mathbb{O}$ 最接近 $\mathbb{Q}_{1}$，因为它具有最小的距离，这意味着该人可能患有病毒性发烧。

**表 15.3** 医疗诊断与患者之间的距离度量

| 距离度量 | $\hat{d}(\mathbb{O}, \mathbb{Q}_{1})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{2})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{3})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{4})$ | $\hat{d}(\mathbb{O}, \mathbb{Q}_{5})$ |
|:------------------|:-------------------------------:|:-------------------------------:|:-------------------------------:|:-------------------------------:|:-------------------------------:|
| $\hat{D}10(\mathbb{Q}_{j}, \mathbb{P})$ | 0.01 | 0.01 | 0.01 | 0.12 | 0.13 |
| $\hat{D}11(\mathbb{Q}_{j}, \mathbb{P})$ | 0.01 | 0.01 | 0.02 | 0.07 | 0.14 |

### 15.6 比较分析

比较分析是一种有价值的工具，它允许考察和评估不同变量、主题或现象之间的相似性、差异、模式和关系。在本文中，我们的目标是通过将其应用于模式识别和医疗诊断等实际场景，来评估所提议度量的可靠性。

已经对一些著名研究人员提出的距离度量进行了比较，并得到了模式识别和医疗诊断的统一结果。表 15.4 和 15.5 分别展示了针对本文中列出的所有距离度量在模式识别和医疗诊断中所得到的结果。

**表 15.4** 模式识别中 $\mathbb{Q}_{j}, \mathbb{P}$, $\mathbb{O}$ 与 $\mathbb{G}$ 之间距离度量的比较分析

| 距离度量 | $\hat{d}(\mathbb{Q}_{j}, \mathbb{G})$ | $\hat{d}(\mathbb{P}, \mathbb{G})$ | $\hat{d}(\mathbb{O}, \mathbb{G})$ |
|:------------------|:-------------------------:|:----------------------:|:-----------------------:|
| $\hat{D}1(\mathbb{Q}_{j}, \mathbb{P})$ | 0.37 | 0.35 | 0.15 |
| $\hat{D}2(\mathbb{Q}_{j}, \mathbb{P})$ | 1 | 1 | 1 |
| $\hat{D}3(\mathbb{Q}_{j}, \mathbb{P})$ | 0.56 | 0.56 | 0.25 |
| $\hat{D}4(\mathbb{Q}_{j}, \mathbb{P})$ | 0.5 | 0.5 | 0.22 |
| $\hat{D}5(\mathbb{Q}_{j}, \mathbb{P})$ | 0.40 | 0.40 | 0.18 |
| $\hat{D}6(\mathbb{Q}_{j}, \mathbb{P})$ | 0.37 | 0.35 | 0.15 |
| $\hat{D}7(\mathbb{Q}_{j}, \mathbb{P})$ | 0.55 | 0.52 | 0.23 |
| $\hat{D}8(\mathbb{Q}_{j}, \mathbb{P})$ | 0.39 | 1.07 | 0.53 |
| $\hat{D}9(\mathbb{Q}_{j}, \mathbb{P})$ | 0.20 | 0.10 | 0.14 |
| $\hat{D}10(\mathbb{Q}_{j}, \mathbb{P})$ | 0.07 | 0.02 | 0.04 |
| $\hat{D}11(\mathbb{Q}_{j}, \mathbb{P})$ | 0.08 | 0.02 | 0.03 |
