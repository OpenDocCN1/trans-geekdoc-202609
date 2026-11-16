

hypertensive and non-hypertensive cases. MLP computed high precision (0.99) for hypertensive cases but relatively lower recall (0.78) that results in an F1 score of 0.87. For non-hypertensive cases, the model performs better with a precision of 0.85, recall of 0.99, and an F1 score of 0.92. In summary, XGBoost, CatBoost, and LGBM performed extremely well for both the classes while MLP performs decently and it indicates room for improvement in classifying the hypertensive and non-hypertensive class. In addition, a comparison table (Table 4) has been created to assess the accuracy of the existing techniques with the techniques discussed in this paper for hypertension detection and classification.

| Author's Name | Dataset | Techniques | Accuracy |
| :--- | :--- | :--- | :--- |
| Martinez-Rios et al. (2022) | PPG数据 | 支持向量机 | 71.42% |
| Fang et al. (2023) | 30k条记录的数据 | KNN+LGBM | 86% |
| LaFreniere et al. (2016) | 185,371名患者的数据 | 神经网络模型 | 82% |
| Soh et al. (2020) | 原始ECG数据 | CNN | 99.99% |
| **本文** | **高血压数据集** | **XGBoost, CatBoost, LGBM** | **100%** |

## 5 结论

在高血压检测领域，AI学习技术的应用已显示出显著的进步和前景。值得提及的是，XGBoost、CatBoost和LGBM等分类器在区分高血压和非高血压病例方面表现出了卓越的精确度、召回率、F1得分和准确率。尽管取得了这些成就，但仍存在一些挑战，尤其是多层感知机（MLP）模型。该模型在实现高准确率方面面临困难。这强调了需要持续优化和改进神经网络模型，以提高其在全面高血压检测中的性能。

遇到的挑战涉及复杂的数据模式，以及持续研究和开发模型架构的需求。理解和驾驭这些复杂性对于推动机器学习和深度学习技术的融合至关重要，这在高血压检测方面具有巨大潜力。未来工作应优先深入探索数据模式、精调模型架构并探索创新的优化策略。这种迭代过程将有助于推动更可靠、准确且易于获取的高血压检测诊断工具的发展，进一步加强计算机科学与医疗保健之间的协作。

## 参考文献

- Angayarkanni, G. 和 Hemalatha, S., 2023年3月. 监督机器学习算法在多种疾病预测中的性能评估：一项比较研究. 在 *2023年第9届先进计算与通信系统国际会议（ICACCS）* (第1卷，第1–7页). IEEE.
- Aras, M.A., Abreau, S., Mills, H., Radhakrishnan, L., Klein, L., Mantri, N., Rubin, B., Barrios, J., Chehoud, C., Kogan, E. 和 Gitton, X., 2023. 使用深度学习进行肺动脉高压心电图检测. *心脏衰竭杂志*.
- Bohr, A. 和 Memarzadeh, K., 2020. 医疗保健应用中人工智能的兴起. 在 *医疗保健中的人工智能* (第25–60页). Academic Press.
- Chaplot, N., Pandey, D., Kumar, Y. 和 Sisodia, P.S., 2023. 利用各种基因疾病进行遗传疾病预测和预后的人工智能技术综合分析. Archives of Computational Methods in Engineering, 30(5), 第3301–3323页.
- Fang, M., Chen, Y., Xue, R., Wang, H., Chakraborty, N., Su, T. 和 Dai, Y., 2023. 高血压风险预测的混合机器学习方法. Neural Computing and Applications, 35(20), 第14487–14497页.
- Kaur, S., Bansal, K. 和 Kumar, Y., 2022年12月. 预测高血压疾病的人工智能方法：开放挑战与研究问题. 在 2022年第5届当代计算与信息学国际会议（IC3I） (第338–343页). IEEE.
- Koul, A., Bawa, R.K. 和 Kumar, Y., 2022. 气道疾病医学图像处理中的人工智能. 在 连接式电子健康：集成物联网与云计算 (第217–254页). Cham：Springer International Publishing.
- Koul, A., Bawa, R.K. 和 Kumar, Y., 2023. 预测气道疾病的人工智能技术：系统综述. Archives of Computational Methods in Engineering, 30(2), 第831–864页.
- Kumar, Y., Gupta, S., Singla, R. 和 Hu, Y.C., 2022. 癌症预测和诊断中人工智能技术的系统综述. Archives of Computational Methods in Engineering, 29(4), 第2043–2070页.
- LaFreniere, D., Zulkernine, F., Barber, D. 和 Martin, K., 2016年12月. 使用机器学习从临床数据集中预测高血压. 在 2016年IEEE计算智能研讨会系列（SSCI） (第1–7页). IEEE.
- Martinez-Rios, E., Montesinos, L. 和 Alfaro-Ponce, M., 2022. 基于光电容积描记法和临床数据的高血压检测机器学习方法. Computers in Biology and Medicine, 145, 第105479页.
- Raju, Y.R., Abiona, T. 和 Gureje, O., 2017. 老年尼日利亚人中高血压认知及其对血压控制的影响：来自伊巴丹老龄化研究的报告. The Pan African Medical Journal, 27.
- Saha, P., Patikar, S. 和 Neogy, S., 2020年10月. 基于相关系列前向选择的医疗保健数据分析特征选择方法. 在 2020年IEEE计算、电力和通信技术国际会议（GUCON） (第69–72页). IEEE.
- Silva, G.F., Fagundes, T.P., Teixeira, B.C. 和 Chiavegatto Filho, A.D., 2022. 高血压预测机器学习：系统综述. Current Hypertension Reports, 24(11), 第523–533页.
- Singh, J., Sandhu, J.K. 和 Kumar, Y., 2023. 使用基于人工智能的学习方法和超参数对不同类别皮肤病的检测和诊断分析. Archives of Computational Methods in Engineering, 第1–28页.
- Soh, D.C.K., Ng, E.Y.K., Jahmunah, V., Oh, S.L., San Tan, R. 和 Acharya, U.R., 2020. 使用卷积神经网络的高血压自动诊断工具. Computers in Biology and Medicine, 126, 第103999页.

## 基于深度学习的多元回归分析方法用于设计医学图像识别系统

Shweta Singh  
电子与通信系，IES技术学院，博帕尔，印度

A.N. Jagadish  
计算机科学系，巴普吉工程技术学院，达瓦纳格雷  
卡纳塔克邦，印度

Bhuman Vyas  
信用接受，坎顿，美国

Mohammed Wasim Bhatt  
模型工程技术学院，查谟，查谟和克什米尔，印度

Aws Zuhair Sameen  
医疗技术学院，法拉德大学，巴格达，伊拉克

Sheshang Degadwala  
计算机工程系，西格玛大学，瓦多达拉，古吉拉特邦，印度

摘要：机器学习模型是优化模型，能够收集数据、评估数据，并为专家和管理层提供其做出最佳决策所需的报告。本研究采用定量研究，因为它旨在收集信息并利用回归分析和方差分析等统计模型进行分析。研究人员希望使用描述性分析、回归分析和方差分析（ANOVA）等统计技术来分析假设。作者使用目的抽样技术来选择在医疗保健领域工作的受访者。使用了一种名为目的抽样的非概率抽样技术。根据分析，R平方值为0.744，即74.4%。根据调查，改进的图像质量与基于机器学习的数字图像识别技术之间存在强相关性。

## 1 引言

像人工智能、机器学习和深度学习这样的新技术的出现正在改变商业的不同领域及其相关流程。机器学习在图像处理领域的应用，主要在与大规模图像分析和提供清晰输出相关的领域，与机器学习相关的技术一直非常有帮助，因为它可以处理复杂信息并提供更好的输出。机器学习支持用户分离图像以便以更清晰的形式识别图像，应当注意的是，基于机器学习的图像处理技术在现代世界日益普及，因为用户需要更好的图像分类、分割和整体识别（Kim et al. 2017）。例如，在医疗保健行业，医疗从业者和护士希望分割图像以识别疾病和其他问题，以便可以提供适当的医疗

