
减少描述符数量（通过向下选择或降维）、扩展训练集、正则化或加入物理先验知识是有效的。作为一个有用的经验法则，当模型变量数量少于训练数据数量的一半时，过拟合很可能得以避免。第2.4节总结了过拟合控制的常用方法。交叉验证对于小数据集有效，而用独立测试集验证模型预测性是最可靠的方法。此外，在使用模型于未知材料空间中筛选新材料时，必须注意模型的适用范围。离模型适用域越远，预测不确定性越高，预测置信度越低。一些降维技术，如t-SNE和UMAP，可用于说明模型的适用范围。对神经网络应用贝叶斯正则化（其中权重被权重的分布取代）也可以估计模型预测的不确定性。

模型有时可能对大多数数据表现良好，但对少量材料（异常值）表现不佳。未经仔细分析就排除异常值是不明智的。在某些情况下，异常值可能是实验误差的结果，当重复相关测量时可以识别。异常值也可能是训练数据中出现频率较低的特征的结果。因此，必须仔细分析异常值的结构、描述符和模型参数，因为从中可以提取有用的信息。

## 4.3. 机器学习在电/光催化应用中的挑战与机遇

尽管机器学习在电催化剂和光催化剂的自动化发现与开发中取得了显著进展，但仍然存在许多挑战。首先，构建准确且广泛适用的机器学习模型依赖于大规模、高质量的数据集，但获取这些数据集可能困难或昂贵。文献中已发表的数据可能是机器学习模型构建的重要数据来源。然而，催化反应不仅强烈依赖于温度、浓度、压力和流速等实验参数，还可能对可能被忽视的其他条件（如反应器形状、搅拌速度）敏感。这可能导致已发表的结果无法比较。更严格地记录实验中所有相关的元数据将克服这个问题，在实验中使用阳性对照材料也是如此。已发表数据的可靠性是另一个问题。例如，虽然牺牲试剂广泛用于光催化水分解中捕获空穴并提高产氢速率，但研究发现氢可能来自牺牲试剂氧化。Das等人揭示了一些溶剂对紫外光极其敏感，分解为CO、CH₄和C₂H₄，导致光催化CO₂还原结果出现偏差。即使在相同条件下，一些实验结果也很难被其他实验室重复。在将已发表数据加入训练集之前，催化剂专家对其进行批判性分析非常重要。此外，机器学习模型可能存在偏差，因为通常只有成功的结果被报道，而低性能或非活性材料也为机器学习模型提供有用信息。与使用已发表数据相比，未来广泛采用高通量合成和表征方法应能缓解这些问题。此外，合作

其次，尽管一些成功的结构–电/光催化反应，但通过机器学习建模却很少进行。我们通过一个在超快时间尺度上对PCET的机器学习-分子动力学研究来说明这一点。然而，机器学习在研究其他重要的动力学过程，如单电子或多电子氧化/还原、固-固或固-液界面之间的电荷转移、载流子的分离和复合等方面的应用仍然很少。这可能是因为通过计算和实验探测分子的激发态很困难，导致机器学习模型训练的数据不足。最近，一些尖端实验技术，如开尔文探针力显微镜、飞秒分辨瞬态吸收光谱和时间分辨瞬态光致发光，已被用于研究载流子迁移率。含时DFT已被用于研究光催化剂中激发态电子的动力学，机器学习技术在加速和提高含时DFT计算精度方面发挥了作用。可以预期，当机器学习与原位研究数据和分子动力学模拟相结合时，将进一步促进电/光催化机制的研究。

第三，由于实验或第一性原理计算数据将继续稀缺，开发从较小数据集生成可靠机器学习模型的技术非常重要。先进的解决方案，如强化学习、主动学习和迁移学习，已被用来解决数据有限的学习问题。最近，元学习被提议作为解决小数据集问题的另一个有前景的方案。元学习通过其他模型的学习经验，生成能够适应并泛化到新任务和新环境的模型。换句话说，元学习模型将首先从在大数据集上训练的其他相关模型学习关系，并利用这些先验知识解决较小数据集上的问题。例如，基于堆叠的元学习已被用于从各种基础模型学习预测，在此基础上构建精确模型来预测具有广泛结构的氧化物光催化剂的带隙和析氢活性。转化机器学习是另一种有望解决小数据集的元学习算法。与从多个基础模型学习知识的堆叠不同，转化机器学习跨一组相关任务提取知识。目前，转化机器学习在药物发现中表现稳健，我们预计它将应用于电/光催化开发（例如，不同分子的结构到催化活性的映射）。可以预期，元学习能够加速数据不足的电/光催化材料研究。归根结底，机器学习模型从有限数据量中能提取的信息是有限的。

第四，通过简单可解释的描述符来描述复杂的催化机制具有挑战性。由于描述符不仅弥合催化剂特征与催化动态事件之间的差距，而且对机器学习模型质量有重大影响，从潜在描述符池中进行特征选择至关重要。最流行的策略是基于化学和

研究兴趣包括钙钛矿光催化和光致发光、铁电薄膜、无机胶体纳米晶体的可控合成以及机器学习。

Tu Le是皇家墨尔本理工大学STEM学院工程学院的讲师。在2017年加入皇家墨尔本理工大学之前，她曾在澳大利亚联邦科学与工业研究组织工作。她于2010年在斯威本科技大学获得博士学位。她感兴趣的是使用机器学习算法进行材料设计和开发，广泛的应用包括可持续能源发电和存储、传感器和治疗。

Dehong Chen是澳大利亚皇家墨尔本理工大学应用化学与环境科学领域的研究员。他于2006年在复旦大学获得化学博士学位。在加入皇家墨尔本理工大学之前，他在墨尔本大学和澳大利亚国立大学进行研究工作。他目前感兴趣的是设计和合成各种功能材料，应用于清洁能源利用、储能、环境修复和传感等领域。

David Winkler是拉筹伯大学分子科学研究所的教授，诺丁汉大学客座教授，以及莫纳什大学莫纳什药物科学研究所的药物化学教授。他应用计算化学、人工智能和机器学习方法设计药物、农用化学品、纳米材料和生物材料的研究已产出200多篇期刊文章和书籍章节以及25项专利。他获得了包括CSIRO商业卓越奖章、RACI的Adrien Albert奖和ACS Herman Skolnik奖在内的著名奖项。他在全球81000名药物化学家中排名第227位，在520000名化学家中排名第999位（Mendeley 2019）。

Rachel Caruso是皇家墨尔本理工大学应用化学与环境科学学科的教授。她在墨尔本大学学习，之后领导了马克斯·普朗克胶体与界面研究所、墨尔本大学、澳大利亚联邦科学与工业研究组织和皇家墨尔本理工大学的研究团队。她在材料化学方面的专业知识已应用于研究纳米尺度材料的结构控制，重点关注多孔金属氧化物、钙钛矿和碳基材料，这些材料在光催化、吸附剂以及能量转换和储存方面具有潜力。

## 致谢

感谢澳大利亚研究委员会通过Discovery Projects DP180103815和DP220100945提供的支持。

## 参考文献

- 1. Tachibana, Y.; Vayssieres, L.; Durrant, J. R. Artificial photosynthesis for solar water-splitting. *Nat. Photonics* **2012**, *6*, 511–518.
- 2. Chu, S.; Majumdar, A. Opportunities and challenges for a sustainable energy future. *Nature* **2012**, *488*, 294–303.
- 3. Kittner, N.; Lilli, E.; Kammen, D. M. Energy storage deployment and innovation for the clean energy transition. *Nat. Energy* **2017**, *2*, 17125.
- 4. Clarke, C. J.; Tu, W.-C.; Levers, O.; Bröhl, A.; Hallett, J. P. Green and Sustainable Solvents in Chemical Processes. *Chem. Rev.* **2018**, *118*, 747–800.
- 5. Seh, Z. W.; Kibsgaard, J.; Dickens, C. F.; Chorkendorff, I.; Nørskov, J. K.; Jaramillo, T. F. Combining theory and experiment in electrocatalysis: Insights into materials design. *Science* **2017**, *355*, No. eaad4998.
- 6. Suen, N.-T.; Hung, S.-F.; Quan, Q.; Zhang, N.; Xu, Y.-J.; Chen, H. M. Electrocatalysis for the oxygen evolution reaction: recent development and future perspectives. *Chem. Soc. Rev.* **2017**, *46*, 337–365.
- 7. Roger, I.; Shipman, M. A.; Symes, M. D. Earth-abundant catalysts for electrochemical and photoelectrochemical water splitting. *Nat. Rev. Chem.* **2017**, *1*, 0003.
- 8. Wang, Q.; Domen, K. Particulate Photocatalysts for Light-Driven Water Splitting: Mechanisms, Challenges, and Design Strategies. *Chem. Rev.* **2020**, *120*, 919–985.
- 9. Chen, S.; Takata, T.; Domen, K. Particulate photocatalysts for overall water splitting. *Nat. Rev. Mater.* **2017**, *2*, 17050.
- 10. Mai, H.; Chen, D.; Tachibana, Y.; Suzuki, H.; Abe, R.; Caruso, R. A. Developing sustainable, high-performance perovskites in photocatalysis: design strategies and applications. *Chem. Soc. Rev.* **2021**, *50*, 13692–13729.
- 11. Low, J.; Yu, J.; Jaroniec, M.; Wageh, S.; Al-Ghamdi, A. A. Heterojunction Photocatalysts. *Adv. Mater.* **2017**, *29*, 1601694.
- 12. Liu, X.; Iocozzia, J.; Wang, Y.; Cui, X.; Chen, Y.; Zhao, S.; Li, Z.; Lin, Z. Noble metal-metal oxide nanohybrids with tailored nanostructures for efficient solar energy conversion, photocatalysis and environmental remediation. *Energy Environ. Sci.* **2017**, *10*, 402–434.
- 13. Wei, H.; McMaster, W. A.; Tan, J. Z. Y.; Chen, D.; Caruso, R. A. Tri-component brookite/anatase TiO₂/g-C₃N₄ heterojunction in mesoporous hollow microspheres for enhanced visible-light photocatalysis. *J. Mater. Chem. A* **2018**, *6*, 7236–7245.
- 14. Singh, N.; Goldsmith, B. R. Role of Electrocatalysis in the Remediation of Water Pollutants. *ACS Catal.* **2020**, *10*, 3365–3371.
- 15. Rong, F.; Lu, Q.; Mai, H.; Chen, D.; Caruso, R. A. Hierarchically Porous WO₃/CdWO₄ Fiber-in-Tube Nanostructures Featuring Readily Accessible Active Sites and Enhanced Photocatalytic Effectiveness for Antibiotic Degradation in Water. *ACS Appl. Mater. Interfaces* **2021**, *13*, 21138–21148.
- 16. Le, T.; Epa, V. C.; Burden, F. R.; Winkler, D. A. Quantitative Structure-Property Relationship Modeling of Diverse Materials Properties. *Chem. Rev.* **2012**, *112*, 2889–2919.
- 17. Reymond, J. L. The Chemical Space Project. *Acc. Chem. Res.* **2015**, *48*, 722–730.
- 18. Walsh, A. The quest for new functionality. *Nat. Chem.* **2015**, *7*, 274–275.
- 19. Hohenberg, P.; Kohn, W. Inhomogeneous Electron Gas. *Phys. Rev. B* **1964**, *136*, B864.
- 20. Kohn, W.; Sham, L. J. Self-Consistent Equations Including Exchange and Correlation Effects. *Phys. Rev.* **1965**, *140*, A1133.
- 21. Potyrailo, R.; Rajan, K.; Stoewe, K.; Takeuchi, I.; Chisholm, B.; Lam, H. Combinatorial and High-Throughput Screening of Materials Libraries: Review of State of the Art. *ACS Comb. Sci.* **2011**, *13*, 579–633.
- 22. Curtarolo, S.; Hart, G. L. W.; Nardelli, M. B.; Mingo, N.; Sanvito, S.; Levy, O. The high-throughput highway to computational materials design. *Nat. Mater.* **2013**, *12*, 191–201.
- 23. Lejaeghere, K.; Bihlmayer, G.; Björkman, T.; Blaha, P.; Blügel, S.; Blum, V.; Caliste, D.; Castelli, I. E.; Clark, S. J.; Dal Corso, A.; et al. Reproducibility in density functional theory calculations of solids. *Science* **2016**, *351*, aad3000.
- 24. Yan, Q.; Yu, J.; Suram, S. K.; Zhou, L.; Shinde, A.; Newhouse, P. F.; Chen, W.; Li, G.; Persson, K. A.; Gregoire, J. M.; et al. Solar fuels photoanode materials discovery by integrating high-throughput theory and experiment. *Proc. Natl. Acad. Sci. U. S. A.* **2017**, *114*, 3040–3043.
- 25. Qiu, B.; Xing, M.; Zhang, J. Recent advances in three-dimensional graphene based materials for catalysis applications. *Chem. Soc. Rev.* **2018**, *47*, 2165–2216.
- 26. Tabor, D. P.; Roch, L. M.; Saikin, S. K.; Kreisbeck, C.; Sheberla, D.; Montoya, J. H.; Dwaraknath, S.; Aykol, M.; Ortiz, C.; Tribukait, H.; et al. Accelerating the discovery of materials for clean energy in the era of smart automation. *Nat. Rev. Mater.* **2018**, *3*, 5–20.
