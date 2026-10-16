
[76] Chambless L E，Folsom A R，Clegg L X，Sharrett A R，Shahar E，Nieto F J，Rosamond W D 和 Evans G 2000 颈动脉壁厚度预测事件性卒中：Atherosclerosis Risk in Communities (ARIC)研究 *Am. J. Epidemiol.* [151] [478–87](http://dx.doi.org/10.1093/oxfordjournals.aje.a010233)

[77] O’Leary D H，Polak J F，Kronmal R A，Manolio T A，Burke G L 和 Wolfson S K Jr 1999 颈动脉内膜和内襟厚度作为老年人心肌梗死和卒中的风险因子 *New Engl. J. Med.* [340] [14–22](http://dx.doi.org/10.1056/NEJM199901073400103)

[78] Kuppili V，Biswas M，Sreekumar A，Suri H S，Saba L，Edla D R，Marinhoe R T，Sanches J M 和 Suri J S 2017 用于脂肪肝疾病风险分层的超声组织特征化的极速学习框架 *J. Med. Syst.* [41] [152](http://dx.doi.org/10.1007/s10916-017-0797-1)

[79] Molinari F，Acharya U R，Saba L，Nicolaides A 和 Suri J S 2014 通过组合水平集分割和注册，验证颈动脉超声中远壁亮度作为特征的 IMT 测量假设 *Multi-Modality Atherosclerosis Imaging and Diagnosis* (Berlin: Springer) 第 255-67 页

[80] Molinari F 和 Suri J S 2011 颈动脉内膜-内襟厚度的自动测量 *Ultrasound and Carotid Bifurcation Atherosclerosis* (Berlin: Springer) 第 177-92 页

[81] Ikeda N，Dey N，Sharma A，Gupta A，Bose S，Acharjee S，Shafique S，Cuadrado-Godia E，Araki T 和 Saba L 2017 使用多台扫描仪的颈动脉超声中薄/厚斑块及存在球形结节的自动分段 IMT 测量：中风风险评估 *Comput. Methods Programs Biomed.* [141] [73–81](http://dx.doi.org/10.1016/j.cmpb.2017.01.009)

[82] El-Baz A 和 Suri J S 2019 *Big Data in Multimodal Medical Imaging* (Boca Raton, FL: CRC Press)

[83] Sinha G 和 Suri J S 2020 认知科学、信息学和建模的介绍 *Cognitive Informatics, Computer Modelling, and Cognitive Science* (Amsterdam: Elsevier) 第 1-12 页

[84] Biswas M *et al* 2020 两阶段人工智能模型，用于颈动脉超声中动脉壁厚度和斑块负荷的联合测量：心血管/中风风险评估的筛查工具 *Comput. Biol. Med.* [123] [103847](http://dx.doi.org/10.1016/j.compbiomed.2020.103847)

# IOP Publishing

## Multimodality Imaging, Volume 1

### Deep learning applications

#### Mainak Biswas and Jasjit S Suri

## Chapter 8

### Stenosis measurement from ultrasound carotid artery images in the deep learning paradigm

#### Mainak Biswas and Jasjit S Suri

[中风](https://wiki.example.org/feynmans_learning_method)每年影响全球 1500 万人，导致 500 万人死亡，另外 500 万人因残疾而生活。包括颈动脉评估在内的预防措施，可制定有效的治疗方案，从而挽救全球大量生命。然而，这类临床评估具有侵入性、成本高昂且风险大。因此，非侵入性方法，例如超声（US），更受青睐。近年来，机器学习（ML）和深度学习（DL）等人工智能范式已用于图像特征分析。这些工具已用于鉴别疾病，并从不同成像模态中分割受影响区域。本章提出一种新的 DL 模型，用于从颈部超声（US）扫描中测量狭窄。使用三位放射学家制定的三套基准真值（GTs）训练了三个 DL 网络实例。基准真值是手动标注超声扫描中血管内膜–内皮（LI）和血管壁–外膜（MA）的边界。每个训练好的 DL 网络从原始颈部扫描中划定边界，并测量狭窄。实验中，收集了来自颈部两侧的 407 幅超声扫描，涉及 204 名患者（一侧扫描缺失）。三套数据的血管腔径平均误差偏差分别为 0.19 ±inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn106.gif"/ 0.27 mm（*p* < 0.001)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn107.gif"/ 0.23 ±inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn108.gif"/ 0.23 mm（*p* < 0.001)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn109.gif"/ 0.21 ±inline-graphic style="height:0.8125em;" xlink:href="bk978-0-7503-2244-7ch8ieqn110.gif"/ 0.19 mm（*p* < 0.001)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn111.gif"/，分别为 0.19 mm（*p* < 0.001)inline-graphic style="height:1.1875em;" xlink:href="bk978-0-7503-2244-7ch8ieqn111.gif"/。

训练得到的三个 DL 系统的业绩指标（精度）分别为 GT1、GT2、GT3 的 96.7%、96.1% 和 96.4%。对应的曲线下面积（AUC）分别为 0.90、0.94 和 0.86。DL 网络在提供稳定、可靠的 SSI（狭窄指数）计算方面表现更好。

### 8.1 介绍

每年全球约有 1500 万人受中风影响，导致 500 万人死亡，另有 500 万人因残疾而生活 \[1\]。

美国每年约有 795 000 人中风，平均每 40 秒就有一名美国人中风。这导致直接经济成本约 330 亿美元，间接成本约 206 亿美元 \[2\]。

中风的主要原因之一是狭窄，即脑部血管的狭窄。狭窄是由于颈动脉壁内斑块的积聚引起的，如图 8.1 所示。斑块形成的主要原因是一种称为动脉粥样硬化的炎症性疾病 \[3, 4\]。动脉粥样硬化导致上皮功能失调，进而引起单核细胞、巨噬细胞以及脂肪和其他脂质在动脉壁内的积聚。随着时间的推移，斑块逐渐增大，形成含有坏死核心和薄纤维盖的结构。最终纤维盖破裂，导致血栓形成、血流阻塞，进而引发中风 \[5, 6\]。

动脉粥样硬化的多种原因中，遗传因素居首 \[7–9\]，年龄居次 \[10, 11\]，肥胖 \[12\]，饮食 \[13\]，吸烟 \[14\]，糖尿病 \[15\]，酒精消费、体育锻炼不足 \[16\]，高血压 \[17\]，空气污染 \[18\] 等。

![Figure 8.1. The anatomy of the common carotid artery and the stenosis caused by plaque development. (Image courtesy of AtheroPoint™, Roseville, CA. Reproduced with permission from \[66\].)](images/bk978-0-7503-2244-7ch8f1_online.jpg)

**Figure 8.1.** 颈动脉的解剖结构及由斑块发展引起的狭窄。（图片提供方：AtheroPoint™，Roseville, CA。经授权复制自 \[66\]。）

多种成像模态可用于颈动脉成像，包括超声（US）\[19\]、磁共振成像（MRI）\[20\]、计算机断层扫描（CT）\[21, 22\]。

虽然 MRI 能够捕获软组织信息，但存在几个缺点，如机器舱体尺寸大，且对体内金属异物（如起搏器）患者的扫描受限 \[23\]。

CT 会产生非离子辐射，对组织有害，甚至可能导致癌症，因此应避免使用 \[23\]。

在此情境下，超声提供了无辐射、成本低、非侵入且便携的颈动脉成像工具 \[24–26\]。

超声成像主要分为彩色多普勒成像和 B 模式成像。多普勒成像测量血压和血流，用于诊断血栓和血管阻塞等问题 \[26\]。

多普勒成像的缺点包括对血流速度、动脉壁弹性的依赖，以及因流体与血管壁阻抗不匹配而导致的分辨率低下 \[27–32\]。

B 模式超声根据组织的声阻抗生成二维图像。由于采用了谐波成像和复合成像，B 模式超声图像的分辨率非常高，因此相比多普勒成像，B 模式更受青睐，因为不同组织具有独特的声阻抗，成像更清晰 \[33, 34\]。

在颈动脉成像自动诊断领域进行了多项工作。其中大多数是关于颈动脉的识别和血管腔径（LD）的量化（[35, 36）以及内膜-中膜复合体（37, 38），以及基于组织形态的特征描述（39, 40）等。一些研究还将颈动脉斑块负荷与踝臂指数（41）、糖化血红蛋白（42）和冠心病风险评分（43）之间的关系联系起来。本研究提出采用基于深度学习的机制，实现（a）远近血管-内膜边界的划分，（b）狭窄的测量，以及（c）风险特征的评估。狭窄按照 NASCAT 标准（44–46）进行测量。

以往在颈动脉腔径特征化和管理方面已有多项工作（47, 48）。大多数研究遵循相似的路径。基于图像纹理、亮度和对比度的特征被收集用于腔径计算，并据此进行狭窄测量。然而，这些特征挖掘算法是手工构建的，无法在所有场景下通用。此外，颈动脉扫描可能包含噪声，导致结果出现偏差。上述腔径和狭窄测量方法缺乏智能化方案。任何智能方案都需要记忆和学习，这涉及训练和测试。过去十年深度学习（DL）在医学影像领域获得青睐，DL 在医学图像的特征描述和分割方面提供了显著提升。DL 模型不同于传统模型，能够同时完成内部特征挖掘和特征描述。DL 由多层模拟大脑的神经网络组成，能够学习图案内部的复杂关系。因此，本文提出一种基于深度学习的腔径识别和狭窄测量方案。狭窄测量的 DL 模型包含四个阶段：第一阶段对颈动脉扫描进行裁剪，去除非组织区域并进行尺寸降低以加快处理；第二阶段使用全卷积网络（FCN）进行腔径特征化（49）；第三阶段从特征化结果中提取远近 LI 边界并上采样回原始尺寸；第四阶段进行风险分析和性能估计。整体流程如图 8.2 所示。

![Figure 8.2. Pre-processing, lumen identification, LI near/far border mining system, stenosis measurement system, and performance evaluation comprise the global DL system. Reproduced with permission from \[66\].](images/bk978-0-7503-2244-7ch8f2_online.jpg)

**Figure 8.2.** Pre-processing, lumen identification, LI near/far border mining system, stenosis measurement system, and performance evaluation comprise the global DL system. Reproduced with permission from \[66\]。

本文其余部分的组织方式如下。第 8.2 和第 8.3 节分别提供患者人口学信息和方法；第 8.4、第 8.5 和第 8.6 节提供结果、统计分析和讨论；最后在第 8.7 节得出结论。

### 8.2 患者人口学信息和图像采集

本实验共纳入 204 名患者，其中男性 157 人，女性 47 人。所有患者的平均年龄为 69 ± 11 岁。收集了 407 幅 B‑mode 超声图像，用于右、左颈动脉（右颈动脉扫描不可用）。经 Toho 大学伦理委员会批准数据收集，且在采集前已取得所有患者的知情同意。患者的其他详细信息见表 8.1。其中 92 名患者吸烟，93 名患者使用他汀，84 名患者有肾素-血管紧张素系统异常。使用的设备为 Toshiba Inc. 的 Aplio XV、Aplio KG、Xario 扫描仪，探头频率为 7.5 MHz，用于检查左、右颈动脉。扫描由经验丰富的超声技师（15 年经验）完成。平均像素分辨率为 0.05 ± 0.01 mm/像素。

**Table 8.1.** 患者人口学详情。（Reproduced with permission from \[66\].）

| 参数 | 值 |
| --- | --- |
| 性别（男性） | 77.0% |
| 平均年龄 | 69 ± 11 年 |
| 低密度脂蛋白胆固醇 | 99.80 ± 31.30 mg dl^(–1) |
| 高密度脂蛋白胆固醇 | 50.40 ± 15.40 mg dl^(–1) |
| 总胆固醇 | 174.6 ± 37.7 mg dl^(–1) |
| HbA1c | 5.8 ± 1.0 mg dl^(–1) |
| Cr | 1.6 ± 2.1 mg dl^(–1) |
| CKD 期 | 3.1 ± 0.9 |
| eGFR | 45.4% |
| 心血管疾病病史 (%) | 12.1% |
| 吸烟者 | 45.1% |
| 总患者中出现脂质异常的比例 | 57.3% |
| 总患者中使用他汀的比例 | 45.6% |

### 8.3 方法论

为追踪颈动脉壁，三位放射科医师使用了 ImgTracer™，这是一款用户友好的软件（50）。追踪在靠近边界的 15–25 个端点上进行，并贯穿整个颈动脉。为更好地可视化，ImgTracer™ 提供缩放功能。输出为一组（*x*, *y*）坐标点的边界数组。下面我们介绍本文的 AI 方法学，如图 8.2 所示。本研究的方法分为三个阶段——第一阶段：多尺度；第二阶段：腔径检测；第三阶段：LI 与 MA 边界划分；第四阶段：狭窄估计与预后。整体系统如图 8.3 所示，局部系统如图 8.4 所示。在多尺度阶段（51, 52）输入图像会先进行非组织区域去除的预处理。预处理包括四个步骤：图像裁剪、二值化、降噪（去除）以及下采样。裁剪任务用于去除除组织区域外的所有背景信息。二值化将追踪边界图转换为二值基准真。组织信息的左、右边缘因探头形状而出现噪声，探头中心提供最佳分辨率。因此，第三步在每侧去除 10% 的组织进行降噪。最后一步对每幅图像进行 50% 的下采样，以加快计算。

![Figure 8.3. Stenosis estimation global model.](img/bk978-0-7503-2244-7ch8f3_online.jpg)

**Figure 8.3.** Stenosis estimation global model.

![Figure 8.4. The training and testing paradigm of the DL based stenosis measurement model. (Reproduced with permission from \[66\].)](images/bk978-0-7503-2244-7ch8f4_online.jpg)

**Figure 8.4.** The training and testing paradigm of the DL based stenosis measurement model. (Reproduced with permission from \[66\].)
