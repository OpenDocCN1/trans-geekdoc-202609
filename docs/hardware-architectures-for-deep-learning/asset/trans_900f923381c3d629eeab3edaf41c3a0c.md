

## 272 深度学习硬件架构

其中 $\sigma_{ij}(\sigma_{jin})$ 是位于非反相（反相）行 $i$ 和列 $j$ 的忆阻器的电导，$V_{net}$ 是节点网的电压，参数 $\zeta$ 定义为：

$$\zeta = \frac{1}{\sum_{i=1}^N(\sigma_{jip} + \sigma_{jin})} \quad (11.3)$$

根据 (11.1)，每个权重采用两个忆阻器，这实现了正负权重的配置。在基于反相器的神经形态电路中，第一个反相器充当激活函数并对加权和执行非线性操作。然而，由于在这种实现中，需要神经元输出（下一层神经元的输入）的正、负值，因此利用另一个反相器来生成非反相输出（$O_p$）。因此，该结构中除输出层外的神经元都包含两个反相器。需要注意的是，由于反相器的效率远高于运算放大器，基于反相器的设计即使具有互补性，也更加高效。由于输出层的神经元输出被认为是网络主要的模拟输出，因此该神经元使用一个反相器。在本章中，反相器的工作电压为 $\pm V_{dd}/2$。注意，神经元的偏置输入可以通过考虑为神经元的额外恒定输入来实现。为了将神经网络权重映射到神经形态电路，我们等了 (11.1) 和 (11.2)。因此，权重（$w_{jip}$ 和 $w_{jin}$）可以计算为：

$$w_{jip} = \frac{\sigma_{jip}}{\sum_{m=1}^N(\sigma_{jmp} + \sigma_{jmn})} \\ w_{jin} = \frac{\sigma_{jin}}{\sum_{m=1}^N(\sigma_{jmp} + \sigma_{jmn})} \quad (11.4)$$

从而：

$$w_{jip} (\sum_{m=1}^N(\sigma_{jmp} + \sigma_{jmn})) - \sigma_{jip} = 0 \\ w_{jin} (\sum_{m=1}^N(\sigma_{jmp} + \sigma_{jmn})) - \sigma_{jin} = 0 \quad (11.5)$$

制备忆阻器的电导值限制在最小值 ($\sigma_{min}$) 和最大值 ($\sigma_{max}$) 之间。因此，在这项工作中，我们使用了 [39] 中的忆阻器参数，其中最大值最小值分别为 7.9 和 0.12$\mu\zeta$，这些值在求解 (11.5) 时使用。使用 (11.5) 并基于忆阻器电导的边界值，可以：

$$\sigma_{min} < w_{jip}\sum_{m=1}^N(\sigma_{jmp} + \sigma_{jmn}) < \sigma_{max} \\ w_{min} < w_{jin}\sum_{m=1}^N(\sigma_{jmp} + \sigma_{jmn}) < \sigma_{max} \quad (11.6)$$

### 基于反相器的忆阻神经形态电路

列出所有权重的方程 (11.5)，形成一个包含 $2N$ 个方程和 $2N$ 个未知数的方程组，通过求解该组将神经网络权重映射到忆阻器的电导值。训练过程中使用的该方程组可以表示为：

$$\begin{bmatrix} W_{j1p}-1 & W_{j1p} & \dots & W_{j1n} \\ W_{j1n} & W_{j1n}-1 & & W_{j1p} \\ & \dots & & \dots \\ W_{Jnp} & & W_{Jnn} & \dots & W_{Jn}-1 \end{bmatrix} = \begin{bmatrix} 0 \\ \vdots \\ 0 \end{bmatrix} \begin{bmatrix} \sigma_{j1p} \\ \sigma_{j1n} \\ \sigma_{j2p} \\ \sigma_{j2n} \\ \vdots \\ \sigma_{JNp} \\ \sigma_{Jn} \end{bmatrix} \quad (11.7)$$

由于 (11.7) 是齐次线性方程组，只有当其系数矩阵的行列式零时，它才有非平凡解。我们已经证明，应用以下条件会导致 (11.7) 系数矩阵的行列式零，从而产生非平凡解：

$$\sum_{i=1}^N(W_{jin} + W_{jip}) = 1 \quad (11.8)$$

假设满足 (11.8)，并将 (11.7) 系数矩阵的所有行合并到第一行，该系统可以重写为：

$$\begin{bmatrix} \sum_{i=1}^N(W_{jin} + W_{jip})-1 & \sum_{i=1}^N(W_{jin} + W_{jip}) & \dots & \sum_{i=1}^N(W_{jin} + W_{jip}) \\ W_{j1n} & W_{j1n}-1 & & W_{j1p} \\ & \dots & & \dots \\ W_{Jnp} & & W_{Jnn} & \dots & W_{Jn}-1 \end{bmatrix} \begin{bmatrix} \sum_{i=1}^N(\sigma_{jin} + \sigma_{jip}) \\ \sigma_{j1n} \\ \sigma_{j2p} \\ \sigma_{j2n} \\ \vdots \\ \sigma_{JNp} \\ \sigma_{Jn} \end{bmatrix} = \begin{bmatrix} 0 \\ \vdots \\ 0 \end{bmatrix} \quad (11.9)$$

由于 $\sum_{i=1}^N(W_{jin} + W_{jip}) = 1$，(11.9) 系数矩阵的第一行元素均为零。因此，该矩阵的行列式为零。因此，学习算法应在两个约束下训练神经网络：

- 权重必须为正，且忆阻器的电导必须在 $[\sigma_{min}, \sigma_{max}]$ 范围内。
- 进入神经元的权重之和必须等于 1（根据 11.8）。

### 1.3.2 输入接口 (DAC)

输入接口应将信号转换为模拟信号，因此需要 DAC。DAC 有多种实现方式（例如 [36, 40]为了在保持性能的同时降低功耗，我们建议不使用运算放大器等有源元件来实现 DAC [17]。建议的 DAC 结构如图 11.5 所示。在该结构中，DAC 的数字输入（$D_0 - D_{n-1}$）通过电阻 $(R, 2R, \dots, 2^{n-1}R)$ 缩放并累加在节点 $R_0$。模拟输出电压可以通过 KCL 方程找到：

$$\frac{V_{AO}}{R_{Load}} + \sum_{i=0}^{n-1} \frac{V_{Di}}{2^{n-1-i}R} = 0 \quad (11.10)$$

其中 $V_{Di}$ 是第 $i$ 个数字输入，$R_{Load}$ 是 DAC 驱动的忆阻阵列等效负载。使用 (11.10)，可以计算（真实的）$V_{AO}$：

$$V_{AO} = \frac{\sum_{i=0}^{n-1} \frac{V_{Di}}{2^{n-1-i}R}}{R_{Load}} \quad (11.11)$$

![](img/e6752b99eb162148c8944a57ea86_299_0.png)

图11.5 带负载的忆阻 DAC 结构

另一方面，在理想 DAC（无负载）中，输入输出关系给出：

$$\sum_{i=0}^{n-1} \frac{V_{A0}-V_{Di}}{2^{n-1-i}R} = 0 \quad (11.12)$$

这可以用于理想的 $V_{A0}$：

$$V_{A0ideal} = \sum_{i=0}^{n-1} \frac{V_{Di}}{2^{n-1-i}R} = \sum_{i=0}^{n-1} 2^i V_{Di} \quad (2^n - 1) \quad (11.13)$$

在这里，DAC 理想输出与真实输出之间的误差表示为：

$$Error = \frac{V_{A0ideal}-V_{A0}}{V_{A0ideal}} = 1 - \frac{V_{A0}}{V_{A0ideal}} = \frac{n}{R_{Load}} - \sum_{i=0}^{n-1} \frac{1}{2^{n-1-i}R} \quad (11.14)$$

假设神经网络的输入误差容差为 $\alpha$，可以确定 $R$ 的最大值 ($R_{max}$)：

$$\frac{n}{R_{Load}} - \sum_{i=0}^{n-1} \frac{1}{2^{n-1-i}R} < \alpha \quad (11.15)$$

重排上述不等式可以发现：

$$\frac{R}{R_{Load}}(n-\alpha) < \frac{2^n-1}{2^{n-1}} \quad (11.16)$$

最后：

$$R < R_{max} = \frac{2^n-1}{2^{n-1}} \times \frac{\alpha}{n-\alpha} \times R_{Load} \quad (11.17)$$

因此，在设计 DAC 时，$R$ 值应根据 $R_{Load}$ 和 $\alpha$ 选择。在 $R_{max}$ 小于可用忆阻器最小电阻的情况下，我们应该并联使用最小电阻的忆阻器。值得注意的是，由于忆阻器尺寸小，并联忆阻器的开销面积远小于运算放大器晶管占据的面积。

当 DAC 分率增加时，二进制权重忆阻器的电阻呈指数级增长（$R, 2R, \dots, 2^{n-1}R$）。由于忆阻器的电阻是有限的（限制在最大和最小电阻之间），可能需要大量的忆阻器。为了解决这个问题，对于更高的分率，我们建议将 DAC 的忆阻分支分组为 4 位（部分）簇，并使用第二级来组合部分簇的结果。

DAC 的第二级（被认为是最后一级）如图 11.6 所示合并到神经网络的第一层。为了训练神经网络，提取 DAC 电路模型并计算相应的模拟输出到数字输入。在这种方法中，输出的

