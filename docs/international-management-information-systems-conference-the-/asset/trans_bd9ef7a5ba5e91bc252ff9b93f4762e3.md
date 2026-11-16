
利用多种决策树，从随机选取的数据子集中构建一棵森林。接着，算法汇总决策树的投票结果，以判断是否预测为 COVID-19。

## 3. 结果

我们研究了 CpG 岛特征在 COVID-19 分类中的有效性。在使用公式 1 和公式 2 提取 CpG 岛特征后，利用支持向量机、朴素贝叶斯、k 最近邻和随机森林等机器学习方法对其进行分类。采用 Weka 3.8.4 工具 [20] 执行机器学习分类。数值结果是在运行 Linux 操作系统、配备 16 GB 内存和 2.7 GHz 处理器的计算机上获得的。每个分类器的性能按精确率、召回率、F 值和准确率进行评估。采用了十倍交叉验证策略，结果如表 2 所示。此外，图 2 展示了精确率、召回率、F 值和准确率的数值。最大分类准确率为 93%，通过使用基于 CpG 岛特征的随机森林获得。本研究中采用所提特征的机器学习模型对 COVID-19 序列进行了高准确率预测。这凸显了所提方法的高效性。

表 2. COVID-19 分类结果（10 倍交叉验证）。

| 方法 | 精确率 | 召回率 | F 值 | 准确率 |
|---|---|---|---|---|
| 支持向量机 | 0.869 | 0.873 | 0.868 | 0.87 |
| 朴素贝叶斯 | 0.882 | 0.885 | 0.879 | 0.88 |
| K 最近邻 | 0.927 | 0.926 | 0.926 | 0.92 |
| 随机森林 | 0.93 | 0.93 | 0.93 | 0.93 |

![](img/1c57d3e71276f21d1972f8c8d85cab50_3_0.png)

图 2. 机器学习方法评价。

## 4. 结论

在本研究中，我们利用四种机器学习方法——支持向量机、朴素贝叶斯、k 最近邻和随机森林——从人类基因组序列中对 COVID-19 病例进行了分类。实验结果表明，采用基于基因组特征的 k 最近邻和随机森林方法取得了显著效果，准确率分别达到 92% 和 93%。在今后的研究中，我们将对比来自人类的 COVID-19 序列与其他类型冠状病毒序列（如来源于小鼠的序列），并提出一种基于相似性的特征。

**资助：** 本研究未获得外部资助。

**机构审查委员会声明：** 本研究使用公开可用的数据集开展，并依据《赫尔辛基宣言》的指导方针进行，经中国国家生物信息中心（中国）批准。

**知情同意声明：** 本研究中涉及的所有受试者均已知情同意，即公开可用的数据集已经生成。

**数据可用性声明：** 本研究分析了公开可用的数据集。该数据可在此处查找 (2019nCoVR) https://bigd.big.ac.cn/ncov/?lang=en

**利益冲突：** 作者声明不存在利益冲突。

## References

- 1. Sohrabi, C.; Alsafi, Z.; O'Neill, N.; Khan, M.; Kerwan, A.; Al-Jabir, A.; Iosifidis, C.; Agha, R. World Health Organization declares global emergency: A review of the 2019 novel coronavirus (COVID-19). *Int. J. Surg.* **2020**, *76*, 71–76. doi:10.1016/j.ijsu.2020.02.034.
- 2. Cui, J.; Li, F.; Shi, Z.L. Origin and evolution of pathogenic coronaviruses. *Nat. Rev. Microbiol.* **2019**, *17*, 181–192. doi:10.1038/s41579-018-0118-9.
- 3. Guan, Y.; Zheng, B.J.; He, Y.Q.; Liu, X.L.; Zhuang, Z.X.; Cheung, C.L.; Luo, S.W.; Li, P.H.; Zhang, L.J.; Guan, Y.J.; et al. Isolation and Characterization of Viruses Related to the SARS Coronavirus from Animals in Southern China. *Science* **2003**, *302*, 276–278, doi:10.1126/science.1087139.
- 4. Altschul, S.F.; Gish, W.; Miller, W.; Myers, E.W.; Lipman, D.J. Basic local alignment search tool. *J. Mol. Biol.* **1990**, *215*, 403–410. doi:10.1016/S0022-2836(05)80360-2.
- 5. Pearson, W.R. Rapid and Sensitive Sequence Comparison with FASTP and FASTA. *Methods Enzymol.* **1990**, *183*, 63–98. doi:10.1016/0076-6879(90)83007-V.
- 6. Pinello, L.; Lo Bosco, G.; Yuan, G.C. Applications of alignment-free methods in epigenomics. *Brief. Bioinform.* **2013**, *15*, 419–430. doi:10.1093/bib/bbt078.
- 7. Vinga, S.; Almeida, J. Alignment-free sequence comparison—A review. *Bioinformatics* **2003**, *19*, 513–523. doi:10.1093/bioinformatics/btg005.
- 8. Kari, L.; Hill, K.A.; Sayem, A.S.; Karamichalis, R.; Bryans, N.; Davis, K.; Dattani, N.S. Mapping the Space of Genomic Signatures. *PLoS ONE* **2015**, *10*, 1–17. doi:10.1371/journal.pone.0119815.
- 9. Karamichalis, R.; Kari, L.; Konstantinidis, S.; Kopecki, S. An investigation into inter- and intragenomic variations of graphic genomic signatures. *BMC Bioinform.* **2015**, *16*. doi:10.1186/s12859-015-0655-4.
- 10. Solis-Reyes, S.; Avino, M.; Poon, A.; Kari, L. An open-source k-mer based machine learning tool for fast and accurate subtyping of HIV-1 genomes. *PLoS ONE* **2018**, *13*, 1–21. doi:10.1371/journal.pone.0206409.
- 11. Randhawa, G.; Hill, K.; Kari, L. ML-DSP: Machine Learning with Digital Signal Processing for ultrafast, accurate, and scalable genome classification at all taxonomic levels. *BMC Genom.* **2019**, doi:10.1186/s12864-019-5571-y.
- 12. Randhawa, G.S.; Soltykial, M.P.M.; El Roz, H.; de Souza, C.P.E.; Hill, K.A.; Kari, L. Machine learning using intrinsic genomic signatures for rapid classification of novel pathogens: COVID-19 case study. *PLoS ONE* **2020**, *15*, 1–24. doi:10.1371/journal.pone.0232391.
- 13. Wang, Y.; Mao, J.M.; Wang, G.D.; Luo, Z.P.; Yang, L.; Yao, Q.; Chen, K.P. Human SARS-CoV-2 has evolved to reduce CG dinucleotide in its open reading frames. *Sci. Rep.* **2020**, *10*, 5165–5184.
- 14. Zhao, W.-M.; Song, S.-H.; Chen, M.-L.; Zou, D.; Ma, L.-N.; Ma, Y.-K.; Li, R.-J.; Hao, L.-L.; Li, C.-P.; Tian, D.-M.; et al. The 2019 novel coronavirus resource. *Yi Chuan* **2020**, *42*, 212–221. doi:10.16288/j.yczz.20-030.
- 15. Dinka, H.; Milkesal, A. Unfolding SARS-CoV-2 viral genome to understand its gene expression regulation. *Infect Genet Evol.* **2020**, *84*. doi:10.1016/j.meegid.2020.104386.
- 16. Ponger, L.; Mouchiroud, D. CpGProD: Identifying CpG islands associated with transcription start sites in large genomic mammalian sequences. *Bioinformatics* **2002**, *18*, 631–633. doi:10.1093/bioinformatics/18.4.631.
- 17. Arslan, H. A New Promoter Prediction Method using Support Vector Machines. In Proceedings of the 2019 27th Signal Processing and Communications Applications Conference (SIU), Sivas, Turkey, 24–26 April 2019; pp. 1–4. doi:10.1109/SIU.2019.8806549.
- 18. Zhang, W.; Zhao, D.; Chai, Z.; Yang, L.T.; Liu, X.; Gong, F.; Yang, S. Deep Learning and SVM-Based Emotion Recognition from Chinese Speech for Smart Affective Services. *Softw. Pract. Exper.* **2017**, *47*, 1127–1138.
- 19. Brown, I.; Mues, C. An experimental comparison of classification algorithms for imbalanced credit scoring data sets. *Expert Syst. Appl.* **2012**, *39*, 3446–3453.
- 20. Frank, E.; Hall, M.A.; Witten, I.H. The WEKA Workbench. In *Online Appendix for “Data Mining: Practical Machine Learning Tools and Techniques”*, 4th ed.; Morgan Kaufmann: Burlington, MA, USA, 2016.
