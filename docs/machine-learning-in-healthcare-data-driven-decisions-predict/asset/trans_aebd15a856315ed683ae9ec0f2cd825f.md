
## 表 1：调谐参数。

| 迭代 | 学习率 | 批次大小 | 丢弃率 | 隐藏单元数 (BiLSTM) | GNN 层数 | 注意力头数 | 验证 AUROC |
|---|---|---|---|---|---|---|---|
| 1 | 0.001 | 64 | 0.5 | 128 | 2 | 4 | 88.6% |
| 2 | 0.0007 | 64 | 0.4 | 128 | 2 | 4 | 90.1% |
| 3 | 0.0005 | 64 | 0.3 | 256 | 3 | 4 | 91.5% |
| 4 | 0.0003 | 128 | 0.3 | 256 | 3 | 8 | 93.2% |
| 5 | 0.0002 | 128 | 0.2 | 256 | 4 | 8 | 94.3% |
| 6 | 0.00015 | 128 | 0.2 | 256 | 4 | 8 | 94.1% |

![](img/106ef0dba620d314f9842503e8ef40c8_290_0.png)

图 2：准确性分析。

更全面、可解释且具有普遍适用性的医疗保健分析方法的需求，是开发 HAD-Net 架构的动机。当前模型中，结构化数据（如 EHR）与非结构化数据（如影像数据）之间的互补性往往未被充分利用，导致临床见解支离破碎。HAD-Net 通过采用多模态学习机制来解决这一问题，该机制涉及自注意力机制，以模态之间建模高级依赖关系，利用 GNN 进行患者之间的关系学习，并利用 BiLSTM 建模 EHR 随时间的动态变化。HAD-Net 具有强健性和可信度，因为贝叶斯调谐的自适应学习调度器提高了优化效率，而 SHAP 确保了对医疗专业人员而言预测结果可解释。

实际部署因数据异质性、缺失值以及影像和 EHR 时间戳之间的不一致而变得复杂。拥有如此深层且多模态的网络需要强大的基础设施和高效的训练方法，因为其计算成本高昂。此外，尽管 SHAP 促进了透明度，但仍需要临床经验来确认特征相关性的解释。由于模型在数据分布不一致的不同机构之间的泛化能力仍然存在问题，因此需要强大的域自适应方法。

未来工作将着重于扩展模型处理日益复杂的数据源（如可穿戴传感器数据流、基因组学和通过自然语言处理的临床记录）的能力。联邦学习可以在不集中敏感患者信息的情况下增强数据隐私，并实现跨机构模型泛化。此外，将探索在临床工作流程中部署该系统并集成实时推理功能，强调临床医生反馈回路和法规遵循。遵循这一发展轨迹，HAD-Net 将从一个研究原型发展成为一个可部署且可扩展的决策支持系统。

## 5 结论

拟议的 HAD-Net（混合注意力驱动网络）模型很好地解决了当前和传统机器学习范式在医疗保健领域的主要局限性，即泛化能力差、缺乏可解释性和多模态融合不佳。HAD-Net 通过融合结构化 EHR 信息与非结构化胸部 X 射线图像，利用图神经网络、BiLSTM 层和自注意力机制的综合集成，为风险分层和早期诊断任务提供了一种可扩展且强健的解决方案。通过引入贝叶斯调谐的自适应学习调度器，确保了动态收敛；而通过使用 SHAP，鼓励了可解释性和透明度，SHAP 提供了具有临床实用性的解释。在合并的 NIH ChestX-ray14 和 MIMIC-III 数据集上的实验验证结果表明，HAD-Net 在准确率、F1 分数和 AUROC 方面优于最先进的模型。此外，该模型在真实循证医疗保健中的实用性体现在其能够识别具有临床意义的生物标志物。本研究通过展示智能多模态系统实现主动且个性化的患者护理的变革能力，填补了最先进的人工智能与强健临床应用之间的差距。

## 参考文献

- [1] Badawy, M., Ramadan, N. & Hefny, H. A. (2023). 使用机器学习和深度学习技术进行医疗保健预测分析：一项综述. Journal of Electrical Systems and Information Technology, 10(1), 40.
- [2] Rehan, H. (2023). 人工智能与机器学习：机器学习对医疗保健预测分析的影响. Innovative Computer Sciences Journal, 9(1), 1–20.
- [3] Venkatesh, R., Balasubramanian, C. & Kaliappan, M. (2019). 使用机器学习技术开发疾病预测的大数据预测分析模型. Journal of medical systems, 43(8), 272.
- [4] Istepanian, R. S. & Al-Anzi, T. (2018). m-Health 2.0：移动健康、机器学习和大数据分析的新视角. Methods, 151, 34–40.
- [5] Nithya, B. & Ilango, V. (2017, June). 使用机器学习工具和技术进行医疗保健预测分析. 在 2017 智能计算与控制系统国际会议 (ICICCS) (第 492–499 页). IEEE.
- [6] Rahim, M. J., Afroz, A. & Akinola, O. (2025). 医疗保健预测分析：大数据，更好的决策. International Journal of Scientific Research and Modern Technology, 4(1), 1–21.
- [7] Johnston, S. S., Morton, J. M., Kalsekar, I., Ammann, E. M., Hsiao, C. W. & Reps, J. (2019). 将机器学习应用于现实世界医疗保健数据进行预测分析：减肥手术中的应用示例. Value in health, 22(5), 580–586.
- [8] Rahman, A., Karmakar, M. & Debnath, P. (2023). 医疗保健预测分析：通过机器学习改善美国的患者结局. Revista de Inteligencia Artificial en Medicina, 14(1), 595–624.
- [9] Nerkar, P. M., Dhaware, B. U. & Liyakat, K. S. S. (2023). 基于心脏医疗保健系统 (HHS) 使用机器学习的预测数据分析框架. Journal of Advanced Zoology, 44(2).
- [10] Weng, W. H. (2020). 临床预测分析的机器学习. Leveraging data science for global health, 199–217.
- [11] Muniasamy, A., Tabassum, S., Hussain, M. A., Sultana, H., Muniasamy, V. & Bhatnagar, R. (2020). 医疗保健预测分析的深度学习. 在 The International Conference on Advanced Machine Learning Technologies and Applications (AMLTA2019) 4 (第 32–42 页). Springer International Publishing.
- [12] Saini, M. K. & Singh, J. (2021). 大数据分析与机器学习：个性化、预测性健康并提升精准医学研究. International Journal of Management IT and Engineering, 11(12), 47–56.
- [13] Islam, M. S., Hasan, M. M., Wang, X., Germack, H. D. & Noor-E-Alam, M. (2018, May). 医疗保健分析的系统综述：数据挖掘的应用与理论视角. 在 Healthcare (第 54 页). Vol. 6, 2, MDPI.
- [14] Gates, J. D., Yuliani, Y. & Pangilinan, G. A. (2024). 医疗保健预测洞察的大数据分析. International Transactions on Artificial Intelligence, 3(1), 54–63.
- [15] Kamble, S. S., Gunasekaran, A., Goswami, M. & Manda, J. (2019). 医疗保健管理中大数据分析应用的系统视角. International Journal of Healthcare Management.
- [16] Rahman, M. H., Uddinb, M. K. S., Hossanc, K. M. R. & Hossaind, M. D. (2024). 预测分析在早期疾病检测中的作用：预防性医疗的数据驱动方法. Journal of the Learning Sciences, 32(2), 2024.
- [17] Sangeetha, S. K. B., Immanuel, R. R., Mathivanan, S. K., Cho, J. & Eswaramoorthy, S. V. (2024). 多模态情感计算方法的实证分析，以推动人工智能在医疗保健中的情感智能. IEEE Access.
- [18] Begum, T. (2023). 机器学习和深度学习的预测分析. 在 Handbook of big data research methods (第 148–164 页). Edward Elgar Publishing.
- [19] Trivedi, N. K. (2023, July). 使用机器学习进行医疗保健预测分析. 在 2023 第 14 届计算通信与网络技术国际会议 (ICCCNT) (第 1–5 页). IEEE.
- [20] Jain, V. & Chatterjee, J. M. (2020). 具有医疗保健视角的机器学习 (第 1–415 页). Cham: Springer.
- [21] Khan, Z. F. & Alotaibi, S. R. (2020). 人工智能和大数据分析在 m-Health 中的应用：医疗保健系统视角. Journal of healthcare engineering, 2020(1), 8894694.
- [22] Kumari, J., Kumar, E. & Kumar, D. (2023). 结构化分析以研究机器学习和深度学习在医疗保健领域与大数据分析中的作用. Archives of Computational Methods in Engineering, 30(6), 3673–3701.
- [23] Sangeetha, S. K. B., Dhaya, R., Shah, D. T., Dhanandharan, R. & Reddy, K. P. S. (2021, February). 数字病理学中机器学习框架的实证分析. 在 Journal of physics: Conference series (p. 012031). Vol. 1767, 1, IOP Publishing.
- [24] Saranya, P. & Asha, P. (2019, November). 医疗保健中大数据分析调查. 在 2019 智能系统与创新技术国际会议 (ICSSIT) (第 46–51 页). IEEE.
