

score (86%)，表明集成学习通过聚合多个分类器的输出来提升预测有效性的强大优势。尽管它很强大，但其能力相对比所提议的混合技术要弱一些。

![](img/106ef0dba620d314f9842503e8ef40c8_106_0.png)

图2：性能分析 – 提议的混合模型。

这一点旨在强调，尽管常规分类器中的集成方法具有稳健性，但将CNN和LSTM等深度模型集成到XGBoost等领先机器学习算法中可以进一步提升模型性能，尤其在挑战性的多模态数据环境中。XGBoost + CNN + LSTM 混合方法优于传统机器学习方法和先前的深度模型或集成模型，并且表明，将作用于不同模态或数据结构（例如表格、序列和图像）的各种模型相结合，可显著提升预测性能和稳健性。图2展示了所提议混合模型的性能分析。

## 5 结论

本文提出了一种面向肿瘤疾病预测及前体早期阶段诊断的新型数据驱动机器学习方法。通过整合异构多模态数据集，并应用经典与深度机器学习模型的混合集成，该方法能够捕捉癌症相关数据中的复杂相互关系。结果表明，与常规单模态或单个机器学习模型相比，该联合策略具有更高的预测准确率、灵敏度和稳健性。检测高可靠性前体及早期疾病生物标志物的能力，表明该框架有潜力提升临床决策和肿瘤患者预后。尽管此处开发的模型在大多数指标上表现良好，但仍存在一些局限性。模型的直接推广性在一定程度上受限于大规模高质量数据集的使用，特别是在数据基础设施不足的地点或诊所中。即使特征选择（FS）和模型意识在一定程度上有助于模型可解释性，未来迭代中加入更多针对临床使用定制的包容性透明度功能将会有所帮助。

## 6 未来方向

未来研究将尝试将模型适应更大规模、更多样化的患者场景，以增加其治疗用途和适用性。使用Cox比例风险模型等生存分析模型和更深层的生存网络，不仅能预测疾病进展和早期诊断，还能预测患者预后和远期结局，这是该工作的有益扩展之一。这些模型将使框架适用于报告临床医生的风险调整生存概率和个体化预后信息，从而使其更贴近临床决策。为了解决数据隐私和非集中式大型数据库问题，未来活动还将探讨使用联邦学习方法。通过此方法，不同医疗机构之间可以在不显式共享数据的情况下进行协作模型训练，从而保护患者隐私，并利用更大规模的分布式数据集来提升模型性能。此外，将投入大量工作，在设想的平台上实施一个开放的、实时的临床决策支持系统。该系统将努力在医疗点以某种格式提供可操作的信息和风险估计，以便促进关于治疗的及时和明智的决策。通过在日常临床肿瘤学实践中实施预测分析，本研究旨在缩小基于研究的创新与日常采纳之间的差距，从而实现精准肿瘤学和改善患者护理的最终目标。

## 参考文献

- [1] Laghmati, S., Hamida, S., Hicham, K., Cherradi, B. & Tmiri, A. (2024). 使用ML和PCA的改进乳腺癌疾病预测系统。 *Multimedia Tools and Applications*, 83(11), 33785–33821.
- [2] Varlamova, E. V., Butakova, M. A., Semyonova, V. V., Soldatov, S. A., Poltavskiy, A. V., Kit, O. I. & Soldatov, A. V. (2024). 机器学习与癌症。 *Cancers*, 16(6), 1100.
- [3] Yang, H., Yang, M., Chen, J., Yao, G., Zou, Q. & Jia L. (2025). 面向精准肿瘤学的多模态深度学习方法：全面综述。 *Briefings in Bioinformatics*, 26(1), bbae699.
- [4] Colomer-Lahiguera, S., Gentizon, J., Christofis, M., Darnac, C., Serena, A. & Eicher, M. (2024). 实现全面、以患者为中心的癌症服务：优化精准健康核心中高级执业护士的角色。载于 *Seminars in Oncology Nursing*. 第40卷，3，151629，WB Saunders.
- [5] Kothini, R. R. 疾病预测中的人工智能：转变早期诊断和预防性医疗保健。(2024).
- [6] Darmofal, M., Suman, S., Atwal, G., Toomey, M., Chen, J.-F., Chang, J. C., Vakiani, E. 等 (2024). 使用靶向临床基因组测序数据的肿瘤类型预测深度学习模型。 *Cancer discovery*, 14(6), 1064–1081.
- [7] Arslan, S., Schmidt, J., Bass, C., Mehrrotra, D., Geraldes, A., Singhal, S., Henge, J. 等 (2024). 基于常规病理图像的深度学习预测多组学生物标志物的全面泛癌研究。 *Communications Medicine*, 4(1), 48.
- [8] Fatima, A., Shabbir, A., Janjua, J. I., Ramay, S. A., Bhatty, R. A., Irfan, M. & Abbas, T. (2024). 使用机器学习和深度学习技术分析乳腺癌检测。 *Journal of Computing & Biomedical Informatics*, 7(02).
- [9] Kaur, H., Das, P., Camphausen, K. & Shankavaram, U. (2024). CPSM：用于预测单个癌症患者生存概率的自动化机器学习管道R包。 *bioRxiv*, 2024-11.
- [10] Joshi, A. A. & Aziz, R. M. (2024). 基于新型适应度函数的基因表达数据两阶段布谷鸟搜索基因选择与癌症疾病深度学习分类方法。 *Multimedia Tools and Applications*, 83(28), 71721–71752.
- [11] Ergul Aydin, Z. & Ozturk, Z. K. (2024). 存在缺失数据时医疗预测模型的基于过滤的特征选择方法。 *Multimedia Tools and Applications*, 83(8), 24187–24216.
- [12] Al-Jamimi, H. A., Ayad, S. & Kheir, A. E. “集成先进技术：用于准确肺癌预测的RFE-SVM特征工程和Nelder-Mead优化XGBoost。” IEEE Access (2025).
- [13] Vatankhah, M. & Momenzadeh, M. (2024). 用于微阵列癌症分类中最具信息特征选择的自正则Lasso。 *Multimedia Tools and Applications*, 83(2), 5955–5970.
- [14] Gu, Y., Su, S., Wang, X., Miao, J., Ni, X., Li, A., Liang, Y. & Zeng, X. (2025). 术后胃癌患者肌肉减少症预测中XGBoost与逻辑回归的比较研究。 *Scientific Reports*, 15(1), 12808.
- [15] Ren, H., Yang, T., Yin, X., Tong, L., Shi, J., Yang, J., Zhu, Z. & Li, H. (2024). 乳腺癌幸存者高水平癌症复发恐惧预测：一种利用随机森林算法和视觉列线图的综合方法。 *European Journal of Oncology Nursing*, 70, 102579.
- [16] Sharma, A. & Mittal, S. “用于肺癌预测的各种CNN模型比较分析。”载于2024年第3届技术创新国际会议（INOCON），第1–6页。IEEE，2024。
- [17] Supriya, K. & Anitha, A. (2024). 使用粗糙计算和LSTM模型对不确定数据集进行基于分期的结直肠癌预测。 *Scientific Reports*, 14(1), 28880.
- [18] Rakhshannejad, M., Fathian, M., Shirkouhi, R., Barzinpour, F. & Gandomi, A. H. (2024). 通过先进数据驱动方法改进乳腺癌生物标志物发现和药物靶向。 *BMC bioinformatics*, 25(1), 33.
- [19] Nopour, R. (2024). 基于风险因素的卵巢癌筛查：机器学习辅助。 *BioMedical Engineering Online*, 23(1), 18.
- [20] Reddy, A. (2024). 乳腺癌中的人工智能与机器学习：通过数据驱动模型推进精准医疗。 *International Journal of Innovation in Engineering*, 4(4), 37–42.
- [21] Froicu, E.-M., Oniciuc, O.-M., Afrășanie, V.-A., Marinca, M.-V., Riondino, S., Dumitrescu, E. A., Alexa-Stratatut, T., Radu, I., Miron, L., Bacaouni, G. 等 (2024). 转移性结直肠癌化疗引起毒性预测中人工智能的应用：面向个体化肿瘤学的数据驱动方法。 *Diagnostics*, 14(18), 2704. https://doi.org/10.3390/diagnostics14182074.
- [22] Qasrawi, R., Daraghmeh, O., Qdaih, I., Thwib, S., Polo, S. V., Owienah, H., Al-Halawa, D. A. & Atari, S. (2024). 用于推进乳腺癌检测和分类临床应用的混合集成深度学习模型。 *Heliyon*, 10(19).
- [23] Nanglia, S., Ahmad, M., Khan, F. A. & Jhanjhi, N. Z. (2022). 用于乳腺癌预测的增强预测异构集成模型。 *Biomedical Signal Processing and Control*, 72, 103279.
- [24] Zerououai, H., Idri, A. & Alaoui, O. E. (2023). 使用深度混合异质集成进行乳腺癌组织学分类的新方法。 *Data Technologies and Applications*, 57(2), 245–278.
- [25] Wang, X., Ahmad, I., Javeed, D., Zaidi, S. A., Alotaibi, F. M., Ghoneim, M. E., Daradek, Y. I., Asghar, J. & Eldin, E. T. (2022). 乳腺癌检测的智能混合深度学习模型。 *Electronics*, 11(17), 2767.
- [26] Sharmin, S., Ahamad, T., Talukder, M. A. & Ghose, P. (2023). 乳腺癌检测的混合可靠深度特征提取和基于集成的机器学习方法。 *IEEE Access*, 11, 87694–87708. doi: 10.1109/ACCESS.2023.3304628.
- [27] Li, Y., Yu, X. & Koudas, N. (2021). 用于改进机器学习模型的数据获取。 arXiv预印本 arXiv:2105.14107.
- [28] Aljrees, T. (2024). 使用KNN插补和多模型集成学习改善宫颈癌预测。 *Plos one*, 19(1), e0295632.
- [29] Kalam, R. & Thomas, C. (2024). 使用基于熵的模糊C-Means聚类和RMCNN对乳腺X线图像中的乳腺癌进行检测和分类。 *Multimedia Tools and Applications*, 83(24), 64853–64878.
- [30] Chhillar, I. & Singh, A. (2024). 一种基于特征工程的机器学习技术，用于从病理图像中检测和分类肺癌和结肠癌。 *Medical & Biological Engineering & Computing*, 62(3), 913–924.

