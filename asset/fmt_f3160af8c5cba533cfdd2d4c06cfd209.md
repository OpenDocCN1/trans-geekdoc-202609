
4.2.3 特征处理 .....................................71

4.2.4 分类 ..........................................72

4.3 结果与讨论 .......................................73

4.3.1 特征分析 ........................................73

4.3.2 分类分析 ..................................74

4.4 结论 ................................................78

参考文献 .......................................................80

### 4.1 引言

据估计，有 3.34 亿人暴露在空气中的病毒环境中，可能会患上呼吸系统疾病，从而对肺部及呼吸系统的其他器官造成严重损害。肺部是人体的关键器官之一，负责氧气向体内的输送以及二氧化碳的排出，维持我们的健康以及正常的工作和生活能力。多种肺部疾病可能会阻碍身体摄入足够的氧气，并可能对其他器官以及血液循环造成严重损害。肺部疾病可能由气道、肺组织和血管的问题引起。一些肺部疾病或呼吸衰竭可能源于出生，这些疾病被称为慢性肺部疾病 [1]。发生在气道中最常见且最严重的慢性肺部疾病包括哮喘、慢性支气管炎和肺气肿。这些疾病会随时间对肺部造成严重损害。在呼吸过程中，肺组织和肌肉像气球一样帮助肺部扩张。然而，如果组织发炎，肺部可能无法完全扩张，肺部将不得不付出巨大努力将氧气输送到血液中，并将二氧化碳排出体外。

许多其他肺部综合征会影响肺部血管，例如血管瘢痕形成、血栓或炎症 [2]。肺部循环疾病可能会对心脏和大脑的功能造成严重损害，进而导致死亡。许多肺部疾病与气道、肺组织和肺部循环的各种障碍相结合。最常见的肺部疾病包括：支气管肿胀和炎症、慢性阻塞性肺病（COPD）、肺炎、肺癌、动脉阻塞以及肺部异常液体积聚 [2]。这些呼吸系统疾病的检测已通过医疗视频和图像分析工具进行了广泛研究。在众多可用的医疗检查工具中，超声波视频分析在补充肺部功能行为信息以检测现有呼吸系统疾病方面发挥着至关重要的作用。传统肺部疾病诊断过程与现代技术的结合，若能在疾病尚处于轻微阶段时进行检测，可能会产生更大的影响。因此，机器学习可以被定义为医疗领域最具影响力的技术方法。各种机器学习技术为选择最佳方法以评估最佳结果提供了许多机会，因为它们在健康数据分析和评估任务中提供了显著优势。

机器学习算法在医疗系统中的整合，可能会部署许多灵活且可扩展的解决方案，用于对不同类型疾病进行早期诊断的分类和预测，例如医学影像分析、视频分析、声音分析或实验室检查结果。Manogaran 等人 [3] 使用正交伽马分布结合机器学习方法（OGDMLA）评估磁共振成像（MRI）图像以检测脑肿瘤。Milani 等人 [4] 利用主成分分析（PCA）结合人工神经网络（ANN）识别正常和异常的心音，而 Cruz 等人 [5] 应用 ANN 进行癌症预测。Verma 等人 [6] 引入 k 近邻（kNN）算法，通过分析肾脏的超声波图像来识别肾结石。Roy Chowdhury 等人 [7] 分析眼底图像，使用高斯混合模型（GMM）、支持向量机（SVM）、kNN 和 AdaBoost 来识别糖尿病视网膜病变（DR）的严重程度等级。[8] 应用分类树（CT）机器学习算法，通过体重指数（BMI）预测高血压。D'Souza 等人 [9] 应用决策树（DT）和 SVM 机器学习模型，通过头颈部鳞状细胞癌（HNSCC）区分 HPV 阳性和 HPV 阴性患者。Zhang 等人 [10] 应用卷积神经网络（CNN）从正电子发射断层扫描（PET）图像中检测肺肿瘤。Kong 等人 [11] 应用级联 CNN 检测超声波图像中的甲状腺结节。

此外，Santos 等人 [12] 通过应用 GMM 和 SVM 在 3D 计算机断层扫描（CT）数据中识别小的肺结节。Lin 等人 [13] 通过应用 CNN 分析超声波图像来识别肩部疼痛。相应地，Isitha 等人 [14] 应用 CNN 通过分析 CT 图像的纹理模式来确定肺部疾病。在所有类型的医疗数据中，图像和视频是医学数据分析中回报最高的资源。许多临床医生依靠医学图像和视频分析来评估患者的特定疾病并监测治疗以改善疗效。因此，医学图像和视频是医疗系统中最大的数据源，包含大量有价值的信息。

超声波是目前可获得的最安全且成本效益高的医学成像方法。超声波成像包含多种应用（如心脏诊断、脊柱和内脏器官诊断）。医学超声波图像使用高频声波来捕捉人体内部部分的图像。超声波视频是通过组合实时图像生成的。因此，它可以在一帧中显示身体不同部分（如器官、血管和组织），以便临床医生更好地理解患者状况并分配特定的治疗方案 [15]。除了许多其他器官外，超声波常用于观察肺部的功能行为。超声波扫描在肺部中的普及率增加，是因为它携带了足够的信息来诊断常见的肺部病理，如胸膜病变、心包病变、呼吸困难、紫绀、咳嗽和休克 [16]。

如今，许多机器学习技术与超声波视频结合，以实现对肺部功能行为的更好预测。然而，从超声波肺部视频和图像分析的角度来看，利用现代技术开发准确的自动肺部疾病和呼吸系统疾病分类方法是至关重要的。特别是，[17] 研究了使用先进的机器学习和深度学习算法结合通用图像和视频处理技术。Correia 等人 [18] 应用 ANN 区分患有肺炎的儿童肺部超声波图像和健康儿童肺部超声波图像，并实现了 90.9% 的敏感性和 100% 的特异性。Zhou 等人 [19] 开发了一种肺部超声波表面波肌电图（LUSWE）技术，通过整合深度神经网络（DNN）模型分析肺组织质量，并达到了 99.2% 的验证准确率。Zhou 等人 [20] 进一步改进了该提出的 DNN 模型，以分析患者超声波中的间质性肺病（ILD）的肺质量密度（LMD），并达到了

---

### 参考文献

9. N Sandeep, Prakash S Kulkarni & R Yaragthi Udayakumar 2014, ‘A single-stage active damped LCL-filter-based grid-connected photovoltaic inverter with maximum power point tracking’, IEEE Conference Publications, Eighteenth National Power Systems Conference (NPSC), Vadodora, pp. 1-6.

10. Aurobinda Panda, MK Pathak & SP Srivastava 2016, ‘A Single Phase Photovoltaic Inverter Control for Grid Connected System’, Indian Academy of Sciences, vol. 41, no. 1, pp. 15-30.

11. Costantino Citro, Pierluigi Siano & Carlo Cecati 2016, ‘Designing Inverters’ Current Controllers with Resonance Frequencies Cancellation’, IEEE Transactions on Industrial Electronics, vol. 63, no. 5, pp. 3072-3080.

12. Perumala Chandrasekhar & Subham Rama Reddy 2010, ‘Design of LCL Resonant Converter for Electrolyser’, International Journal of Electronic Engineering Research, vol. 2, no. 3, pp. 435-444.

13. Behrooz Mirafzal, Mahdi Saghaleini & Ali Kashifei Kaviyani 2011, ‘An SVPWM-Based Switching Pattern for Stand-Alone and Grid-Connected Three-Phase Single-Stage Boost-Inverter’, IEEE Transactions on Power Electronics, vol. 26, no. 4, pp. 1102-1111.

14. Zhen Qin, Deshang, Sha & Xuhua Liao 2012, ‘A three-phase boost-type grid connected inverter based on synchronous reference frame control’, 27th Annual IEEE Applied Power Electronics Conference & Exposition, USA, pp. 384-388.

15. Mahdi Saghaleini & Behrooz Mirafzal 2012, ‘Reactive power control in three-phase grid connected current source boost inverter’, 27th Annual IEEE Applied Power Electronics Conference & Exposition, USA, pp. 904-910.

16. Jiabing Hu & ZQ Zhu 2011, ‘Investigation on Switching Patterns of Direct Power Control Strategies for Grid-Connected DC-AC Converters Based on Power Variation Rates’, IEEE Transactions on Power Electronics, vol. 26, no. 12, pp. 3582-3598.

17. Akanksha Singh & Behrooz Mirafzal 2019, ‘An Efficient Grid-Connected Three-Phase Single-Stage Boost Current Source Inverter’, IEEE Power and Energy Technology Systems Journal, vol. 6, no. 3, pp. 142-151.

18. Naoto Kobayashi, Yuji Hayashi, Seiji Iyasu & Yuichi Handa 2019, ‘Fast current control of the single-phase DC-AC converter using digital peak current mode control’, 2019 21st European Conference on Power Electronics and Applications (EPE), Genova, Italy.

Taylor & Francis

Taylor & Francis Group

http://taylorandfrancis.com

比机器学习模型高出 89%。Palacio 等人 [21] 提出了一种基于成像生物标志物的自动定量超声分析（AQUA）纹理提取器，用于评估胎儿肺成熟度，并达到了 90.3% 的准确率。

同样，Prakash 等人 [22] 和 La Torre 等人 [23] 利用超声图像评估胎儿肺成熟度，分类准确率在 73% 到 96% 之间。Carne 等人 [24] 使用回归、分类树和神经网络等机器学习模型分析了胎儿肺部超声图像的纹理。其敏感性和特异性分别达到了 86.2% 和 87%。Yanran 等人 [25] 通过应用回归机器学习模型分析肺部超声图像的胎儿肺纹理，实现了超过 75% 的分类准确率。Mehanin 等人 [26] 提出了一种基于 CNN 的气胸（PTX）检测方法，使用肺部超声视频。视频在未经预处理的情况下输入到提出的分类模型中，并达到了超过 83% 的准确率。Cheng 等人 [27] 使用 CNN 将 11 种异常超声图像进行分类，准确率达到了 77.9%，而 Kulkhare 等人 [28] 应用相同的模型来检测超声图像中的 5 种肺部异常。Than 等人 [29] 采用 SVM 分类器对肺部图像的 Riesz 特征进行分类，以识别不同类型的肺部疾病，并达到了 99.53% 的分类准确率。Burgos 等人 [30] 从超声图像中提取了经验模态分解（EMD）特征。使用 PCA 算法降低提取的 EMD 特征的维度，并利用 kNN 机器学习模型对健康患者和肺炎患者的肺部进行分类，准确率达到了 83.33%。同样，Prasanth 等人 [31] 应用 kNN 分类模型来检测肺部液体的变化，准确率达到了 91.7%。Veeramani 等人 [32] 通过卷积局部四元模式、Haralick 特征提取、方向梯度直方图和完整局部二值模式特征从肺部超声图像中提取特征。提取的特征使用多级相关性向量机（RVM）分类器进行分类，以识别诸如呼吸窘迫综合征（RDS）、新生儿暂时性呼吸急促、气胸、肺炎、细支气管炎、胎粪吸入综合征和肺癌等肺部疾病。这种提出的分类方法达到了 100% 的准确率。

应用回归、分类树和 CNN 模型的研究工作分类准确率低于 90% [24,27]，而许多其他研究工作使用 ANN、DNN、SVM 和 kNN 模型实现了超过 90% 的分类准确率。这些分类结果之间的差异表明，分类模型的选择在超声视频和图像分析任务中发挥着重要作用。可以指出，根据所做的特征选择，每个分类模型的效果可能会产生不同的分类结果。这一点在 [32] 中得到了很好的证明，该研究对其提取的特征达到了 100% 的分类准确率。因此，在选择机器学习分类模型对正常与异常图像进行分类之前，选择最佳特征是至关重要的。

近年来，肺部超声视频分析超越了其他超声分析应用，在许多医学发现中占据了主导地位。超声视频分析所受到的这种关注可能源于 COVID-19 大流行，该大流行在全球各国引发了潜在的健康威胁。COVID-19 疾病是由严重急性呼吸综合征冠状病毒 2（SARS-CoV-2）病毒引起的。SARS-CoV-2 是一种有包膜、高度多样化且单链的 RNA 病毒，起源于蝙蝠 [33]。顾名思义，SARS-CoV-2 患者会遭受呼吸系统疾病的折磨。根据世界卫生组织（WHO）的说法，这类病毒对肺部的攻击分为三个阶段：首先，病毒从感染者传播给个人，并进行病毒复制。随后，病毒侵染并杀死纤毛细胞，纤毛是存在于肺部以保护其免受病原体入侵的毛发状结构。

纤毛细胞的损伤导致肺部充满碎片和液体，从而导致呼吸短促，这是 COVID-19 患者发展的主要症状。为了修复受损的肺部和组织，免疫细胞涌入肺部。然后，它们开始侵袭病毒。然而，有时会发生过敏反应，其中免疫细胞损伤健康细胞，这种情况被称为免疫高反应性，是病毒攻击的第二阶段。持续的肺部损伤会导致第三阶段，即肺破坏，此时呼吸器官无法正常工作，从而导致死亡。并非所有 COVID-19 患者都可能经历所有三个阶段；只有 25% 的患者遭遇了肺部破坏，且其中许多人将在慢性肺部损伤中幸存 [34]。

### 4.1.2 动机与问题陈述

通常，病毒和许多其他疾病会影响肺部的呼吸功能。在众多肺部疾病中，COVID-19 在全球范围内造成了严重损害，各国试图遏制其传播，从而影响了医疗、金融、工业和教育。WHO 的报告显示，全球确诊的 COVID-19 患者超过 17,900,500 人，死亡人数超过 680,000 人 [35]。此外，WHO 指出，许多脆弱人群感染这种病毒的可能性很高，并且随后可能导致危险损害 [36]。迫切需要有效的治疗方法来治疗这种病毒。然而，目前研究人员的工作重点是寻找抗病毒药物或疫苗。尽管如此，仍有不少研究工作正在通过分析肺部超声视频来早期预测 COVID-19 感染患者，以控制病毒的传播，同时等待尚未定论的疫苗治疗方案。

本研究分析肺部的吸气（inhalation）和呼气（exhalation）模式，以识别 COVID-19 感染患者的特定变化。为了进行此分析，考虑到肺部超声视频，因为它们可以提供许多肺部运动信息，只需瞥一眼即可获取。呼吸过程中发生的运动将在本研究中予以考虑，以识别肺部运动特性的变化。本研究采用非刚性体（NRB）算法，通过计算肺部视频序列中连续帧的运动矢量来找出变化的肺部运动特性。本研究提出了几种有监督的机器学习分类模型，用于对计算出的运动矢量进行进一步分析。

### 4.1.3 章节结构

本文其余部分组织如下：**第 2 节**描述了实现既定问题陈述的所提出方法论。该方法论分为四个小节：数据收集与预处理、特征提取、特征处理和分类。**第 3 节**展示了特征分析和分类的结果与讨论。**第 4 节**提供了研究的最终结论和结论。此外，本节还介绍了该工作的可能扩展和发展方向。

### 4.2 提出的方法论

所提出的肺部超声视频分类方法论的必要步骤如图 4.1 所示。输入的超声视频在收集后，在划分为训练和测试数据集之前进行了预处理。然后，从训练和测试数据集中提取特征。提取的特征在分类任务完成之前进行了进一步处理。最后，实施了有监督的机器学习方法，以从正常人群中预测 COVID-19 感染者。

### 4.2.1 数据收集与预处理

本研究使用的数据集是一个公开可用的在线数据库，其中包括正常受试者以及感染 COVID-19 病毒、细菌性肺炎或病毒性肺炎患者的肺部超声视频。该数据集由作者和贡献者定期更新。然而，我们选择了最近更新的版本，即 2020 年 7 月更新的数据集。有关该数据集的更多详情可在以下位置找到：

`https://github.com/jannismborn/covid19_pocus_ultrasound/tree/master/data`
