
最近，提出了新的数据生成技术用于缓解虚假相关性并促进泛化 [32]。该技术涉及训练数据生成器，以创建并过滤加剧相关性但在任务准确率上产生显著性能提升的数据点。此外，尽管消除偏差的数据增强减少了模型对虚假线索的依赖，但并不能消除它 [33]。词汇偏差的持续存在强调了在有效缓解 NLU 模型中虚假线索影响方面面临的持续挑战。

以模型为中心的方法：在表示层解决 LLM 的偏差问题 [34]。这包括创建对抗模型和专家积（PoE）风格的集成模型，整合有偏差的模型和鲁棒模型，其中关于数据集如何偏差的先验知识 [37] 表，当关注模型的预测特征时缓解捷径更为有效。因此，并不是去偏嵌入，而是通过根据模型如何使用嵌入来去偏，从而提高鲁棒性。在这种情况下，作者使用一个简单的词袋（BoW）模型，利用从数据集统计中提取的可泛化捷径程度测量值来软化 Softmax 计算。这阻止了模型对具有较高捷径程度（表明样本中捷径存在增加）的样本生成过度自信的预测。

## 4 深入探讨

### 4.1 语言和词汇变化

准确识别并消除 LLM 使用的特定捷径是一项重大挑战。成功应对这一挑战需要细致的策略来定位和缓解语言线索。当引入语言和词汇变化时，捷径的影响变得复杂。尽管整合了长上下文，编码词汇语义

提高自然语言理解能力的现象仍是一项持续努力 [38–40]。即使词汇重叠显著，保持一致的性能仍然是一项挑战。这引发了关于当前先进大语言模型（LLMs）在不同语言背景下的广泛适用性，以及模型在面对各种语言表达时表现出韧性和适应性性的疑问。

**前进之路** 设计能够识别和减轻各种已知和未知的捷径的稳健方法至关重要。该领域的研究重点应该是增强先进语言模型在不同上下文中的适应性。这涉及处理与语言及其变化相关的任务，同时在各种上下文和任务定义中分类不同类型的捷径。重点必须扩展到缓解与未知数据集偏差以及训练过程中特定任务知识不完整的挑战。此外，这些策略还需要扩展，以有效应对信息有限或存在未知偏差的场景。

## 4.2 分布外泛化

当在分布外的数据集上评估大语言模型时，减轻捷径的影响变得尤为具有挑战性。自然语言推理（NLI）模型对启发式方法的依赖，特别是在 MNLI [21] 等标准N数据集上进行训练和评估时，对实现稳健的推理能力构成了挑战。这一点在评估缺乏此类启发式方法的精选数据集时，性能显著下降得到了凸显，揭示了在训练分布之外实现泛化的困难性。需要为现有的各种自然语言理解（NLU）任务制定策略和数据集，以增强模型的稳健性和对多种数据分布的适应性。

**前进之路** 为了增强语言模型在分布外数据集上的整体泛化能力，制定有效的策略并专门为该目的设计的数据集至关重要。这需要集中精力定义稳健的推理能力，促进超越训练分布限制的泛化。此外，深入探索量化消除捷径对大语言模型性能影响的方法是必不可少的。鉴于包含大量表面信息的数据集的复杂性，需要更细致的方法来理解捷径减轻策略的后果。这涉及对权衡的仔细检查，以确保性能不会出现显著劣化。目标是在解决对启发式方法的依赖与面对多样化且具有挑战性的数据集时保持最佳模型性能之间取得平衡。

学习捷径：论语言模型中 NLU 具有误导性的承诺

## 4.3 消除捷径的影响

理解消除捷径对大语言模型性能影响的程度是一项关键挑战。在缺乏少数捷径的情况下，大语言模型性能的下降强调了对捷径减轻策略的后果进行细致理解的必要性。

Du 等人 [9] 还表明，模型训练由于激励训练损失而加剧了对表面线索的学习，因为当模型专注于词分布的头部（包含许多捷径特征）而非尾部时，训练损失会迅速降低。[20] 再次重申了，即由于大多数训练示例不能代表真实世界的数据分布（包括挑战性数据），最小化平均训练损失并不是一个合法的目标。他们通过修改已知数据集偏差的损失函数来解决这个问题，但认为未知数据集偏差和特定任务知识不完整的情况仍然是一个挑战。

**前进之路** 我们需要更多工作来衡量消除捷径对 NLU 任务中大语言模型性能的影响。虽然大多数先前的研究利用分布外准确率，但需要对数据集类型和样本困难程度进行系统化和定义，以理解不同的分布偏移如何影响模型行为。

## 4.4 激励训练损失的陷阱

在自然语言处理领域，理解模型训练对表面线索学习的影响至关重要。近期研究表明，模型训练加剧了对表面线索的学习 [9, 20]，因为优化过程激励了训练损失的降低，当模型优先考虑富含捷径特征的词分布头部时，损失会迅速下降。因此，最小化平均训练损失可能并不是一个合法的目标。为了解决这个问题，之前的工作建议针对已知数据集偏差修改损失函数。然而，处理未知数据集偏差和特定任务知识不完整的情况仍然是一个挑战。

**前进之路** 迫切需要重新评估大语言模型中降低训练损失相关的激励。我们必须深入替代的训练和后处理策略，优先获取有意义的语言模式，而不是整合捷径特征。这涉及到训练目标的根本性转变，以更好地符合真实数据的实际分布。为了确保大语言模型在各种语言任务中的可靠性和准确性，研究模型泛化与校准之间的相互作用至关重要。这种探索将有助于能够泛化并对数据集内挑战性样本表现出稳健性的语言模型。

## 5 结论

本章强调了语言模型中自然语言理解与捷径学习之间的相互作用。我们阐了捷径学习对 NLU 带来的扭曲，并强调了对其影响进行细致理解的必要性。有必要从识别和减轻捷径，以及完善评估方法两个方面应对捷径学习带来的挑战。忽视这些问题将危及 NLU 应用的可靠性和公平性。随着我们的进步，NLP 社区的合作对于推进我们对捷径学习的理解至关重要，促进更稳健的语言模型开发，并提高现实背景下 NLU 评估的标准。

# 参考文献

- 1. Devlin, J., Chang, M. W., Lee, K., & Toutanova, K. BERT: Pre-training of deep bidirectional transformers for language understanding. In: Proceedings of the 2019 conference of the North American chapter of the association for computational linguistics: Human language technologies, Volume 1 (Long and Short Papers), (pp. 4171–4186). Association for Computational Linguistics, Minnesota (Jun 2019). https://doi.org/10.18653/v1/N119-1423.

- 2. Peterson, M. E., Meuson, N., Iyer, Gardner, M., Clark, C., Lee, K., Zlemoyer, L. Deep contextualized representations. In: Proceedings of the 2018 conference of the North American chapter of the association for computational linguistics: Human language technologies, Volume 1 (Long Papers) (pp. 2227–2237). Association for Computational Linguistics, New Orleans, Louisiana (Jun 2018). https://doi.org/10.18653/v1/N118-002. https://aclanthology.org/N118-002.

- 3. Sap, M., Shaw, V., Bourseau, A., Choi, Y., Roth, D. Common-sense reasoning for natural language processing. In: Proceedings of the 58th annual meeting of the association for computational linguistics: Tutorials (pp. 27–33). Association for Computational Linguistics, Online (Jul 2020). https://doi.org/10.18653/v1/2020-ac-tutorials-7. https://aclanthology.org/2020-ac-tutorials-7.

# 学习捷径：论语言模型中自然语言处理的误导

Gillespie, L. E., Goel, K., Goodman, N. D., Grossman, S., Guha, N., Hashimoto, T., Terson, P., Hewitt, J., Do, D. E., Jong, J., Hsu, K., Jarcard, T., Jain, F., Jurafsky, D., Kalluri, P., Paramchetti, S., Keeling, G., Hani, F., Khattab, O., Koh, P. W., Kraass, M., Krishna, R. N., Kidiputi, K., Rumin, A., Ladakhh, F. E., Lee, M., Lee, T., Leskovec, J., I, I., Li, X. L., Li, X. T., Malik, A., Manning, C., Manning, D., Cichardi, S. P., Mitchell, E., Munnyk, Y., Zair, S., Narayan, A., Narayanan, D., Newman, B., Nie, A., Niebles, J. C., Nilforson, H., Nyarko, J. F., Ogut, G., Orr, L., Papimitriou, I., Park, J. S., Piech, C., Portale, E., Potts, C., Raghunathan, A., Reich, R., Ren, H., Rohg, F., Rhoiany, R., Ryan, J., Rea, R. C., Sagdev, D., Sagawa, S., Santhanam, H., Shih, A., Sriniv, K. M., Tamkin, A., Rao, R., Thomas, A. M., Traner, F., Wang, R. E., Wang, W., Bu, W., Wu, Y., Xie, S. M., Yasagami, M. Y., Zaharia, A. M., Zhang, Z., Zhang, X., Zhang, Y., Zheng, L., Zhou, K., & Liang, P. (2020). 基础模型的机遇与风险。arXiv: https://arxiv.org/abs/2005.14167

Merge, F., Bijie, A., Rubino, R. (2021). 769页的元评估：第99届计算语言学学会年会和第11届自然语言处理国际会议论文（卷1：长篇论文）（pp. 7297–7306）。

Niv, T., & Kao, H. Y. (2019). 预测论点的神经连接。第57届计算语言学学会年会论文。https://doi.org/10.18653/v1/IP19-1459 https://www.acl.org/annip19-1459, 会议名称：计算语言学学会。

Du, M., Manjun, Y., Jain, R., Deshpande, R., Demircourt, F., Gu, J., Sun, T., Hu, X. 识别与缓解NLP模型的捷径学习：2022年计算语言学学会北美分会会议论文：人类语言理解（pp. 915–929）。计算语言学学会，在线（2021）。https://doi.org/10.18653/v1/naacl-2021.main_77 acl://acanthology.org/naacl-2021-main_77

Moon, S., Mo, S., Lee, K., Lee, J. MASKER：用于文本分类的掩码关键词正则化。AAAI人工智能会议论文 35(13578–13586)。5月（2021）。https://doi.org/10.1609/aaai.v35.17601. https://ojs.aaai.org/index/AAAIArticle/video/17601_15

Nguyen, D., Rossel, L., Grieve, J. 论NLP中社会偏见的学习与缓解：社会政治视角。2021年计算语言学学会北美分会会议论文：人类语言理解（2021）。https://doi.org/10.18653/v1/naacl-2021.main-50 acl://acanthology.org/naacl-2021.main-50

Du, M., Fe, X., N, D., & Hu, X. 自然语言理解中大语言模型的捷径学习。ACM, 67(1), 1。

Wang, T., Sridhar, R., & Wang, G. 在提高NLP鲁棒性中识别并缓解虚假相关。计算语言学学会论文：NAACL 2022（pp. 1719–1729）。计算语言学学会，华盛顿州西雅图（2022年7月）。https://doi.org/10.18653/v1/naacl-2022.findings-naacl-130 acl://acanthology.org/2022-findings-naacl-130

Hendricks, D., Liu, X., Wallace, E., Drieschel, A., Krishna, R., Song, G. 预训练形式提高分布外鲁棒性：第58届计算语言学学会年会论文（pp. 2744–2751）。计算语言学学会，在线（2020年7月）。https://doi.org/10.18653/v1/2020.acacl-main-244 acl://acanthology.org/2020-acacl-main-244

Schauer, T., Shah, R., May, E. S., Fizzola, D., Danus, E., Barzilay, R. 去偏事实核实：在：Liang, J., Ng, V., Wang, X. (编.). 2019年自然语言处理经验方法会议和第9届自然语言处理国际会议（IJCNLP）论文（pp. 3419–3425）。计算语言学学会，香港（2019）。https://doi.org/10.18653/v1/D19-1341

16. McCoy, T., Pavlick, E., Linzen, T. 错误原因：自然语言推理中的诊断启发式方法。在第57届计算语言学学会年会论文中（2019）。https://doi.org/10.18653/v1/P19-1334. aclanthology.org/P19-1334

17. Tu, L., Lwani, G., Gella, S., He, H. (2020). 使用预训练模型进行虚假相关的实证研究。计算语言学交易，8, 621–633。https://doi.org/10.1162/tacl-a_0333

18. Wang, Z., & Culaita, A. 文本分类中的虚假相关识别。在计算语言学学会论文：EMNLP（2020）中（pp. 3431–3440）。计算语言学学会，在线（2020年11月）。https://doi.org/10.18653/v1/2020-finds-emnlp.308. aclanthology.org/2020-finds-emnlp.308

19. Ren, Y., & Zhang, D. (2023). HuSLM：大语言模型的人类注意力捷径与缓解。在计算语言学会论文集发现：ACL 2023（pp. 1235–1265）。https://doi.org/10.18653/v1/2023-findings-781

20. He, H., Zhu, S., & Wang, H. (2019). 通过残差消除偏见。第2次深度学习工作讨会（DeNLP）（pp. 132–142）。https://doi.org/10.18653/v1/D19-615. aclweb.org/615

21. Williams, A., Nia, N., & Bowen, S. (2018). 2018年计算语言学学会北美分会会议：广泛覆盖的句子（pp. 1112–1222）。计算语言学学会，aclweb.org/1111

22. Miles, A., & Gella, M. (2020). 通过先验进行预测不确定性估计。神经信息系统33。

23. Thalasander, S., Chenupati, G., Bilmes, J., Mikhailak, S. (2019). Mixup提升深度神经网络的校准。神经信息系统32。Curran Associates，https://proceedings.neurips.org/paper/2019/70/36ad8b5fd42e9b48270648975cc22d

24. Guo, C., Ples, G., Sun, Y., Weller, K. (2017). 现代神经网络的校准。在第34届机器学习国际会议（pp. 1321–1330）。PMLR。

25. Jackson, N., Bousley, M., Wang, Y., Jeler, F., Tran, D. (2020). 我们如何知道语言模型知道？关于问答模型的校准。

26. Bihani, G., Ray, J. T. (2023). 使用微调进行校准估计。在：Cohen, K., Ernst, N., Buede, R., Vechnik, E. (编.). 神经信息系统2023。NIPS2023。网络与系统丛录，卷751。https://doi.org/10.1007/978-3-031-46778-3_9
