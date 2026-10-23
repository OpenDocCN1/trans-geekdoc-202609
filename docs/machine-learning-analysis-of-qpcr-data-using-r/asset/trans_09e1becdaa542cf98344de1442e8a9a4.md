

## 结论

本工作展示的数据表明，*maxRatio*/SVM 过滤法相比拟合点法具有多项优势：

- *适应性。* 该模型能够适应所评估的数据集，自动纳入实验方法的特性（抑制作用、化学调整等）。
- *灵活性。* 可根据操作员的需求定义类别数量。
- *可扩展性。* 该模型可使用不断增多的数据点进行训练，从而提高方法的准确性。
- *差异性。* 将分类与拟合点法相结合，有助于识别在验证阶段需要操作员充分关注的反应。
- *独立性。* 本工作及先前工作（Marongiu, 2020）的论点是，即使在没有拟合点法预分类的情况下，SVM 提供的分类也能精确定位具有问题扩增曲线的反应。
- *可移植性。* 由于 SVM 分析可以使用高级计算机语言执行——在本例中为 *R*，但其他平台（尤其是 *Python* 或 *Julia*）也可以执行机器学习程序——本工作所展示的分类不依赖于与热循环仪相关的专利软件。相比之下，操作员几乎从不使用*专门*的计算分析重新运行 Cq 值测定，而是依赖热循环仪软件提供的（尽管经过调整的）输出。因此，如果没有这种专利软件，就不可能分析数据。

## 参考文献

Adams, P., Vancutsem, E., Nicolaizeau, C., Servais, J.-Y., Piérard, D., François, J.-H., Schneider, T., Paxinos, E. E., Marins, E. G., Canchola, J. A., and Seguin-Devaux, C. (2019) 使用 cobas® 4800 系统定量检测 HIV-1 血浆病毒载量的 cobas® HIV-1 定量核酸试验的多中心评估. Journal of Clinical Virology, 114, 43-49.

Adams, P. S. (2006) 数据分析与报告. In Dorak, T. (Ed.), 实时 PCR. Taylor & Francis Group.

Ali, N., Rampazzo, R. d. C. P., Costa, A. D. T., and Krieger, M. A. (2017) 当前核酸提取方法及其对即时检测诊断的影响. BioMed Research International, 2017, 9306564.

Al-Soud, W. A., Jönsson, L. J., and Rådström, P. (2000) 血液中免疫球蛋白 G 作为诊断性 PCR 主要抑制剂的鉴定与表征. Journal of Clinical Microbiology, 38, 345-50.

Bailly, C., and Chaires, J. B. (1998) 序列特异性 DNA 小沟结合剂：纺锤菌素和偏端霉素类似物的设计与合成. Bioconjugate Chemistry, 9, 513-38.

van Belkum, A. (1994) 使用 PCR 对医学重要微生物进行 DNA 指纹分析. Clinical Microbiology Reviews, 7, 174-184.

Blattner, F. R., Plunkett, G. 3rd, Bloch, C. A., Perna, N. T., Burland, V., Riley, M., Collado-Vides, J., Glasner, J. D., Rode, C. K., Mayhew, G. F., Gregor, J., Davis, N. W., Kirkpatrick, H. A., Goeden, M. A., Rose, D. J., Mau, B., and Shao, Y. (1997) 大肠杆菌 K-12 全基因组序列. Science, 277, 1453-62.

Boshart, M., Gissmann, L., Ikenberg, H., Kleinheinz, A., Scheurlen, W., and zur Hausen, H. (1984) 一种新型乳头瘤病毒 DNA，存在于生殖器癌活检组织及宫颈癌细胞系中. The EMBO Journal, 3, 1151-7.

Brock, T. D., and Freeze, H. (1969) 水生栖热菌（Thermus aquaticus gen. n. and sp. n.），一种不产孢的极端嗜热菌. Journal of Bacteriology, 98, 289-97.

Brown, M. S., and Goldstein, J. L. (1992) 胆固醇的科赫法则. Cell, 71, 187-188.

Burns, H. (2007) 细菌学说：揭示隐形杀手. BMJ, 334 Suppl, s11-s11.

Bustin, S. A., Benes, V., Garson, J. A., Hellemans, J., Huggett, J., Kubista, M., Mueller, R., Nolan, T., Pfaffl, M. W., Shipley, G. L., Vandesompele, J., and Wittwer, C. T. (2009) MIQE 指南：定量实时 PCR 实验发表所需的最低信息. Clinical Chemistry, 55, 611-22.

Casanova, J.-L., and Abel, L. (2013) 传染病的遗传理论：简史与精选例证. Annual Review of Genomics and Human Genetics, 14, 215-243.

de la Chapelle, A. (2003) 微卫星不稳定性. The New England Journal of Medicine, 349, 209-10.

Chien, A., Edgar, D. B., and Trela, J. M. (1976) 来自极端嗜热菌水生栖热菌的脱氧核糖核酸聚合酶. Journal of Bacteriology, 127, 1550-7.

Cline, J., Braman, J. C., and Hogrefe, H. H. (1996) Pfu DNA 聚合酶及其他热稳定 DNA 聚合酶的 PCR 保真度. Nucleic Acids Research, 24, 3546-3551.

Collins, M. L., Irvine, B., Tyner, D., Fine, E., Zayati, C., Chang, C., Horn, T., Ahle, D., Detmer, J., Shen, L. P., Kolberg, J., Bushnell, S., Urdea, M. S., and Ho, D. D. (1997) 用于定量检测低于 100 分子/毫升核酸靶标的分支 DNA 信号扩增方法. Nucleic Acids Research, 25, 2979-84.

Cortes, C., and Vapnik, V. (1995) 支持向量网络. Machine Learning, 20, 273-297.

Csako, G. (2006) 核酸检测快速和/或高通量方法的现在与未来. International Journal of Clinical Chemistry, 363, 6-31.

Deiman, B., van Aarle, P., and Sillekens, P. (2002) 基于核酸序列的扩增（NASBA）的特性与应用. Molecular Biotechnology, 20, 163-79.

Dempster, A. P., Laird, N. M., and Rubin, D. B. (1977) 通过 EM 算法从不完全数据计算最大似然. Journal of the Royal Statistical Society: Series B (Methodological), 39, 1-22.

Döring, M., Kreer, C., Lehnen, N., Klein, F., and Pfeifer, N. (2019) 通过序列特异性特征的机器学习模拟免疫球蛋白扩增. Scientific Reports, 9, 10748.

Elliott, G. F. (1870) 细菌学说. British Medical Journal, 1, 488-489.

Evans, A. S. (1976) 病因与疾病：重访 Henle-Koch 假设. Yale Journal of Biology and Medicine, 49, 175-195.

Falkow, S. (1988) 分子科赫法则应用于微生物致病性. Reviews of Infectious Diseases, 10 Suppl 2, S274-S276.

Fardy, J. M. (2009) 诊断试验的评价. Methods in Molecular Biology, 473, 127-36.

Fore, J. J., Wiechers, I. R., and Cook-Deegan, R. (2006) 商业实践、许可和知识产权对聚合酶链反应开发与传播的影响：案例研究. Journal of Biomedical Discovery and Collaboration, 1, 7.

Fredricks, D. N., and Relman, D. A. (1996) 基于序列的微生物病原体鉴定：对科赫法则的再思考. Clinical Microbiology Reviews, 9, 18-33.

Garcion, E., Naveilhan, P., Berger, F., and Wion, D. (2009) 癌症干细胞：超越科赫法则. Cancer Letters, 278, 3-8.

Gibriel, A. A., and Adel, O. (2017) 用于基因分型检测的连接酶链反应和基于连接的扩增技术进展：检测与应用. Mutation Research, 773, 66-90.

Gradmann, C. (2014) 科学严谨精神：二十世纪医学中的科赫法则. Microbes and Infection, 16, 885-892.

Green, M. R., and Sambrook, J. (2018) 实时聚合酶链反应（PCR）实验数据的分析与标准化. Cold Spring Harbor Protocols, 2018, pdb.top095000.

Green, M. R., and Sambrook, J. (2019) 聚合酶链反应. Cold Spring Harbor Protocols, 2019, pdb.top095109.

Gunay, M., Goceri, E., and Balasubramaniyan, R. (2016) 用于 qPCR 最佳 CT 预测的机器学习. 15th IEEE International Conference on Machine Learning and Applications, 2016, 588-592.

Hayes, P. C., Wolf, C. R., and Hayes, J. D. (1989) 用于研究 DNA、RNA 和蛋白质的印迹技术. BMJ, 299, 965-8.

Heid, C. A., Stevens, J., Livak, K. J., and Williams, P. M. (1996) 实时定量 PCR. Genome Research, 6, 986-94.

Heptinstall, J., and Rapley, R. (1998) 核酸的分光光度分析. Methods in Molecular Biology, 86, 57-60.

Higuchi, R., Dollinger, G., Walsh, P. S., and Griffith, R. (1992) 特定 DNA 序列的同时扩增与检测. Bio/Technology, 10, 413-7.

Hill, A. B. (1965) 环境与疾病：关联还是因果？ Proceedings of the Royal Society of Medicine, 58, 295-300.

Hoffmann, B., Harder, T., Lange, E., Kalthoff, D., Reimann, I., Grund, C., Oehme, R., Vahlenkamp, T. W., and Beer, M. (2010) 新的实时逆转录聚合酶链反应有助于猪和人类样本中新型 A/H1N1 流感病毒的检测和区分. Berliner und Münchener tierärztliche Wochenschrift, 123, 286-92.

Holland, P. M., Abramson, R. D., Watson, R., and Gelfand, D. H. (1991) 利用水生栖热菌 DNA 聚合酶的 5' 至 3' 外切酶活性检测特定聚合酶链反应产物. Proceedings of the National Academy of Sciences of the United States of America, 88, 7276-80.

Hudecova, I., and Chiu, R. W. K. (2017) 利用母体血浆游离 DNA 进行地中海贫血的无创产前诊断. Clinical Obstetrics & Gynaecology, 39, 63-73.

Ito, J., and Braithwaite, D. K. (1991) DNA 聚合酶序列的汇编与比对. Nucleic Acids Research, 19, 4045-57.

Jeffreys, A. J., Wilson, V., and Thein, S. L. (1985) 人类 DNA 中的高变‘小卫星’区域. Nature, 314, 67-73.

Karrer, E. E., Lincoln, J. E., Hogenhout, S., Bennett, A. B., Bostock, R. M., Martineau, B., Lucas, W. J., Gilchrist, D. G., and Alexander, D. (1995) 从单个植物细胞中原位分离 mRNA：构建细胞特异性 cDNA 文库. Proceedings of the National Academy of Sciences of the United States of America, 92, 3814-8.

Kaushik, A., Tiwari, S., Dev Jayant, R., Marty, A., and Nair, M. (2016) 迈向即时检测中的埃博拉病毒病检测与诊断. Biosensors & Bioelectronics, 75, 254-272.

Kermekchiev, M. B., Tzekov, A., and Barnes, W. M. (2003) Taq DNA 聚合酶的冷敏感突变体为 PCR 提供热启动. Nucleic Acids Research, 31, 6139-6147.

Koch, R. (1882) 结核病的病因学. Berliner Klinische Wochenschrift, 15, 428-445.

