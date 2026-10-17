

# FTS 预测

FTS 预测是传统时间序列预测的一个分支，其中观测值为模糊集 \[[3](#bodymatter-007.xhtml#b_9783110670905-007_ref_003)\]，并在当前观测值与前一观测值之间建立关系。该主题 \[[4](#bodymatter-007.xhtml#b_9783110670905-007_ref_004), [5](#bodymatter-007.xhtml#b_9783110670905-007_ref_005), [6](#bodymatter-007.xhtml#b_9783110670905-007_ref_006)\] 最早于 1993 年和 1994 年提出。随后，其简化形式 \[[7](#bodymatter-007.xhtml#b_9783110670905-007_ref_007)\] 于 1996 年提出。在一阶预测模型中，当前状态仅依赖于前一状态。在高阶预测模型中，当前状态依赖于多个前一状态。FTS 模型已应用于各种应用领域，例如学生入学人数 \[[5](#bodymatter-007.xhtml#b_9783110670905-007_ref_005), [6](#bodymatter-007.xhtml#b_9783110670905-007_ref_006), [7](#bodymatter-007.xhtml#b_9783110670905-007_ref_007), [8](#bodymatter-007.xhtml#b_9783110670905-007_ref_008), [9](#bodymatter-007.xhtml#b_9783110670905-007_ref_009), [10](#bodymatter-007.xhtml#b_9783110670905-007_ref_010)\]、温度 \[[10](#bodymatter-007.xhtml#b_9783110670905-007_ref_010), [11](#bodymatter-007.xhtml#b_9783110670905-007_ref_011)\]、失业率 \[[8](#bodymatter-007.xhtml#b_9783110670905-007_ref_008)\]、股票交易所 \[[8](#bodymatter-007.xhtml#b_9783110670905-007_ref_008), [9](#bodymatter-007.xhtml#b_9783110670905-007_ref_009), [10](#bodymatter-007.xhtml#b_9783110670905-007_ref_010), [11](#bodymatter-007.xhtml#b_9783110670905-007_ref_011), [12](#bodymatter-007.xhtml#b_9783110670905-007_ref_012), [13](#bodymatter-007.xhtml#b_9783110670905-007_ref_013), [14](#bodymatter-007.xhtml#b_9783110670905-007_ref_014)\] 等等。

许多研究者已成功将反向传播神经网络（BPNN）集成到模糊预测模型中 \[[9](#bodymatter-007.xhtml#b_9783110670905-007_ref_009), [10](#bodymatter-007.xhtml#b_9783110670905-007_ref_010), [11](#bodymatter-007.xhtml#b_9783110670905-007_ref_011), [12](#bodymatter-007.xhtml#b_9783110670905-007_ref_012), [13](#bodymatter-007.xhtml#b_9783110670905-007_ref_013), [14](#bodymatter-007.xhtml#b_9783110670905-007_ref_014)\]。在过去，对于使用 BPNN 的高阶模型，不同时期的值会一次性一起输入到输入层，并且只有一个隐藏层。但在本工作中，不同时期的输入被输入到网络的不同层，而不是同一层。这是所提方法与现有基于神经网络的高阶 FTS 模型之间的主要区别。BPTT 算法有许多变体。不同类型的 BPTT 算法的描述见 Williams 和 Zipser 于 1995 年发表的著作 \[[15](#bodymatter-007.xhtml#b_9783110670905-007_ref_015)\]。在 epochwise BPTT 算法中，权重更新仅在每个训练示例序列结束时进行（该序列称为一个 epoch）。epochwise BPTT 模型和实时 BPTT 模型中梯度值的计算相同。但它们之间的基本区别在于，在 epochwise BPTT 中，除了 ∂ 值外，每个中间步骤的误差也被考虑。在截断 BPTT 算法中，记为 BPTT（*h*），仅使用前 *h* 个时间步的数据值。

本章介绍了截断性质的 epochwise BPTT 模型。该模型将前序列值作为输入（模糊输入）输入到展开网络的不同层。阶数与网络中的时间步数（或层数）相同。该模型称为 TBPTT（*h*1，*h*2）。其中，*h*1 是前向传递中的步数，*h*2 是后向传递中的步数。在本研究中，*h*1 = *h*2。

本工作按以下章节介绍：在 [第 7.2 节](#bodymatter-007.xhtml#b_9783110670905-007_s_007_s_002) 中介绍了 BPTT 模型的描述。[第 7.3 节](#bodymatter-007.xhtml#b_9783110670905-007_s_007_s_003) 描述了整个方法。实验结果的比较显示在 [第 7.4 节](#bodymatter-007.xhtml#b_9783110670905-007_s_007_s_004)。结论在 [第 7.5 节](#bodymatter-007.xhtml#b_9783110670905-007_s_007_s_005) 中介绍。

## 7.2 时间反向传播的基本概念

时间反向传播的基本原理 \[[16](#bodymatter-007.xhtml#b_9783110670905-007_ref_016), [17](#bodymatter-007.xhtml#b_9783110670905-007_ref_017)\] 是在时间步 1、2、…、*T* 展开网络，以存储更长的历史信息。展开技术将循环网络转换为具有多步计算的等效前馈网络。展开网络使用反向传播进行训练，每个等效连接权重的所有副本应相同。权重更新是使用每层计算的梯度之和完成的 \[[Figure 7.1](#bodymatter-007.xhtml#b_9783110670905-007_fig_001)\]。

基本算法：

1. 展开循环网络，任意层数（在前向传递中）。
2. 反向传播误差（在后向传递中）。
3. 每个展开阶段的权重变化（每个折叠上的等效连接的连接权重）相加，以得到一组权重变化。

![Figure 7.1: Example of unrolling.](graphic/converted/b_9783110670905-007_fig_001.png)

Figure 7.1: Example of unrolling.

BPTT 算法有许多变体。在本研究中，将采用 Epochwise BPTT \[[15](#bodymatter-007.xhtml#b_9783110670905-007_ref_015)\] 进行预测。让我们考虑一个展开网络。时间 *t* + 1 时第 *n* 个处理节点的输出表示为，

(7.1)$S\_{n}\\left( {t + 1} \\right) = \\!\\sum\\limits\_{l \\in u}{w\_{nl}y\_{l}\\left( t \\right) +}\\!\\sum\\limits\_{l \\in I}{w\_{nl}x\_{l}\\left( {t + 1} \\right)}$ 

在每个节点中，时间 *t* + 1 时的输出是当前输入 *x*（*t* + 1）和前一输出值 *Y*（*t*）的函数。*x*[l]（*t*）表示时间 *t* 时第 *n* 个节点的外部输入信号。元素 *w*[nl] 表示从第 *l* 个节点到第 *n* 个节点的链路上的权重。输入节点集合由 *I* 表示，*u* 表示循环层中的节点集合。每个处理节点应用逻辑函数：

(7.2)*Y*[*n*](*t*+1) = *f*[*n*](*S*[*n*](*t*+1)) (7.3)*f*[*n*]^′(*S*[*n*](*t*+1)) = *Y*[*n*](*t*+1)\[1−*Y*[*n*](*t*+1)\] 

Epochwise BPTT 过程通过重复 [eqs. (7.4)](#bodymatter-007.xhtml#b_9783110670905-007_eq_004) 和 [(7.5)](#bodymatter-007.xhtml#b_9783110670905-007_eq_005) 进行。

(7.4)$\\in\_{n}\\left( {t;\\, F} \\right) = \\,\\left\\{ \\begin{matrix} \\begin{matrix} \\begin{matrix} {e\_{n}\\left( {t;\\, F} \\right)\\ \\ \\!\\quad\\quad\\quad\\quad\\quad\\quad\\quad\\quad{if}\\ t = T} \\\\ \\end{matrix} \\\\ {e\_{n}\\left( {t;\\, F} \\right) + \\sum\\limits\_{l \\in u}{w\_{ln}\\partial\_{l}\\left( {t + 1;F} \\right)\\,\\,\\,\\,{if}\\ t < T}} \\\\ \\end{matrix} \\\\ \\end{matrix} \\right.$ (7.5)∂[*n*](*t*; *F*) = *f*[*n*]^′(*S*[*n*](*t*))∈[*n*](*t*; *F*) 

对于第 *n* 个节点，时间 “*t*” 时的误差“*e*”是通过从目标中减去实际输出来计算的。

每个连接权重 *w[ij]* 按以下方式更新：

(7.6)$\\left( {\\partial F/\\partial w\_{ij}} \\right) = \\left( {learning\\, rate} \\right) \\ast \\sum\\limits\_{t = 0}^{T - 1}x\_{j}\\left( t \\right)\\partial\_{i}\\left( {t + 1,F} \\right)$ 

方程中的“*x*“项表示时间 *t* 时网络的处理节点输出或外部输入节点。最终时间步由 *T* 表示。

## 7.3 拟议方法

