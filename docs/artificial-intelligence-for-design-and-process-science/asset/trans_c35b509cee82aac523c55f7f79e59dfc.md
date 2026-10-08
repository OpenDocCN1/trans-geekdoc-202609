
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

## 参考文献

- 1. Devlin, J., Chang, M. W., Lee, K., & Toutanova, K. BERT: Pre-training of deep bidirectional transformers for language understanding. In: Proceedings of the 2019 conference of the North American chapter of the association for computational linguistics: Human language technologies, Volume 1 (Long and Short Papers), (pp. 4171–4186). Association for Computational Linguistics, Minnesota (Jun 2019). https://doi.org/10.18653/v1/N119-1423.
- 2. Peterson, M. E., Meuson, N., Iyer, Gardner, M., Clark, C., Lee, K., Zlemoyer, L. Deep contextualized representations. In: Proceedings of the 2018 conference of the North American chapter of the association for computational linguistics: Human language technologies, Volume 1 (Long Papers) (pp. 2227–2237). Association for Computational Linguistics, New Orleans, Louisiana (Jun 2018). https://doi.org/10.18653/v1/N118-002. https://aclanthology.org/N118-002.
- 3. Sap, M., Shaw, V., Bourseau, A., Choi, Y., Roth, D. Common-sense reasoning for natural language processing. In: Proceedings of the 58th annual meeting of the association for computational linguistics: Tutorials (pp. 27–33). Association for Computational Linguistics, Online (Jul 2020). https://doi.org/10.18653/v1/2020-ac-tutorials-7. https://aclanthology.org/2020-ac-tutorials-7.
