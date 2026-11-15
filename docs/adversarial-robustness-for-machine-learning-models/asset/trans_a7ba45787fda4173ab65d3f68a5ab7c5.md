

应用于改进表示学习（Hjelm et al., 2019; Zhu et al., 2020a）给定一个数据集。然而，针对给定数据样本生成对抗样本时，原生 MINE 不适用，因为它仅适用于一批数据样本（以便利用经验数据分布计算 MI 估计），而不适用于单个数据样本。

Per-sample MINE。给定数据样本 $x$ 及其扰动样本 $x + \delta$，我们可以利用它们的随机采样或卷积输出构建辅助分布，通过 MINE 计算 MI 作为相似度量度，称为“Per-sample MINE”。

随机采样。使用压缩采样（Candès and Wakin, 2008），我们对给定样本 $x$ 进行独立高斯采样，以获得 $K$ 个压缩样本的一批 $\{x_k, (x + \delta)_k\}_{k=1}^K$ 用于通过 MINE 计算 $I_\Theta(x, x + \delta)$。我们还注意到，随机采样对底层机器学习模型无感知，因为它直接应用于数据样本。

卷积层输出。当底层神经网络模型使用卷积层处理输入数据时（这对于图像数据几乎是默认设置），我们建议使用数据输入第一个卷积层的输出，记作 conv，以获得 $K$ 个特征图 $\{conv(x)_k, conv(x + \delta)_k\}_{k=1}^K$ 用于计算 $I_\Theta(x, x + \delta)$。

统一攻击表述。我们使用 Per-sample MINE 对有监督和无监督对抗样本的目标进行形式化。如表 21.1 所示，有监督设置旨在找到最相似的导致预测逃逸的样本，从而形成一个 MINE 最大化问题。无监督设置旨在找到最不相似但训练损失更小的样本，从而形成一个 MINE 最小化问题。这两个问题都可以使用统一的 MinMax 算法（算法 7）高效求解。

有监督对抗样本。令 $(x, y)$ 表示数据样本 $x$ 及其真实标签 $y$ 的一对。有监督对抗样本的目标是找到对 $x$ 的扰动 $\delta$，使得 MI 估计 $I_\Theta(x, x + \delta)$ 最大化，且 $x + \delta$ 的预测与 $y$ 不同（或为目标类别 $y' \neq y$），其表述为

最大化 $I_\Theta(x, x + \delta)$
受限于 $x + \delta \in [0, 1]^d, \delta \in [-\epsilon, \epsilon]^d$ 且 $f_x(x + \delta) \le 0. \quad (21.1)$

约束 $x + \delta \in [0, 1]^d$ 确保 $x + \delta$ 位于维度为 $d$ 的（归一化）数据空间中，且约束 $\delta \in [-\epsilon, \epsilon]^d$ 对应典型的有界 $L_\infty$ 扰动范数。我们包含此有界范数约束以便与其他有界范数攻击进行直接比较。通过设置 \(\epsilon = 1\)，我们可以忽略此约束。最后，函数 \(f_x^{\text{sup}}(x + \delta)\) 是攻击成功评估函数，其中 \(f_x^{\text{sup}}(x + \delta) \le 0\) 表示 $x + \delta$ 是一个预测逃逸对抗样本。对于非靶向攻击，我们可以使用 Carlini 和 Wagner (2017b) 设计的攻击函数 \(f_x^{\text{sup}}\)，即 \(f_x^{\text{sup}}(x') = \text{logit}(x')_y - \max_{j:j \neq y} \text{logit}(x')_j + \kappa\)，其中 \(\text{logit}(x')_j\) 是神经网络 logit（预 softmax）层的第 \(j\) 个类别输出，\(\kappa \ge 0\) 是原始预测 \(\text{logit}(x')_y\) 与所有非 \(y\) 类别中最高预测 \(\max_{j:j \neq y} \text{logit}(x')_j\) 之间的可调间隔。同样，对于带类别标签 \(y' \neq y\) 的靶向攻击，攻击函数为 \(f_x^{\text{sup}}(x') = \max_{j:j \neq y'} \text{logit}(x')_j - \text{logit}(x')_{y'} + \kappa\)。

*无监督对抗样本。* 许多机器学习任务，如数据重构和无监督表示学习，不使用数据标签，这阻止了上述有监督攻击函数的使用。此处我们使用自编码器 \(\Phi\) 进行数据重构以阐释无监督攻击表述。该设计原则可自然扩展到其他无监督任务。自编码器 \(\Phi\) 以数据样本 \(x\) 作为输入并输出重构数据样本 \(\Phi(x)\)。不同于有监督攻击的原理，对于无监督攻击，我们建议使用 MINE 寻找相对于 \(x\) 的 *最不相似* 扰动数据样本 \(x + \delta\)，同时确保 \(\Phi(x + \delta)\) 的重构损失不大于 \(\Phi(x)\)（即数据重构的攻击成功标准）。无监督攻击表述如下：

\(\text{Minimize}_{\delta} \quad I_\Theta(x, x + \delta)\)
\(\text{受限于 } x + \delta \in [0, 1]^d, \delta \in [-\epsilon, \epsilon]^d\) 且 \(f_x(x + \delta) \le 0. \quad (21.2)\)

前两个约束规范可行数据空间和扰动范围。对于 \(L_2\)-范数重构损失，无监督攻击函数为

\(f_x^{\text{unsup}}(x + \delta) = \|x - \Phi(x + \delta)\|_2 - \|x - \Phi(x)\|_2 + \kappa, \quad (21.3)\)

这意味着攻击成功（即 \(f_x^{\text{unsup}}(x + \delta) \le 0\)），条件是 \(x + \delta\) 相对于原始样本 \(x\) 的重构损小于原生重构损失减去非负间隔 \(\kappa\)，即 \(\|x - \Phi(x + \delta)\|_2 \le \|x - \Phi(x)\|_2 - \kappa\)。换句话说，我们的无监督攻击表述旨在找到 MINE 度量下相对于 \(x\) 最不相似的扰动样本 \(x + \delta\)，且相对于 \(x\) 具有比 \(x\) 更小的重构损失。此类 UAE 因此与低损失样本的泛化误差相关，因为模型对这些未见样本存在偏差。

基于 MINE 的 MinMax 算法。此处我们介绍一种统一的 MinMax 算法，用于求解上述有监督和无监督攻击表述。其算法收敛性证明见 (Hsu et al., 2022)。为简化，我们将使用 \( f_x \) 表示 \( f_x^{\text{sup}} \) 或 \( f_x^{\text{unsup}} \) 的攻击准则。不失一般性，我们将分析带约束的最大化 \( I_\Theta \) 的有监督攻击目标。该分析同样适用于无监督情况，因为最小化 \( I_\Theta\) 等价于最大化 \( I'_\Theta\)，其中 \( I'_\Theta = -I_\Theta \)。

基于 MINE 的攻击生成可以重新表述为以下带简单凸集约束的 MinMax 优化问题：

\(\text{Min}_{\delta: x+\delta \in [0,1]^d, \delta \in [-\epsilon, \epsilon]^d} \text{Max}_{c \ge 0} J(\delta, c) \triangleq c \cdot f_x^+(x + \delta) - I_\Theta(x, x + \delta). \quad (21.4)\)

外层最小化问题在满足数据和扰动可行性约束 \( x + \delta \in [0, 1]^d \) 及 \( \delta \in [-\epsilon, \epsilon]^d \) 的条件下寻找最佳扰动 \(\delta\)，这两个约束均为具有已知解析投影函数的凸集。内层最大化将变量 \( c \ge 0 \) 与原始攻击准则 \( f_x(x + \delta) \le 0 \) 关联，其中 \( c \) 乘以 \( f_x\) 的 ReLU 激活函数，记作 \( f_x^+(x + \delta) = \text{ReLU}(f_x(x + \delta)) = \max\{f_x(x + \delta), 0\} \)。使用 \( f_x^+\) 意味着当攻击准则未满足时（即 \( f_x(x + \delta) > 0 \)），损失项 \( c \cdot f_x^+(x + \delta) \) 将出现在目标函数 \( F\) 中。另一方面，若攻击准则已满足（即 \( f_x(x + \delta) \le 0 \)），则 \( c \cdot f_x^+(x + \delta) = 0 \)，目标函数 \( F\) 仅包含相似度损失项 \( -I_\Theta(x, x + \delta) \)。因此 \( f_x^+\) 的设计平衡了与攻击成功和基于 MINE 的相似度相关的两个损失项之间的权衡。Hsu et al. (2022) 提出在内层和外层步骤之间使用交替投影梯度下降来求解 MinMax 攻击问题，如算法 7 所示。参数 \(\alpha\) 和 \(\beta\) 分别表示最小化步骤和最大化步骤的步长。当 \( f_x(x + \delta) \le 0 \) 时，相对于 \(\delta\) 的梯度 \(\nabla f_x^+(x + \delta)\) 被设为 0。MinMax 算法返回在 \(T\) 次迭代中具有最佳 MINE 值 \(I_\Theta^*(x, x + \delta^*)\) 的成功对抗样本 \(x + \delta^*\)。

## 21.2 经验比较

借助 MinMax 攻击算法和用于相似度评估的 Per-sample MINE，我们可以生成基于 MINE 的无监督对抗样

