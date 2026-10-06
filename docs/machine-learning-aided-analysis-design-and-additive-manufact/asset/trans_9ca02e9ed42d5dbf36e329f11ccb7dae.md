

- [35] Ganapathi M., Anirudh B., Anant C., Polit O. 基于厚度扩展效应的三角变形理论功能梯度石墨烯增强多孔纳米复合弯梁的学特性，Mech Adv Mater Struct. n.d. 28;741–752.
- [36] Saidi AR, Bahaadini R, Majidi-Mozafari K. 气动载荷下石墨烯片增强多孔板的振动与稳定性分析。Compos Part B: Eng 2018;167:78-89.
- [37] Dong Y, Li Y, Chen Y, Wang Y. 旋转运动功能梯度石墨烯增强多孔纳米复合圆的振动特性。Compos Part B: Eng 2018;145:1–13.
- [38] Zhao J, Xie F, Wang S, Tang J, Wang Q. 一般弹性约束下功能梯度多孔（FGP）圆形、环形和扇形板的动力学分析。Compos Part B: Eng 2019;158:45–53.
- [39] Liu Y, Su S, Huang H, Liang Y. 物理中性轴功能梯度石墨烯夹层梁的热力耦合失稳分析。Compos Part B: Eng 2019;168:226–42.
- [40] Liu H, Wang J. 粘弹性Pasternak基础上磁电弹性多孔纳米梁的振动。Compos Part B: Eng 2018:155:244–56.
- [41] Gibson J, Ashby MF. 三维细胞材料力学。Proc R Soc A; Math Phys Eng S Soc 1982;43–59.
- [42] Ashby MF, Evans AG, Fleck NA, Gibson J, Hutchinson JW, Wadley HNG. 金属泡沫，设计指南。Butterworth-Heinemann; 2000.
- [43] Reddy JN. 复合板和壳的力学：理论与分析。CRC Press LLC; 2004.
- [44] Heyziger PR, Reddy JN. 用于弯曲和振动问题的高阶梁有限元。J Sound Vib 1988;126:309–26.
- [45] Ribano P, Preto M. 板的几何非线性、稳态、强制周期性振动，第一部分；J Sound Vib 1999:226:955–83.
- [46] Shojaei MF, Ansari R, Mohammadi V, Rouhi H. 后失稳梁的非线性振动分析。Arch Appl Mech 2014:421–40.

# 功能梯度石墨烯增强多孔梁的概率稳定性分析

Kang Gao¹, Da Chen²,⁴, Jie Yang³ and Sritwat Kitipornchai⁴
¹中国南京东南大学土木工程学院，南京宁
²澳大利亚墨尔本大学基础设施工程系，墨尔本，VIC
³澳大利亚皇家米特理工大学工程学院，Bundoora，VIC
⁴澳大利亚昆士兰大学土木工程学院，圣 卢西亚，QLD

## 7.1 引言

功能梯度多孔纳米复合材料是一类新型复合材料，通过将碳纳米填充物（如碳纳米管、纤维和石墨烯片 GPLs）与具有特定分布的开孔泡沫或闭孔泡沫混合制成[1]。与传统材料相比，纳米增强多孔复合材料具有高强度重量比、卓越的能量吸收能力和优越的物理性能，特别是具有较高表面积和良好分散能力的基于 GPL 的纳米复合材料[2]。功能梯度石墨烯增强（FGGR）聚合物在航空航天、土木、生物医学、国防和汽车领域的巨大潜力了学术界和工业界的广泛关注。

功能梯度（FG）多孔结构（如梁[3]、板[4]、壳[4]和拱[5]）的弯曲、失稳、振动动力学分析得到了全面研究。Chen等[6] 研究了 FG 多孔梁的自由振动和强制振动，发现对称的 FG 孔隙率分布具有最佳机械性能。Gao等[7] 对不完美的 FG 金属梁进行了非线性动力学分析。Chen等[8] 还利用切比雪夫-Ritz 方法对 FG 多孔板展示了弯曲分析。Zhao等[9] 分析了具有均匀弹性边界条件的 FG 多孔矩形板的自由振动。Gao等[10] 针对受到均匀分布谐波载荷的 FG 多孔材料圆壳的主谐振分析提出了一种分析方法。利用有限元方法进行了 FG 圆的自由振动研究[11]。作为先驱，Kitipornchai及其同事[12] 提出了 FGGR聚合物，为多孔材料注入了新能量并促进了纳米增强材料的发展。Chen等[13] 将 Ritz 方法应用于不同孔隙率和增强分布的 FG 多孔纳米复合梁的非线性振动和后失稳分析；Yang等[14] 在一阶剪切变形框架下研究了 FG GPL 增强板的单轴、双轴和剪切失稳载荷。

复合复合结构的机器学习辅助分析、设计与增材制造
DOI: https://doi.org/10.1016/B978-0-12-82145-5-0
Copyright © 2023 Elsevier Ltd. 版权所有。

然而，FGGR 材料的振动和失稳已由 Dong等[15] 结合旋转运动进行了研究。不确定性、制造误差和 FGGR 材料的随机性会损害结构的安全性。文献尚未研究随机参数的影响。在本文中，在该基础上实施了非交换模型（CMM）。通过这种方法，解析解可以被求解并转化为系统。

## 7.2 功能梯度增强梁的材料属性

如图 7.1 所示，梁由 FGGR 材料制成，长度分别为 L，宽度和厚度 h。四种孔隙分布 T1、T2、T3 和 T4 由其他四种增强模式 P1、P2、P3 和 P4 增强，共 16 种情况。

FGGR 梁的分布函数由公式 (7.1) 给出弹性模量 $E(z)$、剪切模量 $G(z)$ 和质量密度 $\rho(z)$：

$E(z) = E_{max}[1 - e_E\psi(z)]$
$G(z) = G_{max}[1 - e_G\psi(z)]$
$\rho(z) = \rho_{max}[1 - e_\rho\psi(z)]$ (7.1)

其中

$\varphi(z) = \begin{array}{cc}\cos^2\frac{\pi z}{h} & T1\\cos^2\frac{\pi z}{2h}-\frac{\pi}{4} & T2\\sin^2\frac{\pi z}{h} & T3\\ & T4\end{array}$ (7.2)

$\alpha$ 是随机幂因子，考虑了孔隙率分布和 GPL 增强模式中的不确定性，如图 7.2 所示。当 $\alpha=1$ 时，模型简化为传统模型。梁的剪切模量为 $G(z)=E(z)[2(1+\nu(z))]$,$\nu(z)$ 是来自闭孔高斯随机场的泊松比，其表达式为：

$\nu(z) = 0.221[1-\frac{\rho(z)}{\rho_{max}}] + \nu_{max}[(1-\frac{\rho(z)}{\rho_{max}})^2+1.21\frac{\rho(z)}{\rho_{max}}-0.21]$ (7.3)

以及 $v_{max}$ 是多孔纳米复合材料的有效泊松比。

