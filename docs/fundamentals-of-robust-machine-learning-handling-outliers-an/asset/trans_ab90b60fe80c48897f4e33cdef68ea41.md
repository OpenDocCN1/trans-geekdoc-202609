

## 7.8 Maximum-Likelihood Procedure for SMRQ

由于 SMRQ 损失函数是检查函数的更平滑版本，可以使用最大似然估计（MLE），如第 3 章所述。要使用最大似然估计程序推导 SMRQ 损失，我们需要一个概率密度函数（PDF），\( f_X(x) \)。由于我们只有损失函数作为起点，因此可以使用反向 MLE 规则（参见第 3.5 节）。也就是说，我们知道 \( \rho(x) = -\log f_X(x) \)。然后，根据反向 MLE 程序得出

\( f_X(x) = \frac{1}{\kappa} e^{-\rho_{SMRQ}(x;\tau)}, \tag{7.8.1} \)

其中

\( \rho_{SMRQ}(x;\tau) = \frac{1}{3} \log \left( \cosh \left( \frac{3x}{2} \right) \right) + \left( \tau - \frac{1}{2} \right)x, \tag{7.8.2} \)

使用 \( a = 1.5 \) 如公式 (7.5.7) 所示。应用该程序，PDF 的形式由以下式给出

\( f_X(x) = \frac{e^{-(\tau - \frac{1}{2})x}}{\kappa \cosh(3x/2)^{\frac{1}{3}}}, \tag{7.8.3} \)

其中归一化常数 \(\kappa\) 将作为所选 \(\tau\) 的函数而变化。对于 \(\tau = 0.5\)，我们得到 \(\kappa\) 如下

\(\kappa = \int_{-\infty}^{\infty} \frac{e^{-(\frac{1}{2}-\frac{1}{2})x}}{\cosh(3x/2)} = 4.857,\)

并且对于 \(\tau = 0.25\)，我们使用以下方法求得 \(\kappa\)

\(\kappa = \int_{-\infty}^{\infty} \frac{e^{-(\frac{1}{4}-\frac{1}{2})x}}{\cosh(3x/2)^{\frac{1}{3}}} = 6.546.\)

对于 \(\tau = 0.75\)，我们使用以下方法求得 \(\kappa\)

\(\kappa = \int_{-\infty}^{\infty} \frac{e^{-(\frac{3}{4}-\frac{1}{2})x}}{\cosh(3x/2)^{\frac{1}{3}}} = 6.546.\)

![](img/f26d7f591c2a080d86425985301266a4_223_0.png)

![](img/f26d7f591c2a080d86425985301266a4_224_0.png)

图 7.14 五个不同 \(\tau\) 值的分位函数 PDF。五个图均合并在右下角面板中。

图 7.13 给出了 \(\kappa\) 与 \(\tau\) 的关系图，使用了多个不同的 \(\tau\) 值。现在可以绘制这些分布以揭示其特征。

从公式 (7.8.3) 和图 7.13 给出的归一化常数 \(\kappa\) 出发，选取了不同的 \(\tau\) 值并将其关联分布绘制在图 7.14 中。所示情况为 \(\tau = 0, 0.25, 0.5, 0.75,\text{和 } 1.0\)。图 7.14 与图 7.5 之间存在一一对应关系。\(\tau = 0.25\) 和 \(\tau = 0.75\) 的分布是镜像关系，\(\tau = 0.0\) 和 \(\tau = 1.0\) 的分布也是镜像关系。唯一的对称分布对应于 \(\tau = 0.5\)。

既然我们现在有了 PDF 的方程，就可以求得期望值和方差。例如，设置 \(\tau = 0.5\)，我们得到

\(\mathbb{E}[X] = 0\) (7.8.4)

并且通过积分得知 \(\mathbb{E}[X^2] = 8.29\)，我们有

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = 8.29 - 0^2 = 8.29\). (7.8.5)

但是，对于 \(\tau = 0.75\)，我们得到

\(\mathbb{E}[X] = -3.7\) (7.8.6)

并且

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = 34.4 - (-3.7)^2 = 20.7\). (7.8.7)

到目前为止本书中遇到的所有分布均值均为 0，但在分位回归中，关联的 PDF 均值均不为 0，除非 \(\tau = 0.5\)。从上面可以看出，\(\tau = 0.75\) 的分布均值为负而非 0，而 \(\tau = 0.25\) 的均值为正而非 0。这可以从图 7.14 中看出。此外，方差不是常数，而是随着 \(\tau\) 接近 1 或 0 而增加。

对于给定的 \(\tau\)，可以使用以下步骤推导 MLE。首先，似然函数为

\(\begin{aligned} L(\mathbf{x}_1, ..., \mathbf{x}_n | \tau) = \prod_{i=1}^n \left( \frac{e^{-(\tau - \frac{1}{2}) x_i}}{\kappa \cosh (3x_i / 2)^{\frac{1}{3}}} \right). \end{aligned}\)

然后，负对数似然为

\(\begin{aligned} -\ell(x_1, ..., x_n | \tau) = \sum_{i=1}^n \left[ \frac{1}{3} \log \left( \cosh \left( \frac{3x_i}{2} \right) \right) + \left( \tau - \frac{1}{2} \right) x_i \right] + n \log(\kappa). \end{aligned}\)

因此，去除常数项后，我们得到损失函数为

\(\begin{aligned} J^{\text{SMRQ}}(\boldsymbol{\beta} | \tau) = \sum_{i=1}^n \left[ \frac{1}{3} \log \left( \cosh \left( \frac{3x_i}{2} \right) \right) + \left( \tau - \frac{1}{2} \right) x_i \right]. \end{aligned}\)

估计是通过选择 \(\tau\) 然后按以下方式进行优化得到的：

\(\begin{aligned} \hat{\boldsymbol{\beta}}^{\text{SMRQ}} = \text{argmin}_{\boldsymbol{\beta} \in \mathbb{R}^{d+1}} \sum_{i=1}^n \left[ \frac{1}{3} \log \left( \cosh \left( \frac{3r_i}{2} \right) \right) + \left( \tau - \frac{1}{2} \right) r_i \right]. \end{aligned}\)

在上述内容中，哑变量 \(x_i\) 被残差 \(r_i = y_i - \mathbf{x}_i^\top \hat{\boldsymbol{\beta}}^{\text{SMRQ}}\) 替换，\(i = 1, ..., n\)。

## 7.9 Standard Error Computation

标准误（s.e.’s）表示估计值周围的不确定性，如第 3 章所述。它基本上是每个估计值的标准差计算值。在使用 log-cosh 的分位回归中，可以使用第 3 章的相同一般公式来获得标准误。然而，每个 \(\tau\) 都会有一组不同的 s.e.’s，因此必须分别为每种情况计算。对于大 \(n\)，我们将估计值视为正态分布，因此可以使用

\(\text{Var}(\hat{\boldsymbol{\beta}}^{\text{SMRQ}}) = \nu^2 (\mathbf{X}^\top \mathbf{X})^{-1},\)

然后定义术语 \(\nu^2\) 如下：

\(\nu^2 = s^2 \frac{\text{E}[\psi_{\text{SMRQ}}(z)^2]}{\text{E}[\psi'_{\text{SMRQ}}(z)]^2},\)

其中 \(z = (r - \mu) / s\)，其无偏估计可以通过将期望替换为平均值来获得（如第 3 章所述）：

\(\hat{\nu}^2 = s^2 \frac{ \frac{1}{n} \sum \psi_{\text{SMRQ}}(r_i / \hat{s})^2 }{ [\frac{1}{n} \sum \psi'_{\text{SMRQ}}(r_i / \hat{s})]^2 } \frac{n}{n - d - 1}.\)

在上述内容中，我们假设 \(\tau = 0.5\)，且

\(\psi_{\text{SMRQ}}(r_i / \hat{s}) = \frac{1}{2} \tanh \left( \frac{3r_i}{2\hat{s}} \right) + \left( \tau - \frac{1}{2} \right),\)

并且

\(\psi'_{\text{SMRQ}}(r_i / \hat{s}) = \frac{3}{4} \text{sech}^2 \left( \frac{3r_i}{2\hat{s}} \right),\)

表 7.3 瑞士生育率数据集中 RQ 和 SMRQ 分位回归的估计值和标准误，\(\tau = 0.5\)。

| 特征 | $\hat{\beta}^{RQ}$ | s.e.$(\hat{\beta}^{RQ})$ | $\hat{\beta}^{SMRQ}$ | s.e.$(\hat{\beta}^{SMRQ})$ |
|---|---|---|---|---|
| 截距 | 63.49 | 15.60 | 62.14 | 10.41 |
| 农业 | −0.20 | 0.10 | −0.20 | 0.07 |
| 检验 | −0.46 | 0.37 | −0.27 | 0.25 |
| 教育 | −0.79 | 0.27 | −0.88 | 0.18 |
| 天主教 | 0.10 | 0.05 | 0.10 | 0.03 |
| 婴儿死亡率 | 1.46 | 0.56 | 1.42 | 0.37 |

其中残差由 \(r_i = y_i - \mathbf{x}_i^\top \hat{\boldsymbol{\beta}}^{\text{SMRQ}}\) 给出，\(i = 1, \dots, n\)。最后，对于所需的 \(\hat{s}\) 和 \(\hat{s}^2\) 项，我们首先按以下方式获得 \(s\) 的鲁棒估计（参见公式 (1.4.6)）：

\(\hat{s} = \text{MADN}(\mathbf{r}),\) (7.9.6)

然后对其求平方。s.e.’s 计算为协方差矩阵 \(\nu^2(\mathbf{X}^\top \mathbf{X})^{-1}\) 对角元素的平方根。

表 7.3 使用瑞士生育率数据集提供了 RQ 和 SMRQ 的估计值和 s.e. 值。在此情况下，感兴趣的分位数为 \(\tau = 0.5\)。表表明，虽然估计值相似，但 RQ 的标准误略大于 SMRQ。

为了在一系列分位数上比较两种方法，一个表格是不够的。由于该数据集有 \(d = 5\) 个解释变量，因此基于 \(L_2\)-范数显示每个 \(\tau\) 的汇总 s.e.’s 是合适的。使用以下公式：

\(\|\text{s.e.}\|_2 = \sqrt{\text{s.e.}_1^2 + \cdots + \text{s.e.}_d^2}.\) (7.9.7)

**练习：** 使用表 7.3 计算瑞士生育率数据集中 \(\tau = 0.5\) 时解释变量的 s.e.’s 的 \(L_2\)-范数。

**答.：** 对于 RQ，\(\|\text{s.e.}\|_2 = \sqrt{0.10^2 + 0.37^2 + 0.27^2 + 0.05^2 + 0.56^2} = 0.732\)。

对于 SMRQ，\(\|\text{s.e.}\|_2 = \sqrt{0.07^2 + 0.25^2 + 0.18^2 + 0.03^2 + 0.37^2} = 0.487\)。\(\square\)

图 7.15 说明了瑞士生育率数据集中 s.e.’s 与分位数参数 \(\tau\) 之间的关系。SMRQ 和 RQ 的标准误的 \(L_2\)-范数在图 7.15 中绘制。在顶部面板的 SMRQ 情况下，针对不同的鲁棒系数 \(a\) 值展示了多个图表。每个图表都有不同的误差轨迹，当 \(\tau\) 从 0 移动到 1 时。与 \(a = 1.5\) 相关的图表为所有 \(\tau\) 值提供了相对较低的标准误。这是 \(a = 1.5\) 是 SMRQ 合适值的又一个原因。其他图表在 \(\tau\) 接近 0 或 1 时开始偏离其中间范围值，尤其是对于 \(a\) 值较低的图表。

在下部面板中，比较了 RQ 和 SMRQ（\(a = 1.5\)）的标准误图表。RQ 的图表明总体标准误较高，并且它不是 \(\tau\) 的平滑函数，原因是众多

