

![](img/5368dd329bd72fa0bf97ac91d6cef632_64_0.png)

**图 3.** 使用 QALD-9-ES 西班牙语翻译与同一标注器使用 QALD-9 西班牙语翻译时，QAnswer 在 Wikidata 上的问答（QA）结果的相对变化。

QA 实验结果显示，使用 QALD-9-ES 时，Micro F1 和 Macro F1 均有所提升（图 3）。Micro F1 指标值在训练集中的增幅大于测试集，而 Macro F1 在测试集中的改善幅度大于训练集。

![](img/5368dd329bd72fa0bf97ac91d6cef632_64_1.png)

**图 4.** 使用 QALD-9-ES 西班牙语翻译与同一标注器使用 QALD-9 西班牙语翻译时，QAnswer 在 Wikidata 上 GERBIL C2KB 子实验结果的相对变化。

C2KB 子实验评估系统识别给定问题的所有相关资源的能力。图 4 显示，测试集的 Micro F1 和 Macro F1 得分均有相对提升，但训练集的得分有所下降。

![](img/5368dd329bd72fa0bf97ac91d6cef632_65_0.png)

图 5. 使用 QALD-9-ES 西班牙语翻译与同一标注器使用 QALD-9 西班牙语翻译时，QAnswer 在 Wikidata 上 GERBIL P2KB 子实验结果的相对变化。

![](img/5368dd329bd72fa0bf97ac91d6cef632_65_1.png)

图 6. 使用 QALD-9-ES 西班牙语翻译与同一标注器使用 QALD-9 西班牙语翻译时，QAnswer 在 Wikidata 上 GERBIL RE2KB 子实验结果的相对变化。

P2KB 子实验评估系统识别给定问题的所有相关属性的能力。在本例中，测试集和训练集的 Micro F1 和 Macro F1 均有所下降（图 5）。最后，RE2KB 子实验将问题预期 SPARQL 中的预期三元组与 QA 系统返回的 SPARQL 中的三元组进行比较。与 QALD-9 相比，QALD-9-ES 在该子实验中表现出更好的结果：在测试集和训练集中，Micro F1 和 Macro F1 均有所提升（参见图 6）。

## 5. 结论

KGQA 系统通过自然语言提供对知识图谱信息的访问。然而，现有 KGQA 系统所覆盖的语言数量，与世界上独立自然语言的数量并不相称。本文针对如何提供用于开发 KGQA 系统的多语言工具这一问题展开研究，以增加这些系统所覆盖的语言数量。我们重点关注西班牙语，这是一种全球超过 4.5 亿人使用的语言。

我们采用三步法开展研究。首先，我们对 QALD-9 中提供的西班牙语翻译进行了定性分析，发现其中只有 30.65% 的西班牙语翻译能够准确表达英文问题。随后，我们为存在翻译问题的问题手动生成新的译文，并在母语人士的帮助下对其进行人工审校。我们将 QALD-9-ES 与 QALD-9-plus 进行了整合。QALD-9-plus 是一个基于 QALD-9、完全由母语译文构成的数据集，因此为 QALD-9 提供了完整的高质量翻译资源，可用于开发新的数据集和 KGQA 系统。

我们使用与语言无关的定量文本分析指标，将 QALD-9-ES 西班牙语翻译与 QALD-9 中包含的原始翻译进行了比较，以确认新译文使用了更多词语、每个词的长度更长，并且每条译文中包含更多有意义的词语。唯一的不足是，译文中的独特词语数量更少。经过进一步审查，我们推测这一结果是因为原始 QALD-9 翻译中经常包含与译文无关的词语，以及一些被视为独特词语的重音符号错误。

我们还使用 GERBIL QA 框架评估了这两个数据集，即 QALD-9-ES 与 QALD-9。我们使用面向 Wikidata 的 QAnswer 标注器（在评估时唯一支持西班牙语 KGQA 的标注器）。实验结果显示，QA 结果略有改善。对于测试集，系统在识别相关关系（C2KB）方面也表现出略好的结果，而在训练集上的结果则略差。我们还发现，使用新译文后，标注器在识别给定问题的相关属性（P2KB）方面的性能有所下降，但在匹配每个问题的预期三元组（RE2KB）方面表现更好。这些混合结果体现了数据集质量以及 KGQA 系统和组件所产生的影响。

最后，我们展示了 QALD-9-ES 数据集对于开发西班牙语 KGQA 流水线的实用价值。我们预计，该新数据集将特别有益于在其流水线中使用大规模语言模型的 KGQA 系统。本研究生成的数据集已合并到 QALD-9-plus（一个完全由母语翻译构成的数据集）中。该资源还可用于将母语翻译与机器翻译生成的译文进行比较。

**致谢：** 本研究得到瑞士拉丁美洲首席之家资助的研究合作伙伴关系基金 RPG2106、DFG 项目 NFDI4DataScience 的资助（DFG 项目编号 460234259），以及联邦经济与气候行动部 CoyPu 项目的资助（项目编号 01MK21007G）。

## 参考文献

[1] Trivedi P、Maheshwari G、Dubey M、Lehmann J。《LC-QuAD：面向知识图谱复杂问答的语料库》。载于：《语义网——ISWC 2017——第 16 届国际语义网会议》，奥地利维也纳，2017 年 10 月 21—25 日。会议论文集，第 II 部分。第 10588 卷《计算机科学讲义》。Springer；2017 年。第 210—218 页。

[2] Ngomo N。《第九届基于关联数据的问答挑战赛（QALD-9）》。第 7 卷；2018 年。第 58—64 页。

[3] Perevalov A、Diefenbach D、Usbeck R、Both A。《QALD-9-plus：由母语人士翻译的面向 DBpedia 和 Wikidata 问答的多语言数据集》。载于：2022 年 IEEE 第 16 届国际语义计算会议（ICSC）；2022 年。第 229—234 页。

[4] Usbeck R、Röder M、Hoffmann M、Conrads F、Huthmann J、Ngomo AN 等。《问答系统基准测试》。Semantic Web。2019 年；10(2)：293—304。

[5] Sanguinetti M、Atzori M、Puddu N。《rewordQALD9：包含 QALD 问题替代表述的双语基准》。载于：与第 18 届国际语义系统会议（SEMANTiCS 2022）同期举办的第 18 届国际语义系统会议海报与演示专题及研讨会专题论文集，奥地利维也纳，2022 年 9 月 13—15 日。第 3235 卷 CEUR 研讨会论文集。CEUR-WS.org；2022 年。

[6] Dubey M、Banerjee D、Abdelkawi A、Lehmann J。《LC-QuAD 2.0：面向 Wikidata 和 DBpedia 复杂问答的大型数据集》。载于：《语义网——ISWC 2019——第 18 届国际语义网会议》，新西兰奥克兰，2019 年 10 月 26—30 日，会议论文集，第 II 部分。第 11779 卷《计算机科学讲义》。Springer；2019 年。第 69—78 页。

[7] Usbeck R、Röder M、Ngonga Ngomo AC、Baron C、Both A、Brümmer M 等。《GERBIL：通用实体标注器基准测试框架》。载于：第 24 届国际万维网会议论文集。WWW ’15。瑞士日内瓦共和国及州：国际万维网会议指导委员会；2015 年。第 1133—1143 页。可访问：https://doi.org/10.1145/2736277.2741626。

[8] Gusmita RH、Jalota R、Vollmers D、Reineke J、Ngomo AN、Usbeck R。《QUANT——问答基准测试策展工具》。载于：《语义系统：人工智能与知识图谱的力量——第 15 届国际会议 SEMANTiCS 2019》，德国卡尔斯鲁厄，2019 年 9 月 9—12 日，会议论文集。第 11702 卷《计算机科学讲义》。Springer；2019 年。第 343—358 页。

[9] Diefenbach D、Giménez-García J、Both A、Singh K、Maret P。《QAnswer KG：设计面向 RDF 数据的可移植问答系统》。载于：Harth A、Kirrane S、Ngonga Ngomo AC、Paulheim H、Rula A、Gentile AL 等，编。《语义网》。Cham：Springer International Publishing；2020 年。第 429—445 页。

