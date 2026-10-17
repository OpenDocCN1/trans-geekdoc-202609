
除了细胞状态外，LSTM 单元还包含输入门、输出门和遗忘门，用于短期和长期记忆。除了控制信息流和存储任意时长的值外，三个门还控制信息如何进入和离开细胞。

(15)

```
F[1] = σ(w[f]|a[f − 1],x[d]|+y[f])
```

(16)

```
X[1] = σ(w[f]|a[f − 1],x[d]|+y[f])
```

具有门控机制的 LSTM 单元如图 2 所示。每个 LSTM 门都有一个 Sigmoid 激活函数和一个逐点乘法运算，并包含三个门（输入门、遗忘门和输出门）。

![图 2. 使用 LSTM 进行心血管疾病预测。](img/fig11_2_B.jpg)

图 2. 使用 LSTM 进行心血管疾病预测。

### 4. 结果与讨论

所提出的技术在 UCI 仓库心脏数据集上，在各种边界条件下进行了实施和评估。这些技术基于各种要素及其特征来评估疾病预测的有效性。借助不同策略对评估结果进行了检查。结果在本部分中介绍。

用于评估不同方法获得的效率的详细信息见表 1。因此，确定了这些方法针对各种参数的有效性。获得的结果在本节中详细说明。

表 1. 评估详情。

| 仿真参数 | 值 |
| --- | --- |
| 使用工具 | Python, Jupiter notebook |
| 使用数据集 | 心脏数据集 |
| 特征数量 | 30 |
| 数据量 | 500 |

根据图 3，每种方法产生不同的分类性能。使用 LSTM-CNN，我们可以准确地对不同疾病进行聚类。

![图 3. 分类准确率。](img/fig11_3_B.jpg)

图 3. 分类准确率。

$$Accuracy = \frac{TP + TN}{TP + TN + FN + FP}$$

如图 4 所示，不同方法在疾病预测中产生不同水平的准确率。与使用其他方法相比，使用所提出的 LSTM-CNN 方法在每个类别的疾病预测中具有更高的准确率。

![图 4. 疾病预测分析的准确率。](img/fig11_4_B.jpg)

图 4. 疾病预测分析的准确率。

$$Precision = \frac{TP}{TP + FP}X100$$

图 5 显示，精确率（也称为阳性预测值）是预测错误数除以特征输入总数。在所提出的方法中，LSTM-CNN 产生 92% 的正确值，优于现有方法。

![图 5. 精确率性能。](img/fig11_5_C.jpg)

图 5. 精确率性能。

$$Recall = \frac{TP}{TP + FP} \times 100$$

这是衡量针对该类别的总输入特征数，正确类别预测的数量，如图 6 所示。对于包含比先前算法更好结果的建议方法，这表明分类器在召回率计算中的完整性。

![图 6. 召回率性能。](img/fig11_6_C.jpg)

图 6. 召回率性能。

不同方法产生的疾病预测准确率对比见图 7。与使用其他方法相比，使用 LSTM-CNN 算法在每个类别中预测疾病具有更高的准确率。

![图 7. 错误分类率分析。](img/fig11_7_B.jpg)

图 7. 错误分类率分析。

### 5. 结论

总之，基于深度谱时变特征分析模型和 Softmax LSTM-CNN 的心脏病预测联邦学习产生了最佳预测准确率。所提出的系统分析心脏病影响率 (CDIR)，根据边际准确率选择心脏特征。这减少了大数据维度问题，使在循环神经网络上训练的特征成为最佳训练特征。结果因素证明，就心脏病影响率而言，实现了高达 97% 的最佳分类准确率。这支持了一种更好的早期风险疾病预测方式，以便进行早期治疗，减少心脏病发作。

### 参考文献

1. Arpaia, P., Cicatiello, M., Benedetto, E.D., Anna Dodaro, C., Duraccio, L., Servillo, G. and Vargas, M. 2020. A health 4.0 Integrated system for monitoring and predicting patient's health during surgical procedures. 2020 IEEE International Instrumentation and Measurement Technology Conference.

2. Mei, X. 2017. Predicting five-year overall survival in patients with non-small cell lung cancer by relief algorithm and random forests. 2017 IEEE 2nd Advanced Information Technology, Electronic and Automation Control Conference.

3. Castaldo, R., Melillo, P., Izzo, R., De Luca, N. and Pecchia, L. 2017. Fall prediction in hypertensive patients via short-term HRV analysis. IEEE Journal of Biomedical and Health Informatics, 21(2): 399–406.

4. Kumar, A. and Anjomshoa, H. 2018. A two-stage model to predict surgical patients' lengths of stay from an electronic patient database. IEEE Journal of Biomedical and Health Informatics, 1–1.

### 参考文献

5. Beitel-White, N., Martin, R.C.G. and Davalos, R.V. 2019. 施用于人类胰腺癌患者的不可逆电穿孔波形的治疗后分析。*2019 年第 41 届 IEEE 工程医学与生物学学会年会*。

6. Latha, R. and Vetrivelan, P. 2019. 基于边缘/雾计算的血液粘度心脏病风险预测模型。*2019 年第 11 届通信系统与网络国际会议*。

7. Sudeshna, P., Bhanumathi, S. and Hamlin, M.R.A. 2017. 利用文本数据挖掘从生物医学文献中识别心脏病的症状与治疗。*2017 年电力、能源、信息与通信计算国际会议*。

8. Ed-Daoudy, A. and Maalmi, K. 2019. 基于大数据方法的心脏病早期检测实时机器学习。*2019 年无线技术、嵌入式与智能系统国际会议*。

9. Chauhan, A., Jain, A., Sharma, P. and Deep, V. 2018. 基于进化规则学习的心脏病预测。*2018 年第 4 届计算智能与通信技术国际会议*。

10. Qidwai, U. 2018. 从模糊数据到清晰估计：辅助神经外科医生为卒中患者做出更好的治疗选择。*2018 年 IEEE-EMBS 生物医学工程与科学会议*。

11. Kasbe, T. and Pippal, R.S. 2017. 基于模糊逻辑的心脏病诊断系统设计。*2017 年能源、通信、数据分析与软计算国际会议*。

12. Meena, G., Chauhan, P.S. and Choudhary, R.R. 2017. 心脏病数据集分类的实证研究——其预测与挖掘。*2017 年计算机、电气、电子与通信当前趋势国际会议*。

13. Pawlovsky, A.P. 2018. 基于距离的集成 kNN 方法用于心脏病诊断。*2018 年电子、信息与通信国际会议*。

14. Gavhane, A., Kokkula, G., Pandya, I. and Devadkar, P.K. 2018. 利用机器学习预测心脏病。*2018 年第二届电子、通信与航空航天技术国际会议*。

15. Raju, C., Philipsy, E., Chacko, S., Padma Suresh, L. and Deepa Rajan, S. 2018. 利用数据挖掘技术预测心脏病的综述。*2018 年新兴设备与智能系统会议*。

16. Ed-Daoudy, A. and Maalmi, K. 2019. 基于大数据方法的心脏病早期检测实时机器学习。*2019 年无线技术、嵌入式与智能系统国际会议(WITS)，摩洛哥非斯，第 1–5 页*。

17. Tuan D. Pham, Honghui Wang, Xiaobo Zhou, Dominik Beck, Miriam Brandl and Gerard Hoehn. 2008. 利用质谱数据计算预测模型早期检测心血管事件风险。*IEEE 生物医学工程信息技术汇刊*，12(5): 636–643。

18. Joo, G., Song, Y., Im, H. and Park, J. 2020. 利用大数据机器学习预测心血管疾病发生的临床意义。*IEEE Access*，8: 157643–157653。

19. Boudra, H., Obaid, A. and Amja, A.M. 2014. 基于传感器和无线传感器网络的智能医疗监测系统。*IEEE 计算、通信与信息学进展国际会议，第 1650–1656 页*。

20. Tomasic, I., Khosraviani, K., Rosengren, P., Jörntén-Karlsson, M. and Lindén, M. 2018. 实现基于物联网的患者环境参数监测：使用 OpenMote 结合 OpenWSN 和 Contiki-NG 的经验。*2018 年第 41 届信息与通信技术、电子与微电子国际大会(MIPRO)，奥帕蒂亚，第 0330–0334 页*。

21. Catarinucci, L., Donno, D., Mainetti, L., Palano, L., Patrono, L., Stefanizzi, M.L. and Tarricone, L. 2015. 面向智能医疗系统的物联网感知架构。*IEEE 物联网期刊*，2(6): 515–526。

22. Varatharajan, R., Manogaran, G., Priyan, M.K. and Sundarasekar, R. 2017. 利用动态时间规整算法通过可穿戴传感器设备早期检测阿尔茨海默病。*集群计算，第 1–10 页*。

23. Chanak, P. and Banerjee, I. 2020. 面向智能医疗应用的物联网无线传感器网络无拥塞路由机制。*IEEE 消费电子汇刊*，66(3): 223–232。

24. Li, P., Haq, A.U., Din, S.U., Khan, J., Khan, A. and Saboor, A. 2020. E-医疗中基于机器学习分类的心脏病识别方法。*IEEE Access*，8: 107562–107582。

25. Kavitha, R. and Kannan, E. 2016. 基于数据挖掘中特征提取与特征选择技术的高效心脏病分类框架。*2016 年工程、技术与科学新兴趋势国际会议，第 1–5 页*。

26. Jabbar, M.A., Chandra, P. and Deekshatulu, B.L. 2012. 利用关联分类与混合特征子集选择预测心脏病风险评分。*2012 年第 12 届智能系统设计与应用国际会议，第 628–634 页*。

27. Haq, U., Li, J., Memon, M.H., HunainMemon, M., Khan, J. and Marium, S.M. 2019. 基于机器学习模型与序列后向选择算法进行特征选择的心脏病预测系统。*2019 年 IEEE 第 5 届技术融合国际会议，印度孟买，第 1–4 页*。

28. Mohan, S., Thirumalai, C. and Srivastava, G. 2019. 利用混合机器学习技术进行有效的心脏病预测。*IEEE Access*，7: 81542–81554。

29. Javeed, A., Zhou, S., Yongjian, L., Qasim, I., Noor, A. and Nour, R. 2019. 基于随机搜索算法与优化随机森林模型的智能学习系统，用于改进心脏病检测。*IEEE Access*，7: 180235–180243。

30. Jikuo Wang, Changchun Liu, Liping Li, Wang Li, Lianke Yao, Han Li and Huan Zhang. 2020. 一种用于冠心病无创检测的基于堆叠的模型。*IEEE Access*，8: 37124–37133。

31. Pasha, S.J. and Mohamed, E.S. 2020. 用于有效疾病风险预测的新型特征降维(NFR)模型，结合机器学习与数据挖掘算法。*IEEE Access*，8: 184087–184108。

32. Alkhodari, M., Islayem, D.K., Alskafi, F.A. and Khandoker, A.H. 2020. 利用心率变异性与机器学习预测发生血管事件高风险的高血压患者。*IEEE Access*，8: 192727–192739。

33. Liaqat Ali, Awais Niamat, Javed Ali Khan, Noorbakhsh Amiri Golilarz and Xiong Xingzhon. 2019. 一种优化的堆叠支持向量机专家系统，用于有效预测心力衰竭。*IEEE Access*，7: 54007–54014。

34. Sarmah, S.S. 2020. 一种基于深学习改进神经网络的高效物联网患者监测与心脏病预测系统。*IEEE Access*，8: 135784–135797。

35. Guo, C., Zhang, J., Liu, Y., Xie, Y., Han, Z. and Yu, J. 2020. 面向医疗物联网平台的递归增强随机森林结合改进线性模型(RERF-ILM)用于心脏病检测。*IEEE Access*，8: 59247–59256。

# 第 12 章：基于联邦学习的阿尔茨海默病预测

*S Suchitra*^(¹²)

电子邮件：senthamn@srmist.edu.in; jeyaselm@srmist.edu.in; poovaraghan1976@gmail.com

### 1. 简介

根据 2021 年的统计数据，印度阿尔茨海默病的总体患病率为：55 岁及以上人群为 0.84%，65 岁及以上人群为 1.36%。其治疗费用极高。由于印度每次神经影像检查的费用超过 5000 美元，这也是印度鲜有人能负担得起如此昂贵检测手段的原因。如果能早期发现阿尔茨海默病，患者从治疗中获益的可能性会增加。与人口数量相比，印度医疗专业人员较少，因此开发一种能够检测阿尔茨海默病早期阶段的模型显得尤为重要。2020 年新冠疫情期间，因阿尔茨海默病导致的死亡人数增加了 17%。印度缺乏足够的阿尔茨海默病护理专业人员来妥善应对国内呈现的病例数量。这呼吁部署一套系统以满足患者需求。正如在世界其他地区一样，计算机、手机、移动电话和互联网在发展中国家也随处可得。

在现有系统中，需要解决以下问题：(i) 阿尔茨海默病和衰老都会导致脑体积萎缩。这使得仅凭 MRI 扫描难以将阿尔茨海默病患者与健康老年人区分开来。(ii) 下一个主要问题是缺乏足够的数据。(iii) 深度学习解决方案存在困难，如算法复杂度高、过拟合和欠拟合，这些问题处理起来有点棘手。(iv) 部分阿尔茨海默病症状与其他疾病相似，使得鉴别诊断变得困难。

本项目旨在利用联邦学习方法，为早期疾病识别提供精准结果，以加速阿尔茨海默病的治疗。该过程可缩短治疗和检测过程所需的时间。借助患者的 MRI 影像也能释放大量人力资源，使医院医生能专注于治疗过程而非检测。这也将确保该脑部疾病对患者造成的损害降至最低，并减缓其进展。这有赖于一个准确、快速且可靠的检测系统。

阿尔茨海默病的早期诊断让患者有更大机会从疾病治疗中获益，并使他们有资格参加多项临床研究。药物在疾病发病早期阶段能提供更多益处。这为规划与阿尔茨海默病患者治疗相关的医疗和财务决策争取了时间。它还为获得适当的服务和支持以控制进行性病情打开了大门。它有助于排除其他伴有类似痴呆症状的可治疗疾病。只有在疾病早期被诊断出时，药物和非药物治疗才能帮助患者。这呼吁建立一个有效、可靠且快速的系统，以尽早检测疾病并开始必要的治疗。医疗系统及其活动的多面性导致医疗数据在大多数情况下呈碎片化状态。然而，医疗机构可能只能检索特定患者群体的诊断信息。这些文档包含特定个人的高度隐私健康信息。已出台多项法规来规范此类数据的收集和分析。联邦学习是一种近期广受欢迎的模型，因为它展现出从分散的私密信息中学习的巨大潜力。它不一次性从多个来源收集数据，也不依赖传统的“寻找后复制”技术，而是支持利用中央服务器训练共享的全局模型，同时保留所有数据在其产生的本地社区中。

本文提出的方法建议使用深度学习技术开发一种 CNN 架构模型，利用图像分类算法在发病早期阶段检测阿尔茨海默病，这可以通过 CNN 提供的特征提取以及以 MRI 形式输入的神经影像技术，借助联邦学习高效完成；它支持在不泄露用户私密数据的情况下进行预测，并使多个用户能够开发分布式、可信且准确的机器学习模型。模型中使用的数据集源自阿尔茨海默病数据集，包含 6400 张 MRI 图像，分为四个不同类别。这些类别代表阿尔茨海默病的四个进展阶段。数据集中的图像来自 45 至 85 岁的人群。数据集经过多渠道彻底检查，检查后发现不包含任何患者的重复 MRI 图像，也不包含来自同一患者的多张图像。建议的技术在阿尔茨海默病数据集（包含 6400 张 MRI 图片）上通过精确率、召回率和准确率等指标进行了彻底检验。与现有方法相比，提出的方法显示出更高的精确度。我们提出的深度学习模型的贡献如下：(1) 提供一个更可靠、更准确的阿尔茨海默病检测系统。(2) 提高所有先前提出模型的准确性。(3) 通过联邦学习利用不同神经层提出一种高效强大的 CNN 架构。
