

## 关于《利用可解释机器学习预测高温形状记忆合金窄热滞回行为》一文的勘误 [Mater. Today Commun. 35 (2023) 105806]

Ronald Machaka<sup>a,*</sup>, Precious M. Radingoana<sup>b</sup>

<sup>a</sup> 独立研究员，澳大利亚新南威尔士州纽卡斯尔汉密尔顿 2303  
<sup>b</sup> 南非比勒陀利亚 0001 邮政信箱 395 号，科学与工业研究理事会制造集群先进材料制造部

作者对本文在线发布前，在校对过程中一些信息未被注意到表示遗憾。经慎重考虑，我们决定对本文进行本勘误。式(1)的更正表达式如下：

**修订1：[式(1)]和[式(2)]中的排版错误：**

$$R^2 = 1 - \sum_{i=1}^{n}\frac{(y_i-\hat{y}_i)^2}{(y_i-\bar{y})^2}$$  
(1)

式(2)的更正表达式如下：

$$RMSE = \sqrt{\frac{\sum_{i=1}^{n}(y_i-\hat{y}_i)^2}{n}}$$  
(2)

其中 $y_i$ 是数据集目标值，$\hat{y}_i$ 代表其对应的预测值，$\bar{y}$ 是 $n$ 个数据集条目的目标描述符的平均值。

**修订2：** [表3]的标题标注有误。[表3]中两种Ti–Ni–Cu合金被错误地表示为“Ti–47.5N–2.5Cu”和“Ti–42.5N–7.5Cu”，而它们应分别为“Ti–47.5Ni–2.5Cu”和“Ti–42.5Ni–7.5Cu”。

[表3]已更正如下：

**修订3：[表A1]中的排版错误：** [表A1]中的特征描述列已修订。[表A1]已更正如下：

**修订4：通讯作者的新电子邮件地址：** 通讯作者（Ronald Machaka）的新电子邮件地址如下：ron[dot]machaka@gmail.com。

这些更改均不影响本文已发表论文的原始内容、方法、结果解释或结论。作者对由此造成的任何不便深表歉意。

**表3**  
*TiNiCu合金的实验测量和机器学习预测的ΔT<sub>H</sub>行为。*

| 合金 [参考文献]（at%） | 实验测量的ΔT<sub>H</sub> [参考文献] | 机器学习预测的ΔT<sub>H</sub> [本研究] |
|---|---:|---:|
| (Ti<sub>50−x</sub>Ni<sub>50−y</sub>Cu<sub>y</sub>) 合金体系 | | |
| Ti–50Ni | 33.20 {2.3} [38,42,45] | 34.315 (6.6) |
| Ti–47.5Ni–2.5Cu | 35.60 [42] | 34.963 (1.8) |
| Ti–45.0Ni–5.0Cu | 23.00 [36,42] | 21.724 (5.5) |
| Ti–42.5Ni–7.5Cu | 19.90 [42] | 19.692 (1.0) |
| (Ti<sub>50−x</sub>Zr<sub>x</sub>)(Ni<sub>50−y</sub>Cu<sub>y</sub>) 体系 | | |
| Ti–50Ni–15Zr | 44.80 [44] | 44.41 (0.9) |
| Ti–47Ni–15Zr–3Cu | 58.80 [44] | 57.10 (2.89) |
| Ti–45Ni–15Zr–5Cu | 55.00 [44] | 52.94 (3.7) |
| Ti–40Ni–15Zr–10Cu | 52.40 [44] | 54.02 (3.2) |
| Ti–35Ni–15Zr–15Cu | 57.00 [44] | 56.70 (0.5) |

**注：** []括号中的数值指向引用的参考文献。{}括号中的数值表示估计平均值时的误差。()括号中的数值表示预测值与真实值或实验测量值之间的百分比误差。

### 表A1

输入特征描述和特征选择结果。降维。

| 模型特征 | 特征描述 | SFBS | SFFS | Purposeful |
|---|---|---:|---:|---:|
| *Ti_Content* | Ti含量（at%） |  |  | X |
| *Ni_Content* | Ni含量（at%） | X | X | X |
| *Pd_Content* | Pd含量（at%） | X | X | X |
| *Pt_Content* | Pt含量（at%） |  | X | X |
| *V_Content* | V含量（at%） | X | X | X |
| *Hf_Content* | Hf含量（at%） |  |  | X |
| *Zr_Content* | Zr含量（at%） | X | X | X |
| *Cu_Content* | Cu含量（at%） |  | X | X |
| *Co_Content* | Co含量（at%） |  |  | X |
| *Num_Elem* | 多组分合金中的元素数量 |  |  |  |
| *SolTreat_T* | 合成后的热处理时间和温度条件 | X |  |  |
| *SolTreat_t* | 合成后的热处理时间和温度条件 |  |  |  |
| *dS_conf* | 多组分合金体系中混合的构型熵 | X | X |  |
| *R_ave* | 按混合法则估算的平均原子半径 |  |  |  |
| *dH_mix* | 多组分合金体系中的混合焓 |  |  |  |
| *Tm* | 按混合法则估算的熔化温度 |  |  |  |
| *X* | 元素间Pauling电负性的失配 |  |  |  |
| *VEC* | 价电子浓度 | X |  |  |
| *D_rom* | 按混合法则估算的合金密度 |  |  |  |
| *Omega, Ω* | 热力学描述符的组合（= Tm·dS_conf/dH_mix）[28]。 |  |  |  |
| *Delta, δ* | 元素原子尺寸之间的失配 |  | X |  |
| *std_dH_mix* | 与等原子dH_mix的偏差 |  | X |  |
| *std_dS_conf* | 与等原子dS_conf的偏差 |  |  |  |
| *std_Tm* | 与等原子Tm的偏差 |  |  |  |
| *std_X* | 与等原子X的偏差 | X |  |  |
| *std_VEC* | 与等原子VEC的偏差 |  | X |  |
| *A, λ* | 固溶体稳定性参数（=dS_conf/δ²）[27]。 | X | X |  |
| *dG_mix* | 混合吉布斯自由能 | X |  |  |
| *dT, ΔT_H* | 热滞回目标响应特征 | — | — | — |
| **性能** |  | **91.3%** | **88.9%** | **89.4%**

### 参考文献

[27] D.J. King, S.C. Middleburgh, A.G. McGregor, M.B. Cortie, Predicting the formation and stability of single phase high-entropy alloys, Acta Mater. 104 (2016) 172–179, https://doi.org/10.1016/j.actamat.2015.11.040.

[28] X. Yang, Y. Zhang, Prediction of high-entropy stabilized solid-solution in multi-component alloys, Mater. Chem. Phys. 132 (2012) 233–238, https://doi.org/10.1016/j.matchemphys.2011.11.021.

[36] X. Yang, L. Ma, J. Shang, Martensitic transformation of Ti50(Ni50−xCux) and Ni50(Ti50−xZrx) shape-memory alloys, Sci. Rep. 9 (2019), 3221, https://doi.org/10.1038/s41598-019-40100-z.

[38] R. Dutta, L. Chen, D. Renshaw, D. Liang, Artificial intelligence automates the characterization of reversibly actuating planar-flow-casted NiTi shape memory alloy foil, PLoS One 17 (2022), e0275485, https://doi.org/10.1371/journal.pone.0275485.

[42] J. Frenzel, A. Wieczorek, I. Opahle, B. Maaß, R. Drautz, G. Eggeler, On the effect of alloy composition on martensite start temperatures and latent heats in Ni–Ti-based shape memory alloys, Acta Mater. 90 (2015) 213–231, https://doi.org/10.1016/j.actamat.2015.02.054.

[44] W.C. Kim, Y.J. Kim, J.S. Kim, Y.S. Kim, M.Y. Na, W.T. Kim, D.H. Kim, Correlation between the thermal and superelastic behavior of Ni50-xTi35Zr15Cux shape memory alloys, Intermetallics 107 (2019) 24–33, https://doi.org/10.1016/j.intermet.2019.01.005.

[45] M.H. Elahinia, M. Hashemi, M. Tabesh, S.B. Bhaduri, Manufacturing and processing of NiTi implants: a review, Prog. Mater. Sci. 57 (2012) 911–946, https://doi.org/10.1016/j.pmatsci.2011.11.001.

