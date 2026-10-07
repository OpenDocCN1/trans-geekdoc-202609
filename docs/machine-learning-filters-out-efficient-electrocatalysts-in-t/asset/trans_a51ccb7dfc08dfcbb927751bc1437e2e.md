

# 应用催化 B: 环境 339 (2023) 1231228

ScienceDirect 上的可用目录列表

# 应用催化 B: 环境

期刊主页：https://www.elsevier.com/apcatb

# 机器学习在燃料电池大规模三元合金空间中筛选电催化剂

Youngtake Parkᵃᵇᶜᵈᵉ, Chang-Kyu Hwangᵇᶜᵈᵉ,¹, Kihoon Bang⁵e, Doosun Hong⁶f, Hyobin Nam⁷g,
Sooncho Kwon⁸i, Chul Ch Yeol⁸h, Jiwan An⁹, Byeong-Kwon Ju¹⁰,
Sang Han Kim¹¹, Ji Young Joon¹¹, Seung Yong Lee¹², Min Kim¹³³, Donghun Kim¹⁴,
Sang Soo Han*, Hyuck Lee Mo*

ᵃ 韩国科学技术研究院 (KIST) 材料科学与工程中心, 291 Daehak-ro, Useong-gu, 34141, Republic of Korea（大韩）
ᵇ 韩国能源研究院 氢研究部门, 152 Gyeongju-ro, Useong-gu, 34129, Republic of Korea（大韩）
ᶜ 韩国科学技术研究院 (KIST) 材料研究中心, 5 Hwarang-14-geil, Seongbuk-gu, 02792, Republic of Korea（大韩）
ᵈ 韩国科学技术研究院 (KIST) 催化研究中心, 5 Hwarang-14-geil, Seongbuk-gu, 02792, Republic of Korea（大韩）
e 韩国科学技术研究院 (KIST) 计算科学研究中心, 5 Hwarang-14-geil, Seongbuk-gu, 02792, Republic of Korea（大韩）
프 加利福尼亚大学帕萨迪纳分校 材料与工艺模拟中心 (MSC), CA
⁷ 加州大学伯克利分校 化学工程系, 94720, USA（美国）
⁸ 韩国技术大学 (NST) 纳米生物工程中心部门, Daejeon, 232 Now, Yuseon-gu, 01811, Republic of Korea（大韩）
⁹ 韩国浦项科学技术大学 (POSTECH) 机械工程系, Cheonghang-ro, 77, Pohang-si, Gyeongsbuk-do 37063, Republic of Korea（大韩）
¹⁰ 韩国科学技术研究院 (KIST) 新兴材料研究中心, 5 Hwarang-14-geil, Seongbuk-gu, 02792, Republic of Korea（大韩）
¹¹ KIST-技术转换部门, Kyung Hee Lee, 02447, Republic of Korea（大韩）

# 文章信息

- 燃料电池
- 电催化剂
- 三元合金
- 机器学习
- 催化剂设计设计方案

# 摘要

尽管多组分材料具有潜力，但由于成分极其复杂，它们一直未被积极视为催化剂。然而，针对燃料电池电催化剂，我们提出了一种由机器学习（ML）驱动的催化剂筛选方案，以识别结构稳定性、选择性、性能和成本效益的结构。我们通过燃料电池每个阴极和阳极的三种测试材料，在合金核心壳结构{X(Y)Z}Fe中从30种元素中测试了17个候选者。这些候选者比铂膜更具稳定性、成本更低且性能更高。作为最终候选者之一的CuAuPt性能优于铂膜，电流密度增加了约2倍，而铂用量减少了2.7倍。这一证明表明，我们的机器学习驱动策略对于探索多组分系统和催化剂设计非常有用。

# 1. 引言

铂（Pt）是一种极其稀缺且昂贵的元素，是燃料电池中不可或缺的成分。十年来，人们付出了大量努力开发与[1–4]具有相当催化活性的廉价催化剂；然而，其他材料要么铂含量低，要么仅仅是铂基材料[5–9]。

对于发生氧还原反应（ORR）的阴极，铂（带有铂皮）是目前的领先水平；对于发生氢反应（HOR）的阳极，由于镍的高活性，使用镍可以避免严重的CO问题，但其耐用性不利[10]。在不牺牲性能的情况下，很难为阴极和阳极找到新型且低成本的材料。

> * 通讯作者：韩国科学技术研究院 (KIST) 材料研究中心, 5 Hwarang-14-geil, Seongbuk-gu, 02792, Republic of Korea（大韩）。
> ** 通讯作者。
* 电子邮箱：jongminkim@kist.re.kr (J.M. Kim), donghun@kist.re.kr (D. Kim), sangsooo@kist.re.kr (S.S. Han), hmlee@kaist.ac.kr (H.M. Lee)。
* 作者贡献同等。

https://doi.org/10.1016/j.apcat.2023.1231228
2023年4月7日收到；2023年7月1日修订；2023年7月22日接受
在线可用：2023年7月24日

0926-3373/2023 Elsevier B.V. 版权所有。

使用卓越催化剂策略[11]进行金属合金化可以显著改变金属的电子结构，从而改变其催化性质。然而，燃料电池中的合金局限于双金属情况。在各种实验中，其性质与纯金属不同。我们关注用于阴极的铂皮（Pt$_X$Y$_Z$），这已被广泛探索。我们基于机器学习的筛选方案识别了10个用于ORR的候选者，具有更高的性能和更低的成本。

# 2. 实验部分

## 2.1. DFT吸附

尽管取得了这些成就，铂基合金未能完全解决燃料电池中的问题。在更广泛的空间尺度上，三元合金出现了[18–22]。在本研究中，我们关注Pt-$_X$Y$_Z$相互作用的效率。使用以下方程计算吸附能：

$\Delta E_{ads} = \Delta E_{ads} - \Delta E_{slab} + \Delta E_{gas}$

其中$\Delta E$表示系统的总能量。所有气种（包括$H_2O$和CO）的吸附能均相对于表面[29]。

自由能在标准条件下（pH = 0, 298 K; P = 1 atm，电位 U = 0）下计算。我们计算了溶剂质子和电子（H$^+$）的自由能，这些能量与气体的水化平衡（相位0.5 h）。热力学自由能定义为$\Delta E_{ads}$，其中$\Delta E_{ads}$表示吸附质吸附的自由能修正。溶液效应使用从显式水模型获得的常数（0.5 eV; U = 0.25 eV）来考虑。

在这项工作中，我们提出了一种基于机器学习的催化剂设计方案，用于在燃料电池三元合金空间中筛选出高效且低成本的材料。在三元空间中的许多结构性质中，本研究关注的是传统的合金金属壳（X,Y,Z）与铂可能不同的性质[48]。基于在DFT水平获得的约十个吸附能值的筛选方案，进行了一个完全的机器学习筛选过程，其标准包括结构稳定性（热力学和

