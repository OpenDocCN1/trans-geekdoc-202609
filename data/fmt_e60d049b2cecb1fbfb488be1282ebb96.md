
## 参数配置

| 参数 | 说明 | 默认值 |
| :--- | :--- | :--- |
| Threads used in Spark | It is the number of map-reduce function threads. | 10 |
| Phrase Frequency Count | Minimum threshold value to be considered for phrase extraction. | 50 |
| Vector Length | The length of vector for representation of word or phrase. | 150 |
| Context Window Size | Number of words to be considered on both side of the target word/phrase. | 10 (5 on each side) |
| Epoch Count | It is the number of allowed iterations to be performed for training the model. | 10 |

## 16.5 结果

本研究的目标是学习短语嵌入，而非词嵌入。本节描述结果，即从 TREC 数据集中使用分块技术和 Spark 架构提取的短语。后半部分展示了拟议短语嵌入模型生成的样本短语和词嵌入。

### 16.5.1 短语提取

表 16.2 显示从语料库中提取的示例短语。如表所示，所提方法提取了二元组、三元组，在某些情况下还有更高阶的 n-gram。从表中可以看出，许多有意义的候选短语被提取。

### 16.5.2 短语嵌入

短语嵌入与词嵌入非常相似。表 16.3 和表 16.4 分别展示了所提嵌入模型对短语和词的样本结果。所提短语嵌入模型同时适用于短语和词。从表 16.4 可以看出，针对任意目标词，相似的短语会与该词一起被提取。结果显示，为每个目标短语和词都得到了高度相关且有意义的医学概念及其相似度评分。

**表 16.2** 语料库中提取的示例候选短语。

| Gene associated | Patient treated | Prospectively included |
| :--- | :--- | :--- |
| Review attempts | Measles virus | Stochastic model |
| Kidney diseases | Therapeutic agent | Cold acclimation |
| Neural basis | Iron homeostasis | Ocean acidification |
| Radiation exposure | Risk assessment | Detailed review |
| Spinal surgery | Investigate effects | Personality traits |
| Proteolytic cleavage | Specific differences | Gren syndrome |
| Major goals | Deep venous thrombosis | Cardiac arrest |
| Optimal level | Different processes | Synapse formation |
| Highest affinity | Large parts | Clinical consequences |
| Showed improvement | Large range | Differentially regulated genes |
| Functional networks | Tumor regression | Obsessive compulsive disorder |
| Rheumatoid arthritis | Warranted conclusion | Retrospectively reviewed patients |
| Clinically suspected | Chemical carcinogens | Inter xadmolecular inter xadactions |

**表 16.3** 示例短语及其嵌入的相似度评分。

| **Contextually similar to “chest pain”** | | **Contextually similar to “human_genome”** | |
| :--- | :--- | :--- | :--- |
| **Word/phrase** | **Similarity score** | **Word/phrase** | **Similarity score** |
| Palpitations | 0.700 | Genome | 0.742 |
| Syncope | 0.699 | Mouse genome | 0.710 |
| Dyspnea | 0.693 | Human genes | 0.706 |
| Epigastric pain | 0.681 | Entire genome | 0.657 |
| Haemoptysis | 0.670 | Genomes | 0.656 |
| Abdominal pain | 0.662 | Yeast genome | 0.643 |
| Dyspnoea | 0.658 | Human genomes | 0.642 |
| Palpitation | 0.647 | Coding regions | 0.621 |
| Pleuritic | 0.646 | Mouse genomes | 0.609 |
| Exertional | 0.645 | Plant genomes | 0.608 |

| **Contextually similar to “measles_virus”** | | **Contextually similar to “kidney_diseases”** | |
| :--- | :--- | :--- | :--- |
| **Word/phrase** | **Similarity score** | **Word/phrase** | **Similarity score** |
| Poliovirus | 0.661 | Renal_diseases | 0.700 |
| Virus | 0.627 | Kidney_disease | 0.624 |
| Paramyxovirus | 0.600 | Renal_disease | 0.613 |
| Edmonston | 0.590 | Nephropathies | 0.609 |
| Vaccinia_virus | 0.590 | Nephropathy | 0.547 |
| Influenza_virus | 0.587 | Kidney_failure | 0.533 |
| Viral | 0.581 | Renal | 0.528 |
| Measles_viruses | 0.568 | Glomerulopathy | 0.523 |
| Reovirus | 0.566 | Kidney | 0.516 |
| Ectromelia | 0.563 | Hyperfiltration | 0.509 |

| **Contextually similar to “spinal_surgery”** | | **Contextually similar to “cardiac_arrest”** | |
| :--- | :--- | :--- | :--- |
| **Word/phrase** | **Similarity score** | **Word/phrase** | **Similarity score** |
| Spine_surgery | 0.791 | Ohca | 0.727 |
| Spinal_fusion | 0.725 | Resuscitation | 0.718 |
| Discectomy | 0.674 | cpr | 0.689 |
| Laminoplasty | 0.661 | Asystole | 0.680 |
| Surgery | 0.642 | rosc | 0.673 |
| Microdiscectomy | 0.625 | Cardiac_arrests | 0.672 |
| Decompression | 0.609 | Pulseless | 0.650 |
| Durotomy | 0.609 | Comatose | 0.629 |
| Thyroid_surgery | 0.605 | Asystolic | 0.624 |
| Arthrodesis | 0.598 | Hypothermia | 0.616 |

**表 16.4** 示例词及其嵌入的相似度评分。

| **Contextually similar to “tachycardic”** | | **Contextually similar to “ribosomal”** | |
| :--- | :--- | :--- | :--- |
| **Word/phrase** | **Similarity score** | **Word/phrase** | **Similarity score** |
| Tachypneic | 0.719 | rrna | 0.743 |
| Pulse rate | 0.678 | Large subunit | 0.659 |
| Tachypnea | 0.646 | Small subunit | 0.651 |
| Afebrile | 0.642 | ssu | 0.626 |
| Diaphoretic | 0.640 | Ribosome | 0.614 |
| Vitals | 0.606 | lsu | 0.598 |
| Tachypnoea | 0.605 | rrna genes | 0.571 |
| Drowsy | 0.582 | rdna | 0.571 |
| Hypotensive | 0.571 | rrnas | 0.570 |
| Diaphoresis | 0.562 | Processome | 0.560 |

| **Contextually similar to “echocardiogram”** | | **Contextually similar to “dermatologist”** | |
| :--- | :--- | :--- | :--- |
| **Word/phrase** | **Similarity score** | **Word/phrase** | **Similarity score** |
| Angiogram | 0.655 | Dermatologists | 0.785 |
| Echocardiograms | 0.654 | Dermatology | 0.687 |
| Cardiomegaly | 0.655 | Dermatological | 0.600 |
| Transesophageal | 0.639 | Rheumatologist | 0.574 |
| Transthoracic | 0.619 | Acral | 0.573 |
| Murmur | 0.612 | Dermoscopy | 0.571 |
| ekg | 0.603 | Allergist | 0.568 |
| tte | 0.600 | Dermatoses | 0.560 |
| Hypokinesis | 0.579 | Skin_lesions | 0.559 |
| Physical_exam | 0.573 | Artefacta | 0.550 |

| **Contextually similar to “distress”** | | **Contextually similar to “diabetes”** | |
| :--- | :--- | :--- | :--- |
| **Word/phrase** | **Similarity score** | **Word/phrase** | **Similarity score** |
| Anxiety | 0.708 | dm | 0.796 |
| Psychological | 0.664 | Type diabetes | 0.767 |
| Depression | 0.643 | Hypertension | 0.714 |
| Psychosocial | 0.642 | Obesity | 0.706 |
| Feelings | 0.629 | cvd | 0.704 |
| Emotional | 0.599 | Dysglycemia | 0.699 |
| Hopelessness | 0.593 | Hyperglycemia | 0.688 |
| Physical stress | 0.593 | Prediabetes | 0.688 |
| Social problems | 0.590 | Diabetic | 0.685 |
| Somatization | 0.586 | Dyslipidemia | 0.677 |

## 16.6 结论

本文提出了一种基于预注解语料库的短语嵌入方法。采用基于 Spark 的 MapReduce 框架实现大规模数据集的可扩展性，并应用分块技术从中提取高频词组。采用 word2vec CBOW 模型的短语嵌入方法在同一向量空间中学习短语和词的表示，捕捉有意义的概念。这些概念在信息检索和推荐系统领域具有广泛的应用。可以广泛用于查询扩展。未来计划研究在临床决策支持领域利用短语嵌入技术进行医疗查询扩展的效果。

## 参考文献

1. Harris, Z.S., Distributional structure. *Word*, 10, 2–3, 146–162, 1954.
2. Collobert, R., Weston, J., Bottou, L., Karlen, M., Kavukcuoglu, K., Kuksa, P., Natural language processing (almost) from scratch. *J. Mach. Learn. Res*., 12, 2493–2537, 2011, Aug.
3. Grover, A. and Leskovec, J., node2vec: Scalable feature learning for networks. *Proceedings of the 22nd ACM SIGKDD international conference on Knowledge discovery and data mining*, 2016.
4. Yu, Y., Wan, X., Zhou, X., User embedding for scholarly microblog recommendation. *Proceedings of the 54th Annual Meeting of the Association for Computational Linguistics (Volume 2: Short Papers)*, 2016.
5. Mikolov, T., Chen, K., Corrado, G., Dean, J., Efficient estimation of word representations in vector space, *1st International Conference on Learning Representations (ICLR) Scottsdale*, Arizona, USA, Workshop Track Proceedings, [`arxiv.org/abs/1301.3781`](http://arxiv.org/abs/1301.3781), 2013.
6. Deerwester, S., Dumais, S.T., Furnas, G.W., Landauer, T.K. and Harshman, R., Indexing by latent semantic analysis. `JASIST`, 41, 6, 391–407, 1990.
7. Blei, D.M., Ng, A.Y., Jordan, M., II, Latent dirichlet allocation. `J. Mach. Learn. Res`., 3, 993–1022, 2003, Jan.
8. Baroni, M., Dinu, G., Kruszewski, G., Don’t count, predict! A systematic comparison of context-counting vs. context-predicting semantic vectors, in: `Proceedings of the 52nd Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)`, pp. 238–247, 2014.
9. Yin, W. and Schtze, H., An exploration of embeddings for generalized phrases, in: `Proceedings of the ACL Student Research Workshop`, pp. 41–47, 2014.
10. Yu, M. and Dredze, M., Learning composition models for phrase embeddings. `Trans. Assoc. Comput. Linguist`., 3, 227–242, 2015.
