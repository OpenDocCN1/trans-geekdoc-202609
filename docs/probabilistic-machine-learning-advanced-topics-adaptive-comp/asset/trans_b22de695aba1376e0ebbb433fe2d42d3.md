
经验期望。因此模型的形式为

$$p(\boldsymbol{x}|\boldsymbol{\theta}) = \frac{1}{Z(\boldsymbol{\theta})} \exp \left( \boldsymbol{\theta}^{\mathsf{T}} \boldsymbol{\phi}(\boldsymbol{x}) \right)$$

如果特征 $\boldsymbol{\phi}(\boldsymbol{x})$ 根据图结构分解，我们得到一种称为 **最大熵模型** 的 MRF。下面给出一些示例。

## 4.3.4.1 对数线性模型

假设势函数具有以下对数线性形式：

$$\psi_c(\boldsymbol{x}_c; \boldsymbol{\theta}_c) = \exp(\boldsymbol{\theta}_c^{\mathsf{T}} \boldsymbol{\phi}(\boldsymbol{x}_c))$$

其中 $\boldsymbol{\phi}(\boldsymbol{x}_c)$ 是由团 $c$ 中的变量推导出的特征向量。那么整体模型由以下公式给出：

$$p(\boldsymbol{x}|\boldsymbol{\theta}) = \frac{1}{Z(\boldsymbol{\theta})} \exp \left( \sum_c \boldsymbol{\theta}_c^{\mathsf{T}} \boldsymbol{\phi}(\boldsymbol{x}_c) \right)$$

例如，在高斯图形模型（GGM）中，我们有

$$\boldsymbol{\phi}([x_i, x_j]) = [x_i, x_j, x_i x_j]$$

对于 $x_i \in \mathbb{R}$。在 Ising 模型中，我们有

$$\boldsymbol{\phi}([x_i, x_j]) = [x_i, x_j, x_i x_j]$$

对于 $x_i \in \{-1, +1\}$。因此，这两者都是最大熵模型。然而，有两个关键区别：首先，在 GGM 中，变量是实值的，而不是二进制的；其次，在 GGM 中，配分函数 $Z(\boldsymbol{\theta})$ 可以在 $O(D^3)$ 时间内计算，而在玻尔兹曼机中，计算配分函数可能需要 $O(2^D)$ 时间（有关详细信息，请参见第 9.5.4 节）。

如果特征 $\boldsymbol{\phi}$ 按层次方式结构化（捕获一阶交互、二阶交互等），且所有变量 $\boldsymbol{x}$ 都是分类变量，则在统计学中，所得模型称为 **对数线性模型**。然而，在机器学习社区中，“对数线性模型”一词通常用于描述任何形式为方程 (4.95) 的模型。

## 4.3.4.2 最大熵拼写模型的特征诱导

在某些应用中，我们假设特征 $\boldsymbol{\phi}(\boldsymbol{x})$ 是已知的。然而，可以以无监督的方式学习最大熵模型中的特征；这称为 **特征诱导**。

特征诱导的一种常见方法最初在 [DDL97; ZWM97] 中提出，即从一组基础特征开始，然后不断从旧特征中创建新特征组合，贪婪地将最佳特征添加到模型中。

作为这种方法的示例，[DDL97] 描述了如何构建表示英文拼写的模型。这可以形式化为可变长度字符串上的概率分布 $p(\boldsymbol{x}|\boldsymbol{\theta})$，其中 $x_t$ 是英文字母中的一个字母。最初模型没有特征，这表示均匀分布。该算法首先选择添加特征

```
\(\phi_1(\boldsymbol{x}) = \sum_i \mathbb{I}(x_i \in \{a, \dots, z\})\) (4.98)
```

该特征检查是否有任何字母是小写字母。添加特征后，参数通过极大似然估计进行（重新）拟合（这是一个计算困难的问题，我们将在第 4.3.9.1 节中讨论）。对于此特征，结果是 \(\hat{\theta}_1 = 1.944$，这意味着任意位置有小写字母的单词比同一单词在该位置没有小写字母的可能性大约大 \(e^{1.944} \approx 7\) 倍。使用（退火）吉布斯采样（在第 12.3 节中描述）从该模型生成的一些样本如下所示。

```
m, r, xev0, ijjjiir, b, to, jz, gsr, wq, vf, x, ga, msnGh, pcp, d, oziVlaI, hzagh, yzop, io,
advzmxnv, ijv_bolft, x, emx, kayerf, mlJ, rawzyb, jp, ag, ctdnnnbg, wgdw, t, kguv, cy,
spxcq, uzflbbf, dxtkkn, cxwx, jpd, ztzh, lv, zhpkvnu, l~, r, qee, nynrx, atze4n, ik, se, w,
lrh, hp+, yryqka'h, zcngotcnx, igcump, zjcjs, lqpWiqu, cefmfhc, o, lb, fdcY, tzby, yopxmvk,
by, fz, t, govyccm, iyjyiduwfzo, 6xr, duh, ejv, pk, pjw, 1, f1, w
```

算法添加的第二个特征检查两个相邻字符是否为小写字母：

```
\(\phi_2(\boldsymbol{x}) = \sum_{i \sim j} \mathbb{I}(x_i \in \{a, \dots, z\}, x_j \in \{a, \dots, z\})\) (4.99)
```

现在模型的形式为

```
\(p(\boldsymbol{x}) = \frac{1}{Z} \exp(\theta_1 \phi_1(\boldsymbol{x}) + \theta_2 \phi_2(\boldsymbol{x}))\) (4.100)
```

继续这种方式，该算法为字符串 s> 和 ing> 添加特征，其中 > 表示单词结束，以及针对 [0-9] 等各种正则表达式。使用（退火）吉布斯采样生成的具有 1000 个特征的模型的一些样本如下所示。

```
was, reaser, in, there, to, will, ,, was, by, homes, thing, be, relowerated, ther, which,
conists, at, fores, andting, with, Mr., proveral, the, , ****, on't, prolling, prothere, ,
mento, at, yaou, 1, chestraing, for, have, to, intrally, of, quit, , . best, compers, ****,
cluseliment, usster, of, is, several, this, thise, of, offect, inatever, thifer,
constranded, stater, vill, in, thase, in, youse, menttering, and, . , of, in, verate, of,
to
```

如果为每个可能的字母组合定义一个特征，我们可以表示任何概率分布。然而，这会导致过拟合。最大熵方法的强大之处在于我们可以选择哪些特征对该领域很重要。

一种替代方法是引入隐变量，这些隐变量隐式地建模可见节点之间的相关性，而不是显式地学习特征函数。有关此类模型的示例，请参见第 4.3.3 节。

6. 我们感谢 John Lafferty 分享此示例。

## 4.3.5 高斯 MRF

在第 4.2.3 节中，我们展示了如何使用 DPGM 表示多元高斯分布。在本节中，我们展示了如何使用 UPGM 表示多元高斯分布。（有关 GMRF 的更多详细信息，请参见 [RH05] 等。）

### 4.3.5.1 标准 GMRF

高斯图形模型（或 GGM），也称为高斯 MRF，是以下形式的成对 MRF：

$$
p(x) = \frac{1}{Z(\theta)} \prod_{i \sim j} \psi_{ij}(x_i, x_j) \prod_i \psi_i(x_i)
\psi_{ij}(x_i, x_j) = \exp(-\frac{1}{2} x_i \Lambda_{ij} x_j)
\psi_i(x_i) = \exp(-\frac{1}{2} \Lambda_{ii} x_i^2 + \eta_i x_i)
Z(\theta) = (2\pi)^{D/2} |\Lambda|^{-\frac{1}{2}}
$$

$\psi_{ij}$ 是边势（成对项），而每个 $\psi_i$ 是节点势或一元项。（我们可以将一元项合并到成对项中，但为了清晰起见，我们将它们保持分开。）

联合分布可以重写为以下更常见的形式：

$$p(x) \propto \exp[\eta^T x - \frac{1}{2} x^T \Lambda x]$$

这称为高斯分布的信息形式；$\Lambda = \Sigma^{-1}$ 和 $\eta = \Lambda \mu$ 称为标准参数。

如果 $\Lambda_{ij} = 0$，则没有连接 $x_i$ 和 $x_j$ 的成对项，因此 $x_i \perp x_j | x_{-ij}$，其中 $x_{-ij}$ 是除 $x_i$ 和 $x_j$ 之外的所有节点。因此，$\Lambda$ 中的零项称为结构零。这意味着我们可以对权重使用 $\ell_1$ 正则化来学习稀疏图，这种方法称为图形拉索（有关详细信息，请参见补充部分 30.4.2）。

请注意，即使精度矩阵 $\Lambda$ 是稀疏的，协方差矩阵 $\Sigma = \Lambda^{-1}$ 也可以是稠密的。例如，考虑具有相关系数 $\rho$ 的 AR(1) 过程。精度矩阵（对于具有 T=7 个节点的图）如下所示：

$$
\Lambda = \frac{1}{\tau^2} \begin{pmatrix} 1 & -\rho & & & & \\ -\rho & 1+\rho^2 & -\rho & & & \\ & -\rho & 1+\rho^2 & -\rho & & \\ & & -\rho & 1+\rho^2 & -\rho & \\ & & & -\rho & 1+\rho^2 & -\rho \\ & & & & -\rho & 1 \end{pmatrix}
$$

7. 此示例来自 https://dansblog.netlify.app/posts/2022-03-22-a-linear-mixed-effects-model/.

但是协方差矩阵是完全稠密的：

\[
\Lambda^{-1} = \tau^2 \begin{pmatrix} 
\rho & \rho^2 & \rho^3 & \rho^4 & \rho^5 & \rho^6 & \rho^7 \\
\rho^2 & \rho & \rho^2 & \rho^3 & \rho^4 & \rho^5 & \rho^6 \\
\rho^3 & \rho^2 & \rho & \rho^2 & \rho^3 & \rho^4 & \rho^5 \\
\rho^4 & \rho^3 & \rho^2 & \rho & \rho^2 & \rho^3 & \rho^4 \\
\rho^5 & \rho^4 & \rho^3 & \rho^2 & \rho & \rho^2 & \rho^3 \\
\rho^6 & \rho^5 & \rho^4 & \rho^3 & \rho^2 & \rho & \rho^2 \\
\rho^7 & \rho^6 & \rho^5 & \rho^4 & \rho^3 & \rho^2 & \rho 
\end{pmatrix}
\]

这是因为，在链式结构 UPGM 中，每对节点在边缘上都是相关的，即使在给定分隔符的条件下可能条件独立。

### 4.3.5.2 非线性高斯 MRF

在本节中，我们考虑 GGM 的推广以处理非线性模型的情况。假设联合分布由局部因子（或团势）$\psi_c$ 的乘积给出，每个因子定义在一组团变量 $x_c$ 上，如下所示：

\[ p(x) = \frac{1}{Z} \prod_c \psi_c(x_c) \]

\[ \psi_c(x_c) = \exp(-E_c(x_c)) \]

\[ E_c(x_c) = \frac{1}{2}(f_c(x_c) - d_c)^T \Sigma_c^{-1} (f_c(x_c) - d_c) \]

其中 $d_c$ 是第 c 个团的可选局部证据项，$f_c$ 是某种测量函数。假设测量函数 $f_c$ 是线性的，即，

\[ f_c(x) = J_c x + b_c \]

在这种情况下，团 c 的能量变为

\[ E_c(x_c) = \frac{1}{2} x_c^T \underbrace{J_c^T \Sigma_c^{-1} J_c}_{\Lambda_c} x_c + x_c^T \underbrace{J_c^T \Sigma_c^{-1} (b_c - d_c)}_{-\eta_c} + \frac{1}{2} \underbrace{(b_c - d_c) \Sigma_c^{-1} (b_c - d_c)}_{k_c} \]
\[ = \frac{1}{2} x_c^T \Lambda_c x_c - \eta_c^T x_c + k_c \]

这是一个标准高斯因子。如果 $f_c$ 是非线性的，通常在当前估计 $x_c^0$ 附近对模型进行线性化以得到

\[ f_c(x_c) \approx f_c(x_c^0) + J_c(x_c - x_c^0) = J_c x_c + \underbrace{(f_c(x_c^0) - J_c x_c^0)}_{b_c} \]

其中 $J_c$ 是 $f_c(x_c)$ 关于 $x_c$ 的雅可比矩阵。这为我们提供了一个可用于推理的“临时”高斯因子。可以迭代此过程以提高精度。
