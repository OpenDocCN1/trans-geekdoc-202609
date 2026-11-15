

下降至少 1.7 分即可被患者主观感知为“感觉好转”。²² 我们将治疗反应计算为从基线到治疗后立即的最后一次测量的 PHQ-9 分数变化，记为 PHQ-9 变化；我们未关注 iCBT 后 3 个月进行的自动随访。如果患者在仅提供一次测量后终止治疗，则为该患者分配 PHQ-9 变化为 0（iCBT 项目需要症状报告；fCBT 治疗师仅被建议鼓励患者报告）。这种保守方法相比于完全数据或插值分析，实际上惩罚了辍学率较高的治疗。

## 统计分析

fCBT 和 iCBT 注册表均记录了总体焦虑严重程度和损害量表分数，使我们能够使用该连续值分数作为结局的基线预测因子。²³ 其他预测变量来自多个关联的行政登记表（图 2B）。出于隐私和方差减小的考虑，我们仅纳入与治疗分配交叉分组时单元格大小为 10 例及以上的分类协变量。

我们通过从登记表中选取所有合格患者来确定样本。我们的目标是估计 fCBT 与引导式 iCBT 之间的 ATE。一个 95% CI 不超过 1.7 个 PHQ-9 点的估计可被视为准确，因为它低于此前估计的“感觉好转”与“感觉与治疗前相同”之间的检测阈值。²²

对于 TMLE，我们实现了带有广泛基础学习器集的超级学习器（Philips 及其同事文章中的示例 6 和 7⁴），包括广义线性模型、贝叶斯广义线性模型、广义加性模型、lasso、弹性网和岭回归、多项式样条、多元回归样条、极端梯度提升、贝叶斯加性回归树以及高度自适应 lasso。²⁴⁻²⁷ TMLE 需要两个超级学习器，一个预测治疗分配，另一个预测治疗结局。³¹⁴ 我们的超级学习器使用交叉验证，通过非负最小二乘回归算法自动为基础学习器分配权重，并保证其渐进性能优于基础学习器。¹⁵,²⁴ 我们使用超级学习器构建 ATE 估计值，并利用 TMLE 优化 ATE 参数的偏差-方差权衡。¹³,²⁶ 因此，TMLE 控制了变量及其机器学习的非线性组合和交互作用造成的混杂。我们遵循了 Philips 及其同事²⁴ 和 van der Laan 及其同事²⁶ 的在线和已发表指南，使用他们的 tlverse R 环境，包括 sl3（版本 1.4.4）、tmle3（版本 0.2.0）和 cvAUC（版本 1.1.4）包。该方法对治疗结局进行嵌套十倍交叉验证，并用于

| | Therapist-guided iCBT (n=5446) | fCBT (n=388) | p value (iCBT vs fCBT) |
|---|---|---|---|
| **Continuous variables** | | | |
| PHQ-9 score at first assessment* | 13.31 (5.34) | 11.57 (5.60) | <0.0001 |
| OASIS score at first assessment | 10.36 (3.68) | 9.97 (3.81) | 0.048 |
| Distinct previous F-diagnoses, count | 1.74 (2.61) | 3.34 (3.92) | <0.0001 |
| Distinct previous non-F-diagnoses, count | 10.21 (9.55) | 15.57 (12.55) | <0.0001 |
| Relatives, patients plus siblings, count | 4.08 (1.91) | 3.78 (1.85) | 0.0024 |
| Maternal F-diagnoses, count | 0.76 (2.29) | 0.94 (2.83) | 0.23 |
| Paternal F-diagnoses, count | 0.62 (2.10) | 0.50 (1.94) | 0.24 |
| Siblings’ F-diagnoses per sibling, count | 0.58 (1.31) | 0.50 (1.28) | 0.27 |
| Distinct purchased medicine (ATC-N) prescriptions, count | 4.53 (4.20) | 5.77 (5.52) | <0.0001 |
| Distinct ATC-N medicine purchase events, count | 26.77 (53.92) | 45.00 (83.54) | <0.0001 |
| Insurance-reimbursed sickness absence days, count | 113.57 (187.58) | 135.64 (196.74) | 0.033 |
| Insurance-reimbursed sickness absence days with F-diagnosis, count | 71.17 (126.89) | 72.80 (137.7) | 0.82 |
| Previous psychiatry visits, count | 16.29 (41.45) | 43.89 (81.63) | <0.0001 |
| Age, years | 34.49 (11.89) | 40.37 (15.57) | <0.0001 |
| **Binary-valued variables** | | | |
| Rehabilitation money received | 25 (<1%) | 12 (3%) | <0.0001 |
| Income support received | 1118 (21%) | 71 (18%) | 0.32 |
| Rehabilitation support received | 860 (16%) | 59 (15%) | 0.82 |
| Rehabilitation psychotherapy received | 502 (9%) | 32 (8%) | 0.58 |
| Gender | .. | .. | 0.070 |
| Male | 1634 (30%) | 99 (26%) | .. |
| Female | 3812 (70%) | 289 (74%) | .. |
| First F-diagnosis for depression | 1982 (36%) | 140 (36%) | 0.95 |
| First F-diagnosis other† | 259 (5%) | 27 (7%) | 0.069 |
| Most frequent F-diagnosis for depression | 2295 (42%) | 185 (48%) | 0.038 |
| Most frequent F-diagnosis other† | 1080 (20%) | 78 (20%) | 0.95 |
| Siblings’ most frequent F-diagnosis for depression | 685 (13%) | 39 (10%) | 0.17 |
| Siblings’ most frequent F-diagnosis other‡ | 1447 (27%) | 103 (27%) | 1.00 |
| Siblings’ most frequent F-diagnosis for psychotic disorder | 149 (3%) | 12 (3%) | 0.80 |
| Mother’s most frequent F-diagnosis for depression | 469 (9%) | 37 (10%) | 0.60 |
| Mother’s most frequent F-diagnosis other† | 772 (14%) | 64 (16%) | 0.24 |
| Father’s most frequent F-diagnosis for depression | 281 (5%) | 12 (3%) | 0.093 |
| Father’s most frequent F-diagnosis other† | 702 (13%) | 50 (13%) | 1.00 |
| Most frequently purchased medicine was benzodiazepine | 137 (3%) | 18 (5%) | 0.019 |
| Most frequently purchased medicine was for migraine | 240 (4%) | 10 (3%) | 0.11 |
| Most frequently purchased medicine was non-SSRI for depression | 945 (17%) | 59 (15%) | 0.31 |
| Most frequently purchased medicine was paracetamol | 799 (15%) | 32 (8%) | 0.0006 |
| Most frequently purchased medicine was for psychosis | 178 (3%) | 10 (3%) | 0.55 |
| Most frequently purchased medicine was for sleep problems | 157 (3%) | 22 (6%) | 0.0035 |
| Most frequently purchased medicine was SSRI for depression | 1821 (33%) | 132 (34%) | 0.89 |
| Most frequently purchased medicine was opioid | 461 (8%) | 20 (5%) | 0.028 |
| Entrepreneur | 186 (3%) | 25 (6%) | 0.0032 |
| Upper white-collar employee | 894 (16%) | 58 (15%) | 0.49 |
| Lower white-collar employee | 1774 (33%) | 90 (23%) | <0.0002 |
| Manual labourer | 756 (14%) | 39 (10%) | 0.041 |
| Student | 953 (17%) | 39 (10%) | <0.0002 |
| Retiree | 163 (3%) | 68 (18%) | <0.0001 |
| Unemployed or working status unknown | 461 (8%) | 46 (12%) | 0.028 |
| Native language is Finnish§ | 5092 (93%) | 363 (94%) | 1.00 |

表 1：各治疗组的描述性统计

数据以连续变量的均数（标准差）和二值变量的频数（百分比）表示。iCBT vs fCBT 指组间比较（连续变量的 p 值来自 t 检验，二值变量的 p 值来自 χ² 检验）。症状分数来自治疗登记表，诊断指芬兰健康福利研究所维护的全国护理登记表中的 ICD-10 代码，工作状态来自芬兰统计局，人口统计数据来自数字和人口数据服务局，其他变量来自芬兰社会保障局（Kela）。变量已预处理为适合分析的格式。变量（例如，F 代码）指各自登记表中可用的完整病史（图 2B），但人口统计、症状和工作状态指治疗前最近值。表中的患者与反事实分析中的患者相对应，并排除了 25 名有部分缺失数据的患者（图 2A；变量特异性缺失：性别和年龄 18 例，工作状态 21 例，OASIS 4 例，存在一些重叠）。每当会出现 <10 名患者的类别时，均将其与其他类别合并，以保护患者匿名性并便于统计解释。ATC-N=解剖治疗化学-神经系统。CBT=认知行为疗法。iCBT=互联网提供的 CBT。fCBT=面对面 CBT。OASIS=总体焦虑严重程度和损害量表。PHQ-9=患者健康问卷-9。*仅纳入敏感性分析，因为基线分数与变化分数之间存在人为的统计依赖。#存在测量误差。†其他 F 诊断指不属于抑郁类别的诊断（F32、F33、F34.1；<10 名患者的类别已合并）。‡其他 F 诊断指不属于抑郁或精神病类别的诊断（F32、F33、F34.1、F2、F39；<10 名患者的类别已合并）。§大多数公民，尤其是以芬兰语为母语的公民，属于芬兰民族起源；目前芬兰不允许常规收集种族或民族来源数据。

参见在线附录 2

在调查超级学习器性能时，按提供格式分层的嵌套十倍交叉验证用于治疗分配（在选择-验证超级学习器交叉验证内嵌套训练-验证基础学习器交叉验证；附录 2 第 4 页）。TMLE 估计中使用了非嵌套（训练-选择）交叉验证（目标参数是反事实量，排除了验证样本）。我们使用 superMICE 包（版本 1.1.1；五条链和五次迭代）进行了多重插补。学习器、协变量和插补选择以及核心分析脚本的示例进一步讨论见附录 2（第 2–12 页）。我们使用 χ² 检验比较原始比例，使用 Welch’s t 检验比较均数。标准化均数差效应量以 Hedge’s g 给出，标准化变化效应以 Cohen's（配对）d 效应量给出。作为敏感性分析，我们还计算了 ATE 的 G-计算和 AIPTW 估计，以及一种使用简单模型的 TMLE 版本。¹⁴ 我们使用线性回归作为结局模型，并使用逻辑回归来估计接受 fCBT 而非 iCBT 的概率。采用了先前推荐用于 (A)IPTW 的协变量平衡检查。²⁸ 所有分析均在 Findata 机构的安全 Kapseli 计算环境中进行，使用 R（版本 4.2.2）。

## 资助方的作用

研究的资助方在研究设计、数据收集、数据分析、数据解释或报告撰写中均未发挥任何作用。

## 结果

共评估了 32 343 条登记条目的资格，其中 8417 条来自 FPQR，23 926 条来自 HUS-iCBT 注册表。排除了 FPQR 的 8025 条条目和 HUS-iCBT 注册表的 18 459 条条目，总计 392 名来自 FPQR 的患者形成 fCBT 组，5467 名来自 HUS-iCBT 的患者形成 iCBT 组，用于自然观察分析（图 2A）。25 名患者缺失基线数据，并从主要结局的反事实分析中移除，因此 fCBT 组剩余 388 名患者（99 [26%] 男性和 289 [74%] 女性），iCBT 组剩余 5446 名患者（1634 [30%] 男性和 3812 [70%] 女性）（图 2A）。在我们访问的 40 263 名患者中，有 4 名（<0.01%）反对 Findata 使用其登记数据（当前纳入标准不明；部分被访问的登记表未纳入本研究，但可能包含反对的 4 名患者）。Four (1%) of 392 patients from the fCBT group and 21 (<1%) of 5467 patients from the iCBT group were missing mostly demographic baseline data. Table 1 summarises treatment group characteristics at baseline, after removing these 25 patients (other missingness pertaining to treatment dropout did not affect table 1). The mean age of patients in the final analytic fCBT group was 40 years (SD 16; median 36 years [IQR 28–51]) and 363 (94%) of 388 spoke Finnish as their native language. In the final guided iCBT group, the mean age was 34 years (SD 12; median 31 years [IQR 25–42]) with 5092 (93%) of 5446 speaking Finnish as their native language.
A mean of 9.4 weeks (SD 3.5) passed between baseline and the last follow-up assessment in guided iCBT for those who completed the last session and 7.7 weeks (4.4) for all patients (including patients whose first and last measurements were the same one). We estimated a mean interval of 35 weeks (22.9) between the reported start and end dates of the fCBT therapy period; this estimate was based on less accurate data reported to the outsourcing registry owner (in contrast, the iCBT programme automatically collects and dates data).
In the analytic iCBT group, there was a mean of 5.5 (SD 2.1; median 7.0 [IQR 4.0–7.0]) treatment sessions. In the fCBT group, reporting the number of sessions was not obligatory due to a coupon system that predefined the number of HUS-paid sessions; therefore, these data were only available for 352 (91%) of 388 patients (mean 12.3 [SD 9.8]; median 14.0 [IQR 2.0–20.0]). Of the 5467 people given iCBT, those who finished the treatment by reaching the seventh session (3333 [61%]) reported a mean decline

