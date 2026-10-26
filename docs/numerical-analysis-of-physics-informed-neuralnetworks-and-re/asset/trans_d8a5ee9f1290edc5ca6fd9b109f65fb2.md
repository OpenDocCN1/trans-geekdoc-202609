

## 物理信息神经网络及物理信息机器学习中相关模型的数值分析

Tim De Ryck
Seminar for Applied Mathematics, ETH Zürich,
Rämistrasse 101, 8092 Zürich, Switzerland
E-mail: tim.deryck@math.ethz.ch

Siddhartha Mishra
Seminar for Applied Mathematics & ETH AI Center, ETH Zürich,
Rämistrasse 101, 8092 Zürich, Switzerland
E-mail: siddhartha.mishra@math.ethz.ch

近年来，物理信息神经网络（PINNs）及其变体作为偏微分方程正问题和反问题数值模拟的算法已经非常流行。本文旨在全面回顾目前已有的关于PINNs及构成物理信息机器学习骨干的相关模型的数值分析结果。我们提供了一个统一框架，能够有效地分析PINNs在逼近偏微分方程时所产生的各个误差分量。我们详细回顾了关于逼近误差、泛化误差和训练误差的现有结果，以及它们随PDE类型和底层域维度的变化行为。特别是，我们阐明了解的正则性及其对扰动的稳定性在误差分析中的作用。我们还给出了数值结果以说明该理论。我们确定训练误差是一个关键的瓶颈，它会对物理信息机器学习中各种模型的整体性能产生不利影响。

2020年数学学科分类：主分类 65M15；次分类 68T07, 35A35

通过（随机）梯度下降获得一个逼近底层偏微分方程解的神经网络。这一框架在20世纪90年代已被考虑，见Dissanayake和Phan-Thien（1994）、Lagaris、Likas和Fotiadis（1998）、Lagaris、Likas和Papageorgiou（2000）及其参考文献；这些论文应被视为PINNs的先驱。然而，PINNs的现代版本是最近在Raissi和Karniadakis（2018）以及Raissi、Perdikaris和Karniadakis（2019）中引入并命名的。此后，关于PINNs的文献爆炸式增长，它们已被广泛应用于众多场景，用于求解PDE及相关方程（SDE、SPDE）的正问题和反问题；参见Karniadakis等人（2021）和Cuomo等人（2022）对PINNs现有文献的广泛综述。

然而，PINNs并不是物理信息机器学习框架内仅有的模型。人们可以考虑其他形式的PDE残差，例如产生VPINNs的变分形式（Kharazmi、Zhang和Karniadakis 2019）、产生wPINNs的弱形式（De Ryck、Mishra和Molinaro 2024c），或最小化底层能量从而产生DeepRitz方法（E和Yu 2018）。类似地，人们可以使用高斯过程（Rasmussen 2003）、DeepONets（Lu等人2021b）或神经算子（Kovachki等人2023）作为试解空间，以实现物理信息机器学习的替代模型。

鉴于物理信息机器学习中关于PINNs及相关模型的文献呈指数增长，有必要追问这些方法是否对其性能具有严格的数学保证，以及人们能否以类似于对传统数值方法（如有限差分、有限元、有限体积和谱方法）进行分析的大量文献的方式来分析这些方法。尽管研究的主要焦点一直是PINNs及其变体在科学和工程不同领域的广泛应用，但近年来出现了大量对PINNs进行严格分析的论文。本文旨在回顾物理信息机器学习中构成PINNs及相关模型数值分析的现有文献。我们的目标是批判性地分析PINNs及其变体，以确定它们何时可以被应用以及其适用性的限制是什么。为此，我们在第2节中首先介绍物理信息机器学习的公式，包括底层偏微分方程、其不同形式的残差和逼近的试解空间。在第3节中，我们概述了物理信息机器学习中底层误差的主要组成部分；相应的逼近、稳定性、泛化和训练误差将分别在第4、5、6和7节中分析。

## 2. 物理信息机器学习

在本节中，我们为文章的其余部分奠定基础。在第2.1节中，我们引入一个抽象的PDE设置，并考虑一些将在后续数值分析中使用的重要PDE示例。接下来，在第2.2节中介绍不同的模型类别。在第2.3节中，我们介绍基于PDE不同公式的物理信息学习变体，其产生的残差将通过离散化（第2.4节）和优化（第2.5节）构成物理信息损失函数。最后，在第2.6节中给出整个方法的总结。

### 2.1. 偏微分方程设置

在整篇文章中，我们考虑以下设置。设$X$、$Y$、$W$为可分Banach空间，范数分别为$\|\cdot\|_X$、$\|\cdot\|_Y$和$\|\cdot\|_W$；类似地，设$X^* \subset X$、$Y^* \subset Y$和$W^* \subset W$为闭子空间，范数分别为$\|\cdot\|_{X^*}$、$\|\cdot\|_{Y^*}$和$\|\cdot\|_{W^*}$。此类空间的典型例子包括$L^p$空间和Sobolev空间。我们考虑抽象形式的PDE

$$\mathcal{L}[u] = f, \qquad \mathcal{B}[u] = g, \tag{2.1}$$

其中$\mathcal{L}: X^* \to Y^*$是一个*微分算子*，$f \in Y^*$是一个*输入*或*源函数*。边界条件（包括时变PDE的初始条件）由*边界算子* $\mathcal{B}: X^* \to W^*$和边界数据$g \in W^*$规定。我们假设对于所有$f \in Y^*$，存在唯一的$u \in X^*$使得(2.1)成立。最后，我们假设对于所有$u \in X^*$和$f \in Y^*$，有

$$\|\mathcal{L}[u]\|_{Y^*} < +\infty, \qquad \|f\|_{Y^*} < +\infty, \qquad \|\mathcal{B}[u]\|_{W^*} < +\infty. \tag{2.2}$$

我们还将$u$的定义域记为$\Omega$，其中对于与时间无关的PDE，$\Omega = D \subset \mathbb{R}^d$；对于时变PDE，$\Omega = D \times [0,T] \subset \mathbb{R}^{d+1}$。

#### 2.1.1. 正问题

抽象PDE（2.1）的正问题相当于以下内容：给定源$f$和边界条件$g$（以及可能另一个参数函数$a$，使得$\mathcal{L} := \mathcal{L}_a$），求PDE的解$u$。这可以概括为寻找一个*算子*，它将输入函数$v \in \{f,g,a\} \subset \mathcal{X}$映射到PDE的相应解$u \in X^*$

$$\mathcal{G}: \mathcal{X} \to X^*: v \mapsto \mathcal{G}[v] = u. \tag{2.3}$$

注意，确定整个算子$\mathcal{G}$而不仅仅是函数$u$也可能是有意义的。找到$\mathcal{G}$的良好逼近被称为*算子学习*。算子的第一个具体示例是输入函数或源函数$f$与相应解$u$之间的映射，因此$\mathcal{X} = Y^*$且$v=f$：

$$\mathcal{G}: Y^* \to X^*: f \mapsto \mathcal{G}[f] = u. \tag{2.4}$$

对于时变PDE，另一个常见示例是$\mathcal{B}[u] = g$包含初始条件$u(\cdot,0) = u_0$的规定，即*解算子*将初始条件$u_0$映射到PDE的解

$$\mathcal{G}: W^* \to X^*: u_0 \mapsto \mathcal{G}[u_0] = u, \tag{2.5}$$

其中$\mathcal{X}=W^*$且$v = u_0$。或者，也可以考虑映射$u_0 \mapsto u(\cdot,T)$。

算子学习的最后一个示例可以在参数化PDE中找到，其中微分算子、源函数、初始条件或边界条件依赖于标量参数或参数函数。虽然求解参数化PDE通常不被称为算子学习，但很明显它可以被视为这样，唯一的区别是输入空间不一定是无限维的。

下面我们给出PDE（2.1）的示例，稍后我们将考虑这些示例的正问题。

### 示例2.1（半线性热方程）。

我们首先考虑半线性热方程的设置。设$D \subset \mathbb{R}^d$是一个具有连续可微边界$\partial D$的开连通有界集。则半线性抛物方程由下式给出

$$\begin{cases} u_t = \Delta u + f(u) & \text{for all } x \in D,\ t \in (0,T), \\ u(x,0)=u_0(x) & \text{for all } x \in D, \\ u(x,t)=0 & \text{for all } x \in \partial D,\ t \in (0,T). \end{cases}\tag{2.6}$$

这里，$u_0 \in C^k(D)$，$k \ge 2$，是初始数据，$u \in C^k([0,T] \times D)$是经典解，$f : \mathbb{R} \times \mathbb{R}$是非线性源（反应）项。我们假设非线性是全局Lipschitz的，即存在常数$C_f > 0$使得

$$|f(v)-f(w)| \le C_f |v-w| \quad \text{for all } v,w \in \mathbb{R}.\tag{2.7}$$

特别地，具有$f(u) \equiv 0$的齐次线性热方程和线性源项$f(u)=\alpha u$是（2.6）的示例。具有全局Lipschitz非线性的半线性热方程出现在生物学和金融学的几个模型中（Beck等人2021）。具有如（2.6）的Lipschitz非线性的半线性抛物方程的存在性、唯一性和正则性可以在经典教科书中找到，例如Friedman（1964）的著作。

### 示例2.2（Navier–Stokes方程）。

我们考虑著名的不可压缩Navier–Stokes方程（Temam 2001及其参考文献）

$$\begin{cases} u_t + u \cdot \nabla u + \nabla p = \nu \Delta u & \text{in } D \times [0,T], \\ \operatorname{div}(u)=0 & \text{in } D \times [0,T], \\ u(t=0)=u_0 & \text{in } D. \end{cases}\tag{2.8}$$

这里，$u: D \times [0,T] \to \mathbb{R}^d$是流体速度，$p: D \times [0,T] \to \mathbb{R}$是压力，$u_0: D \to \mathbb{R}^d$是初始流体速度。粘度用$\nu \ge 0$表示。在本文的其余部分，我们考虑在$d$维环面$D = \mathbb{T}^d = [0,1)^d$上带周期边界条件的Navier–Stokes方程（2.8）。

