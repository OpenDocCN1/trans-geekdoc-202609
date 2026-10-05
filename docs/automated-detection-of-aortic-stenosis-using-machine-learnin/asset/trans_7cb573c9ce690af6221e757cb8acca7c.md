

# 期刊预证明 (Journal Pre-proof)

基于机器学习的动脉脉狭窄自动检测

Benjamin S. Wessler, Zhe Huang, Gary Long, Stefano Pacifici, Nishant Prashar, Samuel Karmily, Roman A. Sandler, Joseph Sokol, Daniel B. Sokol, Monica M. Dehn, Luisa Maslon, Eileen May, Ayan R. Patel, Michael C. Hughes

PII: S0894-7317(23)0014-7

DOI: https://doi.org/10.1016/j.echo.2023.01.006

引用：YMJE 5115

即将发表于：美国超声心学会杂志 (Journal of the American Society of Echocardiography)

收稿日期：2022年12月2日

修改日期：2023年1月1日

接收日期：2023年1月3日

> 请引用本文如下：Wessler BS, Huang Z, Long G, Pacifici S, Prashar N, Karmiy S, Sandler RA, Sokol J, Sokol DB, Hahn MM, Maslon L, Mai E, Patel AR, Hughes MC, 基于机器学习的动脉脉狭窄自动检测, Journal of the American Society of Echocardiography (2023), doi: https://doi.org/10.1016/j.echo.2023.01.006。

此文件为接受后经过增强的文章 PDF 文件，增加了封页和元数据，并为了可读性进行了格式处理，它尚不是最终的记录版本。该版本在以最终形式出版之前，将经过额外的文字编辑、排版和审查，但我们提供此版本是为了让文章具有早期可见性。请注意，在制作过程中，可能会发现影响内容的错误，并适用于本期刊的所有法律免责声明。

2023 年由 Elsevier Inc. 代表美国超声心学会出版。

![](img/9e83ae159adbe9802ed604394e924f29_0_0.png)

# 基于机器学习的动脉脉狭窄自动检测

短标题：动脉脉狭窄的自动检测

Benjamin S. Wexler^a, Zhe Huang^b, Gary Long^c, Stefano Pacifici^d, Nishant Prashar^d, Samuel Karmiyd, Roman A. Sandler^d, Joseph Sokol^e, Daniel B. Sokol^e, Monica M. Dehn^a, Luisa Maslon^a, Eileen Mai^a, Ayan R. Patel^b, Michael C. Hughes^b

- a 波士顿 MA，塔夫茨医学中心心血管中心
- b 美国马萨诸塞州梅德福德，塔夫茨大学计算机科学系
- c 马萨诸塞州多彻斯特，CVAI Solutions
- d 波士顿 MA，塔夫茨医学中心，医学科
- e 加利福尼亚州洛杉矶，Cardio.ai

部门与机构：

通讯地址：
Benjamin S. Wexler, MD, MS
塔夫茨心血管中心，
预测分析与比较有效性 (PACE) 中心，
临床研究与健康政策研究学院 (ICRHPS)
塔夫茨医学中心 (TMC)
800 Washington Street, Box 63
Boston, MA 02111
电话：617-633-2273
传真：617-633-0022
邮箱：bwessler@tuftsmedicalcenter.org

## 摘要：

目标：动脉脉狭窄 (AS) 是一种变性瓣膜疾病，目前诊断不足且治疗不足。利用有限的 2D 超声心图检测 AS 可以实现筛查，并改善该疾病的适当转诊和治疗。我们旨在开发从有限成像数据自动检测 AS 的方法。

方法：使用有限的 2D 经胸超声心图 (TTE) 数据对卷积神经网络进行训练、验证和测试。开发的网络用于完成两个顺序任务：1) 视图识别和 2) AS 的疾病级分级。使用平衡准确率和受者工作特征曲线下面积 (AUROC) 作为性能指标。

结果：包含了 577 名患者的标注图像。神经网络在来自 338 名患者的数据（平均 N = 10,253 张标注图像）上进行训练，在 119 名患者上进行验证（平均 N = 3,505 张标注图像），并在 120 名患者的测试集上（平均 N = 3,511 张标注图像）评估性能。实现了 AUROC 为 0.96 的 AS 全自动筛查。网络能以 AUROC = 0.86 区分无显著（无、轻度、轻/中度）AS 与显著（中度或严重）AS，并以 0.75 的 AUROC 区分早期（轻度或轻度/中度 AS）与显著（中度或严重）AS。在 8502 例门诊 TTE 队列中对这些网络的外部验证显示，仅需胸旁长轴成像即可实现 AUROC 为 0.91 的 AS 筛查。

结论：使用现代神经网络利用有限的 2D 数据实现 AS 全自动检测是可行的。这些方法为新型 AS 筛查方法奠定了基础。

**关键词：**动脉脉狭窄，筛查，机器学习，超声心图，经胸超声心图

## 缩写：

- AS = 动脉脉狭窄
- TTE = 经胸超声心图
- ML = 机器学习
- VHD = 瓣膜心脏病
- AVR = 动脉瓣置换
- SSL = 半监督学习
- DICOM = 医学数字影像和通信标准
- PLAX = 胸旁长轴
- PSAX AoV = 胸旁短轴主动脉瓣
- 2：塔夫茨医学中心

## 声明：

利益冲突：BW 曾为 iCardio.ai 提供咨询，没有与本工作相关的商业利益追求。

## 资助：

本工作受 NCATS 资助 UL1TR02544，受 NIH 资助 K23AG05567

## 引言

动脉脉狭窄 (AS) 是一项巨大的公共卫生问题，影响着 1260 万成年人，在全球范围内每年导致估计 10,200 人死亡。7 近期，对 AS 的早期识别引起了兴趣，且证据表明许多患者未得到适当治疗。2,3 这些观察促使我们研究识别 AS 的新型机器学习 (ML) 方法。

传统上，AS 的准确分级依赖于多个平面的结构和血动力学参数的整合。4 从筛查的角度来看，AS 的某些特征（如瓣膜厚度和钙负荷）在 2D 图像上显而易见。虽然深度学习方法在某些医学图像分类任务中已经超过人类5,6，常见的分类器仅以单个图像作为输入，且在超声心图中的应用目前主要关注视图识别、分割以及心脏功能和心肌疾病的评估。7-10 目前 AS 的 ML 方法限于使用超声报告（因此需要专家对图像进行解读才能工作）11,12，或者限于仅关注严重疾病的小样本13。14 尚未研究关注利用有限图像评估 AS 的连续性，以建立适用于筛查的工具。

## 方法

一家大型三级医疗中心（马州波士顿塔夫茨医学中心）。心血管成像中心已获得国际学会认证委员会 (IAC) 认证，并配备了主要供应商（Philips, Toshiba, Siemens）的超声设备。

## 超声图

本工作已获得塔夫茨医学中心伦理委员会 (IRB) 的批准。超声图源于 2011-2020 年间作为常规护理实施的 TTE。通过使用标准的医学数字影像和通信 (DICOM) 图像，这些方法旨在独立于设备。根据是否存在 AS 纳入超声图。未根据图像质量选择图像。排除既往过动脉瓣置换的患者。其他心脏发现，包括其他结构性心脏疾病和心律异常（如房颤）均未排除。

## 图像采集与预处理

图像由经过培训的超声技师采集，方法与现美国超声心学会 (ASE) 指南一致。15。对于本研究，我们使用元数据来识别