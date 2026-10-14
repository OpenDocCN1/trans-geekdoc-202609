
-   [物联网 (IoT)](https://wiki.example.org/feynmans_learning_method) 促进了设备之间的交互和数据分析 (`Sundas et al., 2021`)。因此，护士有可能自动化重要标志记录的过程。IoT 在其分布式平台中采用云计算，用于数据处理和存储 (`Sundas et al., 2022`)。该平台使得能够应用机器学习 (ML) 算法 (`[Gultepe et al., 2013](#ch15.xhtml#ref15_1)`; `Sundas et al., 2022`) 来预测患者健康下降并通过预测未来患者需求来优化医院资源。

本文探讨了医疗物联网 (IoHT)，这是一种新兴技术，能够使互连设备监测患者健康并共享数据。我们建议将机器学习与该架构相结合，以关联数据并预测未来的健康趋势和需求。当信息和通信技术 (ICT) 应用于医疗环境时，它被称为电子健康 (eHealth) 或移动健康 (mHealth) (`[Vistisen et al., 2019](#ch15.xhtml#ref15_6)`)。这些术语都旨在提升患者结果，特别关注移动健康服务和普适健康 (uHealth)。uHealth 利用普遍和移动计算，持续监测个体健康，强调预防性和个性化护理，脱离当前范式 (`Chen et al., 2016`)。

在本文中，我们深入探讨了 IoHT 在医院病房监测生命体征的潜力，并研究了自动化和智能化的方法，以预测患者健康恶化。文章结构分为六个章节。第 2 节讨论医院患者治疗的最新进展。第 3 节介绍 IoHT 概念及医院病房收集生命体征的技术。第 4 节讨论机器学习在数据解释中的应用。第 5 节阐述主要挑战并提供解决方案。第 6 节总结研究。

## II. Hospital treatment focused on the individual patient

Patient-centered care (PCC) 作为医院质量指标的核心 (`[Gultepe et al., 2013](#ch15.xhtml#ref15_1)`)。PCC 的评估依赖于患者需求、医护人员有效沟通以及服务可用性等因素。从信息技术 (IT) 角度看，PCC 等同于患者的电子健康记录 (EHR)。这与过去的各种企业资源规划 (ERP) 系统有显著不同，后者主要旨在优化工作流和流程方面 (`[Bloch et al., 2019](#ch15.xhtml#ref15_9)`)。在 PCC 的语境下，医院病房的生命体征起着关键作用，是识别患者健康问题及其与其他相关数据的关联的重要指标。

### A. Vital signs monitoring

患者中心护理提升了医院治疗效果 (`Tang et al., 2020`)。患者中心护理的评估体现在如何满足患者需求、临床医生快速沟通健康数据以及患者便捷获得治疗。EHRs 是 PCC 医疗信息系统。因此，ERPs 优化工作流 (`Khan et al., 2014`)。

医院病房的生命体征是用于突出患者健康问题的关键指标，且当这些体征与其他数据相连时，可描述 PCC。护士自 1900 年以来一直在测量相同的生命体征 (`Sundas et al., 2021`)。

血压、体温、心率和呼吸率测量血氧饱和度。要有效评估患者状态，国家健康与护理卓越局 (NICE) 建议在监测这五项指标的同时，还需监测氧饱和度。还需考虑尿液输出、不适感以及生化检测。医院规则决定监测哪些体征，这往往引发争议。

Elliott 和 Coventry 建议八项生命体征 (`[Rana et al., 2018](#ch15.xhtml#ref15_17)`)，并增加疼痛、意识和尿液输出 (`Iyer et al., 2022`)。表 15.1 中的定义、正常化和影响指出，医院可监测的八项指标对患者健康产生影响。

[Table 15.1 Typical hospital vitals used for patient monitoring](#ch15.xhtml#R_tab15_1)

| Definition || Vital sign || Some influencing factors || Normal range |
| --- | --- | --- | --- |
| A pain scale is used to measure the patients’ pain intensity || Pain of level || The view from the patient || The patient reports no pain on the 0–10 pain scale (1–3 mild, 4–6 moderate, 7–10 severe) |
| The force multiplied by the period between heartbeats (systole) that blood exerts on arteries || Blood pressure || Variables such as age, posture, effort, sleep, slant, and confounding variables (such as White-Coat-Syndrome or anxiety) || 90/60–120/80 mmHg |
| How many times in 60 seconds the chest moves up and down || Breathing rate || Variables such as age, oxygen levels in the environment, pain and anxiety levels, and physical effort || Breathing rate: 12–1/8/min |
| Estimates the quantity of oxygen in the blood by measuring the saturation level of its peripheral capillaries (SpO[2]) || SPO[2] || Workload, oxygen levels, and other confounding variables (such as activity and pain intensity) || From 95% to 100% |

监测生命体征带来的挑战在于监测频率和报告内容。与 [Table 15.1](#ch15.xhtml#tab15_1) 不同，并非所有体征都能即时获取。

疼痛评估是主观的。WILDA 验证疼痛术语、0–10 量表上的强度、部位、持续时间、加重因素以及缓解变量 (`Sundas et al., 2021`)。患者-照护者 WILDA 方法可能使用电脑记录数据。平板电脑和智能手机可以捕获患者数据用于 EHRs。意识评估需要患者与医护人员的沟通。格拉斯哥昏迷评分 (Glasgow Coma Scale) 测量眼睁开、语言和运动反应 (`[Khan et al., 2021](#ch15.xhtml#ref15_12)`)。这些评估的数值结果取决于患者对刺激的反应。

电子捕获这些数值可帮助评估患者的神经状态。导管可自动记录尿液输出。手动尿量计仍在使用 (`Sundas et al., 2021`)。

### B. Patient risk assessment

医院 PCC 定期监测生命体征，并在出现疑虑时更频繁地进行监测。数据和分级响应技术降低风险。监测与触发定义了检查的频率、内容和时机。[Table 15.2](#ch15.xhtml#tab15_2) 列出了医疗机构评估风险的方法。先检查指标 (`[Liu et al., 2014](#ch15.xhtml#ref15_13)`)。该组采用医疗急救团 (MET)  calling 标准。MET 由气道威胁、呼吸或心脏骤停、状态改变以及抽搐 (`[Singh et al., 2019](#ch15.xhtml#ref15_7)`; `Sundas et al., 2021`) 确定。第 2 组只需一个异常体征。PART (Prehospital Acuity Rating for Triage) calling 要求是一个例子。PART 方法测量呼吸、心率、收缩压、意识、氧饱和度和尿液输出。

[Table 15.2 Methods, frameworks, and systems for assessing risk](#ch15.xhtml#R_tab15_2)

| Common practices || Type || Characteristics |
| --- | --- | --- |
| EWS + MET, MEWS + PART intensity || Combination || Monitoring development, graded response, varying sensitivity and specificity |
| --- | --- | --- |
| Acceptable calling standards || Single parameter || Easy to use, but no improvement tracking |
| PART || Multiple parameter || high sensitivity and low specificity, yet it allows progress tracking and progressive reaction |
| The worthing physiological scoring system (EWS, MEWS, ViEWS) || Aggregate scoring || Allows development monitoring, progressive response, and high sensitivity and specificity, based on the score |

