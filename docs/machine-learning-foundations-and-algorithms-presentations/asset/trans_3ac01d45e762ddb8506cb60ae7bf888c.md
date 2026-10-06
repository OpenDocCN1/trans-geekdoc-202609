

# 今日议程

回顾：线性分类器

支持向量机：

- 最大间隔 (Maximum Margin)
- 优化问题
- 软间隔 (Soft-Margin)
- 铰形损失 (Hinge-Loss)
- 与伯努利似然性的对比

基础知识：

- 子梯度 (Sub-gradients)

## 二分类：之前的定义

![](img/f01928df50903c99ce023dd3c527a33d_181_0.png)

给定训练数据 $(x_i, y_i)$，$i = 1\dots N$，其中 $x_i \in \mathbb{R}^d$  $y_i \in \{0, 1\}$，学习一个分类器 $f(\boldsymbol{x})$使得：

```
$f(\boldsymbol{x}_i) = \begin{cases} > 0, & \text{if } y_i = 1 \\ < 0, & \text{if } y_i = 0 \end{cases}$
```

## 二分类：新定义

**对于 SVM 而言，使用 +1 和 -1 作为类别标签可以简化符号表示**

**新定义：** 给定训练数据 $(x_i, y_i)$，$i = 1..N$，其中 $x_i \in \mathbb{R}^d$ 和 $y_i \in \{-1, 1\}$，学习一个分类器 $f(x)$使得：

$f(x_i) = \begin{cases} > 0, & \text{if } y_i = 1 \\ < 0, & \text{if } y_i = -1 \end{cases}$

**或者：** 对于分类正确的情况，$f(x_i)y_i > 0$

## 回顾：线性分类器

线性分类器的形式为：

$f(\mathbf{x}) = \mathbf{w}^T\mathbf{x} + b$

在二维空间中，分类器是一条直线

- $w$ 是直线的法向量
- $b$ 是偏置 (bias)

![](img/f01928df50903c99ce023dd3c527a33d_183_0.png)

## 基础知识：向量的投影

两个向量的点积可以用于计算向量 $a$ 在向量 $b$ 上的投影：

- 点积的几何定义
$a^T b = ||a||||b|\cos\theta$

- 两个向量之间的角度
$\cos\theta = \frac{a^T b}{||a||||b||}$

- $a$ 在 $b$ 上的标投影
$a_b = ||a||\cos\theta = \frac{a^T b}{||b||}$

![](img/f01928df50903c99ce023dd3c527a33d_184_0.png)

**观察：** 如果两个向量相互垂直，则投影为 0

## 回顾：几何检查

**观察：**

- 决策边界与 $w$ 垂直
- 如果没有 $b$，它将通过原点

![](img/f01928df50903c99ce023dd3c527a33d_185_0.png)

## 回顾：几何检查

**观察：**

- **$b$ 沿着 $w$ 的（负）方向平移决策边界**
- 这种位移对应于在投影上加上 $\frac{b}{\|\mathbf{w}\|}$

$\mathbf{w}^T\mathbf{x} + b = 0 \Rightarrow \frac{\mathbf{w}^T\mathbf{x}}{\|\mathbf{w}\|} + \frac{b}{\|\mathbf{w}\|} = x_w$

- 即为了使 $\mathbf{x}$ 在决策边界上，其投影必须为：

$x_w = -\frac{b}{\|\mathbf{w}\|}$

![](img/f01928df50903c99ce023dd3c527a33d_186_0.png)

## 最优分离

哪一条直线是最优的？

![](img/f01928df50903c99ce023dd3c527a33d_187_0.png)

## 最大间隔

- **支持向量：** 靠近决策边界的数据点
  - 其他样本可以被忽略

- **间隔 $\rho$ 是支持向量与决策边界之间的距离**

- **间隔应该被最大化**
- 即决策边界与样本之间的最小距离应该最大化

![](img/f01928df50903c99ce023dd3c527a33d_188_0.png)

## 最大间隔

- **最大化**超平面与“困难样本”之间的距离
  - 靠近决策边界的样本
  - 也称为**支持向量**

- **直觉：**
  - 靠近决策边界的样本越 -> 越鲁棒

- **统计学习：**
  - 最大间隔分类器的复杂度更低（VC 维）
  - 且泛化能力更好

![](img/f01928df50903c99ce023dd3c527a33d_189_0.png)

## 几何检查

点 $\mathbf{x}_i$ 到直线的距离：$r = \frac{\mathbf{w}^T\mathbf{x}_i+b}{\|\mathbf{w}\|}$

![](img/f01928df50903c99ce023dd3c527a33d_190_0.png)

## 数学公式

**观察：**

- $w^T x + b = 0$ 和 $c(w^T x + b) = 0$ 定义同一平面
- 缩放因子 $c$ 可以自由选择使得：

- 对于正支持向量，$w^T x_+ + b = 1$
- 对于负支持向量，$w^T x_- + b = -1$

间隔由下式给出：

$$\frac{w^T x_+ + b - (w^T x_- + b)}{\|w\|} = \frac{2}{\|w\|}$$

![](img/f01928df50903c99ce023dd3c527a33d_191_0.png)

## SVM 优化

优化问题：

```
$\arg\max_w \frac{2}{\|\mathbf{w}\|}$
$\text{s.t.} \quad \mathbf{w}^T\mathbf{x}_i + b \begin{cases} \geq 1, & \text{if } y_i = 1 \\ \leq -1, & \text{if } y_i = -1 \end{cases}$
```

间隔条件

**观察：**

- 如果不满足约束，我们的间隔定义是错误的：
$\min_{\mathbf{x}_+\in\mathbf{x}_+} (\mathbf{w}^T\mathbf{x}_+ + b) = 1 \quad \max_{\mathbf{x}_-\in\mathbf{x}_-} (\mathbf{w}^T\mathbf{x}_- + b) = -1$
$\mathbf{x}_-: 负样本$
$\mathbf{x}_+: 正样本$
- 支持向量到决策边界的距离最小
- 至少有一个正点和一个负点恰好满足支持向量条件（即等号）
- 因为 argmax 的存在！向量的范数可以减小

## SVM 优化

优化问题：

```
$\arg\max_w \frac{2}{\|\mathbf{w}\|}$
$\text{s.t.} \quad \mathbf{w}^T\mathbf{x}_i + b \begin{cases} \geq 1, & \text{if } y_i = 1 \\ \leq -1, & \text{if } y_i = -1 \end{cases}$
```

间隔条件

## 重构：更容易求解，相同的解

```
$\arg\min_w \|\mathbf{w}\|^2,$
$\text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \geq 1$
```

- 二次优化问题
- 线性约束
- 凸，唯一最优

可以使用拉格朗日优化求解（目前不重要……）

# 今日日程

回顾：线性分类器

支持向量机：

- 最大间隔
- 优化问题
- 软间隔
- 铰形损失
- 与伯努利似然性的对比

基础知识：

- 子梯度

## 回到线性可分

### 什么是最好的 $w$?

- 线性可分但：间隔小

![](img/f01928df50903c99ce023dd3c527a33d_195_0.png)

- 间隔大但分类错误

我们必须在间隔和分类准确率之间进行权衡！

## 软间隔

引入松变量：
$\xi_i \ge 0$

允许违反间隔条件
$y_i(w^T x_i + b) \ge 1-\xi_i$

- $0 \le \xi_i \le 1$ 样本位于间隔和决策边界之间：违反间隔
- $\xi_i > 1$ 样本位于决策边界的错误侧：分类错误

![](img/f01928df50903c99ce023dd3c527a33d_196_0.png)

## 软间隔

优化问题：

$$\text{argmin}_{\mathbf{w},\xi} \quad ||\mathbf{w}||^2 + C\sum_{i=1}^N \xi_i,$$
$\text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \ge 1-\xi_i, \quad \xi_i \ge 0$$

惩罚松变量

- $C$ 是一个（反）正则化参数
- 小 $C$：约束影响小 -> 大间隔 -> 大正则化
- 大 $C$：约束影响大 -> 小间隔 -> 小正则化
- $C$ 无穷大：强制执行约束 -> 硬间隔 -> 无正则化

## 插图

# 硬间隔

# 软间隔

![](img/f01928df50903c99ce023dd3c527a33d_198_0.png)

![](img/f01928df50903c99ce023dd3c527a33d_198_1.png)

Gerhard Neumann | 机器学习 – 基础与算法 | KIT | 2023年夏季学 22

# 今日议程

回顾：线性分类器

支持向量机：

- 最大间隔
- 优化问题
- 软间隔
- 铰形损失
- 与伯努利似然性的对比

基础知识：

- 子梯度

## 重构为无约束问题

约束优化：松变量

```
$\text{argmin}_{\mathbf{w},\xi} \quad ||\mathbf{w}\|^2 + C\sum_{i=1}^N \xi_i,\quad \text{s.t.} \quad y_i(\mathbf{w}^T\mathbf{x}_i + b) \geq 1-\xi_i, \quad \xi_i \geq 0$
正则化损失函数
```

