

表 3：临床实用性模拟结果。

| 指标 | Transformer | GAT-only | PATHTRACK-RL |
| :--- | :--- | :--- | :--- |
| ICU 再入院率（%） | 19.6 | 17.3 | 15.2 |
| 平均住院天数（天） | 6.4 | 6.1 | 5.6 |
| SAPS-II 风险降低（%） | 4.8 | 6.1 | 7.4 |
| 关键干预时间（小时） | 3.8 | 3.1 | 2.4 |

PATHTRACK-RL 模型已通过实验结果得到验证。该模型利用深度变分编码器、支持强化学习的策略优化以及基于图的注意力模型，在处方和预测任务中实现更高的准确性、可解释性和实用性。在早期风险检测、治疗建议准确性及后续医疗结局方面，它始终优于基线模型。通过使用两个大型数据集（eICU 和 MIMIC-IV）对推断结果进行交叉验证，提高了研究结果的泛化能力。PATHTRACK-RL 的灵活性和稳健性使其成为一个前沿的 AI 驱动型临床决策支持系统，能够大规模推动数据驱动、高质量且个性化的医疗服务。

## 5 结论

本研究介绍了基于深度学习的临床决策支持系统 PATHTRACK-RL。该系统专门用于处理现实世界医疗数据中存在的稀疏性、异质性和关系复杂性。PATHTRACK-RL 通过结合堆叠变分自编码器（VAEs）来处理高维多模态输入、使用图注意力网络（GATs）来建模患者特定交互，以及采用基于强化学习的策略优化器来定制治疗路径，从而连接处方决策制定与预测分析。该模型在两个大型危重症数据集（MIMIC-IV 和 eICU 协作研究数据库）上经过充分测试后，在多项评估指标上优于强健的基线模型。它将真实世界患者结局（例如降低 ICU 再入院率）提升了 11.2%，同时在早期风险检测中达到 94.1% 的准确率，在治疗建议中达到 91.8% 的 Top-3 精确率。这些发现支持 PATHTRACK-RL 能够可靠地预测重要事件，并提供切实、深思熟虑的建议，以改善临床流程和结果。PATHTRACK-RL 将可解释性和模块化置于性能之上，这使其能够适应各种医疗环境。它通过结合关系建模、时序动态和序贯决策流程，为下一代 AI 辅助个性化医疗创建了一个可扩展的蓝图。未来的研究可以扩展此框架，以管理实时数据流、纳入影像和基因组模式，并在实际临床环境中实施该系统以进行潜在验证。

## References

- [1] Cancela, J., Charlafti, I., Colloud, S. & Wu, C. (2021). 个性化医疗时代的数字健康：将研究和患者护理提升到新水平的机遇与挑战。*Digital health*, 7–31.
- [2] Pejovic, V., Mehrortra, A. & Musolesi, M. (2016). 预期移动数字健康：迈向个性化主动疗法和预防策略。载于 *Anticipation and Medicine*（第 253–267 页）。Cham: Springer International Publishing.
- [3] Grant, P. (2024). 主动护理。载于 *The Virtual Hospital*（第 87–107 页）。Cham: Springer Nature Switzerland.
- [4] Lewy, H., Barkan, R. & Sela, T. (2019). 个性化健康系统——现实环境中研究开发与实施的过去、现在与未来。*Frontiers in medicine*, 6, 149.
- [5] Sittig, S., Iyengar, M. S., Florez-Arango, J. F. & Chaudhry, B. M. (2024). 创建、维持和评估个性化数字健康系统。载于 *2024 IEEE International Conference on Big Data (Big Data)*（第 5884–5890 页）。IEEE.
- [6] Wu, C. (2020). 个性化医疗时代的数字健康：将研究和患者护理提升到新水平的机遇与挑战。*Digital health: mobile and wearable devices for participatory health applications*, 7.
- [7] Maeckelberghe, E., Zdunek, K., Marceglia, S., Farsides, B. & Rigby, M. (2023). 个性化数字健康的伦理挑战。*Frontiers in medicine*, 10, 1123863.
- [8] Albulushi, A., Al Kindi, D. I., Moawwad, N., Kamel, A. M., Khan, A., Mustafa, M. A. & Al Kalbani, A. (2024). 数字健康技术在增强心力衰竭管理中患者及照护者参与方面的应用：机遇与挑战。*International journal of cardiology*, 132116.
- [9] Abatal, A., Mzili, M., Mzili, T., Cherrat, K., Yassine, A. & Abualigah, L. (2024). 智能互联医疗系统：整合物联网和大数据以实现个性化患者护理。*International Journal of Online & Biomedical Engineering*, 20(11).
- [10] Dinsmore, J., Hannigan, C., Smith, S., Murphy, E., Kuiper, J. M., O'Byrne, E. . . . Doyle, J. (2021). 用于整合与主动以患者为中心的多病共存自我管理和护理（ProACT）的数字健康平台：行动研究概念验证试验方案。*JMIR research protocols*, 10(12), e22125.
- [11] Sangeetha, S. K. B., Dhaya, R., Shah, D. T., Dhanandharan, R. & Reddy, K. P. S. (2021, 2月). 医学数字病理学机器学习框架的实证分析。载于 *Journal of physics: Conference series*, Vol. 1767, 1, 012031. IOP Publishing.
- [12] Vallée, A. (2023). 医疗保健系统的数字孪生。*Frontiers in Digital Health*, 5, 1253050.
- [13] Ahmadi, A. (2024). 数字健康转型：利用 AI 进行监测和疾病管理。*International Journal of BioLife Sciences (IJBLS)*, 3(1), 10–24.
- [14] Bhavnani, S. P., Parakh, K., Atreja, A., Druz, R., Graham, G. N., Hayek, S. S. . . . Shah, B. R. (2017). 2017 年创新路线图——ACC 关于数字健康、大数据和精准健康时代医疗保健转型的健康政策声明：美国心脏病学会健康政策声明和护理系统工作组报告。*Journal of the American College of Cardiology*, 70(21), 2696–2718.
- [15] Aminabee, S. (2024). 医疗保健和以患者为中心的护理的未来：数字创新、趋势和预测。载于 *Emerging Technologies for Health Literacy and Medical Practice*（第 240–262 页）。IGI Global Scientific Publishing.
- [16] Canaud, B., Davenport, A., Leray-Moragues, H., Morena-Carrere, M., Cristol, J. P., Koman, J. & Kotanko, P. (2024). 数字健康支持：增强透析患者护理和赋能患者的现状与未来发展。Toxins, 16(5), 211.
- [17] Sangeetha, S. K. B., Immanuel, R. R., Mathivanan, S. K., Cho, J. & Eswaramoorthy, S. V. (2024). 多模态情感计算方法的实证分析：用于推动医疗保健人工智能中的情感智能。IEEE Access.
- [18] Rashid, Z., Ahmed, H., Nadeem, N., Zafar, S. B. & Yousaf, M. Z. (2025). 数字健康范式：AI 应用与变革性趋势。Neural Computing and Applications, 1–32.
- [19] Li, J., Tian, Y. & Zhou, T. (2024). 主动健康系统。载于 Healthcare Information Systems: Progress, Challenges and Future Directions (pp. 295–310). Singapore: Springer Nature Singapore.
- [20] Ibeh, C. V., Elufioye, O. A., Olorusogo, T., Asuzu, O. F., Nduubuisi, N. L. & Daraojimba, A. I. (2024). 医疗保健中的数据分析：以患者为中心方法和医疗保健提供的综述。World Journal of Advanced Research and Reviews, 21(02), 1750–1760.
- [21] Paramasivan, A. (2020). 演进的以患者为中心的护理：AI 和自然语言处理如何重塑数字健康记录。International Journal of Innovative Research and Creative Technology, 6(4), 1–11.

## 基于机器学习和数据分析视角的预测医疗保健混合注意力驱动网络

摘要：机器学习（ML）与医疗保健分析的整合，为风险评估、早期诊断和个性化治疗规划打开了前所未有的新大门。随着医学影像、电子健康记录（EHRs）和生理信号的不断扩展，当今使用数据驱动方法来发现有意义的洞察既是可能的，也是迫在必行的。尽管取得了令人瞩目的进步，但当前基于 ML 的框架仍存在三个关键问题：(i) 由于数据不足或偏差，跨人群泛化能力有限；(ii) 黑盒模型的可解释性不足，削弱了临床信任；以及 (iii) 数据源多模态整合不足，导致决策孤立。为克服这些问题，我们提出了 HAD-Net（混合注意力驱动网络），这是一种多模态深度学习架构，通过自注意力机制、图神经网络（GNNs）和双向长短期记忆网络（BiLSTM）的综合优势，将结构化 EHR 数据与非结构化影像模态相结合。采用了贝叶斯调优的自适应学习调度器，以自适应地调整模型以实现更好的收敛，并添加了 SHAP（SHapley Additive exPlanations）以提供可理解的风险预测。使用 NIH ChestX-ray14 数据集和 MIMIC-III 临床数据库来测试所提的 HAD-Net。HAD-Net 的 AUROC 为 94.3%，准确率为 91.7%，F1 分数为 92.1%，分别比传统机器学习模型（随机森林和逻辑回归）和新型深度模型（CNN-LSTM 和基于 Transformer 的模型）中表现最好的基线模型高出 9.5% 和 12.4%。此外，添加 SHAP 解释增强了模型的可解释性，并实现了临床相关生物标志物（如异常 PaO2/FiO2 比值、升高的肌钙蛋白和放射学浸润）的生物标志物发现。这些发现验证了 HAD-Net 在有效多模态分析方面的适用性，以提供个性化和预测性护理，从而实现主动临床决策并最大限度地减少可避免的不良后果。

关键词：混合注意力驱动网络，多模态学习，电子健康记录，医学影像，可解释性，预测医疗保健

