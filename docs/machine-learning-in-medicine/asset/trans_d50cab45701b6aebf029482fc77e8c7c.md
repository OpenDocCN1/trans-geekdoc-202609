
然而，大多数传统的数值方法 \[[6](#C11_chapter4.xhtml#ref4_6), [7](#C11_chapter4.xhtml#ref4_7), [8](#C11_chapter4.xhtml#ref4_8)\] 都是为准确近似软组织生物热传导特性而开发的，却未考虑快速计算的需求。例如，已报道使用传统方法模拟热消融过程所需的计算时间从数分钟到数小时不等 \[[9](#C11_chapter4.xhtml#ref4_9)\]，这主要是因为在每个时间步骤中都需要求解非线性生物热传导方程。基于有限差分法（FDM） \[[10](#C11_chapter4.xhtml#ref4_10)\]，Schwenke 等人 \[[11](#C11_chapter4.xhtml#ref4_11)\] 和 Kalantzis 等人 \[[12](#C11_chapter4.xhtml#ref4_12)\] 研究了基于图形处理单元（GPU）的快速热消融模拟技术。Zhang 等人 \[[13](#C11_chapter4.xhtml#ref4_13),[14](#C11_chapter4.xhtml#ref4_14)\] 和 Mariappan 等人 \[[15](#C11_chapter4.xhtml#ref4_15)\] 提出了基于 GPU 加速的有限元方法，用于高速生物热传导热消融求解。He 和 Liu \[[16](#C11_chapter4.xhtml#ref4_16)\] 设计了一种交替显式方法，Carluccio 等人 \[[17](#C11_chapter4.xhtml#ref4_17)\] 则开发了一种基于空间滤波的方法以降低计算时间。其他方法如快速显式动力学有限元算法 \[[18](#C11_chapter4.xhtml#ref4_18),[19](#C11_chapter4.xhtml#ref4_19)\]、基于快速傅里叶变换的 FDM 算法 \[[20](#C11_chapter4.xhtml#ref4_20)\]、模型顺序缩减方法 \[[21](#C11_chapter4.xhtml#ref4_21)\]、基于有限体积的多网格方法 \[[22](#C11_chapter4.xhtml#ref4_22),[23](#C11_chapter4.xhtml#ref4_23)\] 和基于无网格点拼接的动态模式分解方法 \[[24](#C11_chapter4.xhtml#ref4_24)\] 也均被研究用于快速生物热传导分析。

近期，卷积神经网络（CNN）因其在生物力学领域的快速数值计算能力而受到关注 \[[25](#C11_chapter4.xhtml#ref4_25), [26](#C11_chapter4.xhtml#ref4_26), [27](#C11_chapter4.xhtml#ref4_27), [28](#C11_chapter4.xhtml#ref4_28)\]，并由于细胞的集体和同步计算活动而能够实现快速计算 \[[29](#C11_chapter4.xhtml#ref4_29)\]。CNN 由 Chua 和 Yang 发展 \[[30](#C11_chapter4.xhtml#ref4_30)\]，主要用于图像处理，如噪声消除、模式识别和特征提取 \[[31](#C11_chapter4.xhtml#ref4_31)\]（参见综述论文 \[[32](#C11_chapter4.xhtml#ref4_32)\] 和专著 \[[33](#C11_chapter4.xhtml#ref4_33)\]）。可以看出，CNN 方案能够对包括反应-扩散方程、Burgers 方程、纳维尔–斯托克斯方程和热传导方程等许多非线性偏微分方程提供优秀的近似解 \[[34](#C11_chapter4.xhtml#ref4_34),[35](#C11_chapter4.xhtml#ref4_35)\]，因此已将 CNN 用于建模多种非线性动态系统，包括机械振动系统 \[[36](#C11_chapter4.xhtml#ref4_36)\]、模式形成与波传播 \[[37](#C11_chapter4.xhtml#ref4_37)\]、微分方程 \[[29](#C11_chapter4.xhtml#ref4_29)\]、可变形模型 \[[38](#C11_chapter4.xhtml#ref4_38),[39](#C11_chapter4.xhtml#ref4_39)\] 和生物热传导问题 \[[40](#C11_chapter4.xhtml#ref4_40),[41](#C11_chapter4.xhtml#ref4_41)\]，以实现高效、有效的解法。本文基于计算特性，采用 CNN 高效求解生物热传导方程用于生物软组织热剂量建模，为热消融癌症治疗提供计算机辅助规划与分析。本文在 2D 和 3D 规则及不规则计算域的网格上给出了生物热传导方程的 CNN 形式ulation，并利用所提出的 CNN 模型预测软组织温度分布及相应的热剂量，并通过一个具有临床相关性的肝癌局部热消融情景进行演示。

本文的其余部分结构如下：[Section 4.2](#C11_chapter4.xhtml#secc004_4) 介绍软组织热剂量建模的基本控制方程，随后在 [Section 4.3](#C11_chapter4.xhtml#secc004_5) 中介绍 CNN 架构及其在 2D 和 3D 规则与不规则网格上的形式ulation；[Section 4.4](#C11_chapter4.xhtml#secc004_6) 展示针对特定患者的热剂量估计结果以及 HIFU 消融肝肿瘤的应用；讨论在 [Section 4.5](#C11_chapter4.xhtml#secc004_7)；[Section 4.6](#C11_chapter4.xhtml#secc004_8) 则总结本工作。

## [4.2 Soft Tissue Thermal Dose MODELING](#C11_chapter4.xhtml#rsecc004_4)

不可逆的细胞蛋白变性和凝固坏死发生在软生物组织在特定温度下保持一定时间时。尽管一些研究 \[[42](#C11_chapter4.xhtml#ref4_42),[43](#C11_chapter4.xhtml#ref4_43)\] 假设凝固坏死区（病灶）近似为球体或椭圆体等规则形状，但已证明病灶的范围与组织所达到的热剂量有关，热剂量是组织热暴露历史的度量。本文采用经验热剂量 CEM[43]，该指标将病灶范围与在 43°C 的组织累计等效分钟数（CEM）联系起来 \[[44](#C11_chapter4.xhtml#ref4_44)\]，并认为当热剂量达到 240 CEM[43] 时，肿瘤坏死发生 \[[45](#C11_chapter4.xhtml#ref4_45)\]。数学上，CEM[43] 由

``` 
{\\text{CEM}_{43} = \\int\\limits_{}^{t}R^{({43 - T{(t)}})}dt}\\mspace{54mu}\\operatorname{(4.1)}
``` 

其中 *t* 为热暴露的持续时间，*T*(*t*) 为局部组织温度，*R* 为常数，给出为

``` 
$$R = \\left\\{ \\begin{array}{l} {0.25,\\operatorname{}\\operatorname{}\\left( {T\\left( t \\right) < 43{^\\circ}\\text{C}} \\right)} \\\\ {0.5,\\operatorname{}\\operatorname{}\\operatorname{}\\operatorname{}\\operatorname{}\\left( {T\\left( t \\right) \\geq 43{^\\circ}\\text{C}} \\right)} \\\\ \\end{array} \\right.}\\mspace{54mu}\\operatorname{(4.2)}
``` 

为求得 CEM[43]，必须计算并记录软组织温度场（温度随时间变化的历史）。生物软组织的热传导由 Pennes 生物热传导方程 \[[46](#C11_chapter4.xhtml#ref4_46)\] 模型，该方程考虑了热传导、血液灌注、代谢热生成以及外部热源的影响。已通过实验 \[[47](#C11_chapter4.xhtml#ref4_47),[48](#C11_chapter4.xhtml#ref4_48)\] 验证，Pennes 模型能够可靠预测组织温度，并被广泛用于超声热疗和热消融治疗的肿瘤管理 \[[49](#C11_chapter4.xhtml#ref4_49), [50](#C11_chapter4.xhtml#ref4_50), [51](#C11_chapter4.xhtml#ref4_51), [52](#C11_chapter4.xhtml#ref4_52)\]。对于质量密度 *ρ*、比热容 *C*、热导率 *k*、血灌注率 *w*[*b*]、血液比热容 *C*[*b*]、动脉血温度 *T*[*a*]、代谢热生成率 *Q* 以及外部热源 *H*，Pennes 生物热传导方程为

``` 
$$\rho C\\frac{\\partial T\\left( t \\right)}{\\partial t} = \\nabla \\cdot \\left( {k\\nabla T\\left( t \\right)} \\right) - w\_{b}C\_{b}\\left( {T\\left( t \\right) - T\_{a}} \\right) + Q + H}\\mspace{54mu}\\operatorname{(4.3)}
``` 
