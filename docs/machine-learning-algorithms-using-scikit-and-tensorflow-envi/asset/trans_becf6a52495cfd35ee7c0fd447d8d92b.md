

### 图 4. 性别与失智症率

![](img/20813928ec98c7f6fbdbab0d52bde2f1_222_0.png)

### 图 5. MMSE 分析

![](img/20813928ec98c7f6fbdbab0d52bde2f1_222_1.png)

### 图 6. ASF 分析

![](img/20813928ec98c7f6fbdbab0d52bde2f1_222_2.png)

### 图 7. eTIV 分析

![](img/20813928ec98c7f6fbdbab0d52bde2f1_223_0.png)

### 图 8. nWBV 分析

![](img/20813928ec98c7f6fbdbab0d52bde2f1_223_1.png)

我们的主要性能指标是接收者操作特征曲线下面积（AUC）。我们认为，对于非致命性终末疾病（如大多数神经退行性疾病）的医学诊断而言，高真阳性率至关重要，以便尽快识别所有阿尔茨海默病患者。然而，由于我们不希望将健康成年人误诊为精神疾病并开始医疗治疗，我们也希望确保假阳性率尽可能低。因此，AUC 似乎是性能指标的完美选择。下表 1 显示了带有训练得分和测试得分的不同分类器。误分类数量和误分类百分比也列在给定的表 1 中。

### 表 1. 分类分析

| 分类器 | 训练得分 | 测试得分 | 误分类数 | 误分类百分比 | 训练时间 | 预测时间 |
|---|---|---|---|---|---|---|
| 随机森林 | 0.975410 | 0.910714 | 4 | 8.888889 | 0.025142 | 0.002500 |
| 带交叉验证的随机森林 | 1.000000 | 0.910714 | 4 | 8.888889 | 0.866884 | 0.062739 |
| XGBoost | 0.964406 | 0.872024 | 6 | 13.333333 | 0.123368 | 0.000881 |
| 带交叉验证的 XGBoost | 1.000000 | 0.910714 | 4 | 8.888889 | 0.420718 | 0.000897 |

### 图 9. 比较分析

![](img/20813928ec98c7f6fbdbab0d52bde2f1_224_0.png)

### 图 10. 混淆矩阵

![](img/20813928ec98c7f6fbdbab0d52bde2f1_224_1.png)

我们建议使用随机森林方法尽早预测老年人的阿尔茨海默病。接下来，将随机森林的性能指标与 XGBoost 和带交叉验证的 XGBoost 进行比较。比较分析表明，所提方法优于其他方法。图 9 显示了不同算法的比较分析。

图 9 显示了所提工作的混淆矩阵分析。除了为临床决策提供科学指导（最优子集）外，所提可解释框架有助于在不平衡的 AD 多类分类任务中实现出色性能，从而促进疾病管理，并为优化 AD 预防和治疗方案产生新的研究思路。

## 5. 结论

阿尔茨海默病会导致大脑萎缩并最终死亡。阿尔茨海默病无法治愈，但会导致人的记忆、推理能力、行为和社交技能逐渐退化。更多研究人员提出了更多算法来检测阿尔茨海默病。但准确率非常低。在本所提系统中，使用一种高效算法来早期检测阿尔茨海默病。所提算法使用 XGBoost 和随机森林算法来检测阿尔茨海默病。数据集用于训练，并且还使用情绪识别来早期预测阿尔茨海默病。随机森林算法的训练得分为 97%，测试得分为 91%。XGBoost 算法的训练得分为 1.00，测试得分为 87.2%。随机森林算法和 XGBoost 算法进行了比较。与 XGBoost 算法相比，随机森林算法具有最佳准确率。

## 参考文献

Bari Antor, M., Jamil, A. H. M., Mamtaz, M., Monirujjaman Khan, M., Aljahdali, S., Kaur, M., Singh, P., & Masud, M. (2021). 用于预测阿尔茨海默病的机器学习算法比较分析. 医疗工程期刊. doi:10.1155/2021/9917919 PMID:34336171

Bron, E. E., Klein, S., Papma, J. M., Jiskoot, L. C., Venkatraghavan, V., Linders, J., Aalten, P., De Deyn, P. P., Biessels, G. J., Claassen, J. A., Middelkoop, H. A., Smits, M., Niessen, W. J., van Swieten, J. C., van der Flier, W. M., Ramakers, I. H. G. B., & van der Lugt, A. (2021). 基于 MRI 的阿尔茨海默病诊断和预测中深度与传统机器学习的跨队列泛化能力. NeuroImage. 临床, 31, 102712. doi:10.1016/j.nicl.2021.102712 PMID:34118592

Chang, C. H., Lin, C. H., & Lane, H. Y. (2021). 阿尔茨海默病诊断的机器学习与新型生物标志物. 分子科学国际期刊, 22(5), 2761. doi:10.3390/ijms22052761 PMID:33803217

Chitradevi, D., & Prabha, S. (2020). 阿尔茨海默病中利用优化技术和深度学习方法分析脑亚区. 应用软计算, 86, 105857. doi:10.1016/j.asoc.2019.105857

Ding, Y., Sohn, J. H., Kawczynski, M. G., Trivedi, H., Harnish, R., Jenkins, N. W., Lituiev, D., Copeland, T. P., Aboian, M. S., Mari Aparici, C., Behr, S. C., Flavell, R. R., Huang, S.-Y., Zalocusky, K. A., Nardo, L., Seo, Y., Hawkins, R. A., Hernandez Pampaloni, M., Hadley, D., & Franc, B. L. (2019). 利用脑 18F-FDG PET 预测阿尔茨海默病诊断的深度学习模型. 放射学, 290(2), 456–464. doi:10.1148/radiol.2018180958 PMID:30398430

Fisher, C. K., Smith, A. M., Walsh, J. R., Simon, A. J., Edgar, C., Jack, C. R., Holtzman, D., Russell, D., Hill, D., Grosset, D., Wood, F., Vanderstichele, H., Morris, J., Blennow, K., Marek, K., Shaw, L. M., Albert, M., Weiner, M., Fox, N., ... Kubick, W. (2019). 用于阿尔茨海默病进展综合预测的机器学习. 科学报告, 9(1), 13622. doi:10.1038/s41598-019-49656-2 PMID:31541187

Franzmeier, N., Koutsouleris, N., Benzinger, T., Goate, A., Karch, C. M., Fagan, A. M., McDade, E., Duering, M., Dichgans, M., Levin, J., Gordon, B. A., Lim, Y. Y., Masters, C. L., Rossor, M., Fox, N. C., O’Connor, A., Chhatwal, J., Salloway, S., Danek, A., ... Ewers, M. (2020). 通过遗传性阿尔茨海默病信息的机器学习预测散发性阿尔茨海默病进展. 阿尔茨海默病与失智症, 16(3), 501–511. doi:10.1002/alz.12032 PMID:32043733

Grassi, M., Loewenstein, D. A., Caldirola, D., Schruers, K., Duara, R., & Perna, G. (2019). 用于预测阿尔茨海默病转化的可临床转化机器学习算法：通过迁移学习方法验证其准确性的进一步证据. 国际精神老年学期刊, 31(7), 937–945. doi:10.1017/S1041610218001618 PMID:30426918

Grueso, S., & Viejo-Sobera, R. (2021). 从轻度认知障碍到阿尔茨海默病失智症进展的机器学习方法：系统综述. 阿尔茨海默病研究与治疗, 13(1), 1–29. doi:10.1186/s13195-021-00900-w PMID:34583745

Jain, R., Jain, N., Aggarwal, A., & Hemanth, D.J. (2019). 基于磁共振脑图像的卷积神经网络阿尔茨海默病分类. 认知系统研究, 57, 147–159. doi:10.1016/j.cogsys.2018.12.015

Kavitha, C., Mani, V., Srividhya, S. R., Khalaf, O. I., & Tavera Romero, C. A. (2022). 使用机器学习模型进行早期阿尔茨海默病预测. 公共健康前沿, 10, 853294. doi:10.3389/fpubh.2022.853294 PMID:35309200

Khan, N. M., Abraham, N., & Hon, M. (2019). 用于预测阿尔茨海默病的带智能训练数据选择的迁移学习. IEEE Access：实用创新与开放解决方案, 7, 72726–72735. doi:10.1109/ACCESS.2019.2920448

Kumari, R., Nigam, A., & Pushkar, S. (2020). 阿尔茨海默病早期检测的机器学习技术. 微系统技术, 26(12), 3935–3944. doi:10.1007/s00542-020-04888-5

Kundaram, S. S., & Pathak, K. C. (2021). 基于深度学习的阿尔茨海默病检测. 载于《第四届微电子、计算与通信系统国际会议论文集：MCCS 2019》（第 587–597 页）。新加坡：Springer Singapore.

Lee, J., Meijer, E., Langa, K. M., Ganguli, M., Varghese, M., Banerjee, J., Khobragade, P., Angrisani, M., Kurup, R., Chakrabarti, S. S., Gambhir, I. S., Koul, P. A., Goswami, D., Talukdar, A., Mohanty, R. R., Yadati, R. S., Padmaja, M., Sankhe, L., Rajguru, C., ... Dey, A. B. (2023). 印度失智症患病率：全国性研究的全国和各州估计. 阿尔茨海默病与失智症, 19(7), 2898–2912. doi:10.1002/alz.12928 PMID:36637034

Leong, L. K., & Abdullah, A. A. (2019, November). 使用带 Boruta 算法作为特征选择方法的机器学习技术预测阿尔茨海默病 (AD). 物理学期刊：会议系列, 1372(1), 012065. doi:10.1088/1742-6596/1372/1/012065

Li, H., Habes, M., Wolk, D. A., & Fan, Y. (2019). 基于海马磁共振成像数据的阿尔茨海默病失智症早期预测深度学习模型. 阿尔茨海默病与失智症, 15(8), 1059–1070. doi:10.1016/j.jalz.2019.02.007 PMID:31201098

