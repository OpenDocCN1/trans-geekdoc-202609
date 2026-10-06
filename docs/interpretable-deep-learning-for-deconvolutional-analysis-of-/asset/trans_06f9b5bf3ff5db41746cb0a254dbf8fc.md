

# CellPress

# Neuron（神经元）

深度学习架构为单次试验神经数据分析提供了一种高效且可扩展的工具。美国研究基金 (NARSAD) 年轻研究员补助第 305 号资助 S.M.；哈佛大脑行为倡议资助 P.M.；本研究部分工作得益于加拿大研究卓越基金，该基金通过麦吉尔大学的“健康大脑生活倡议”授予了 P.M.。

我们的框架具有灵活性，需要选择几个超参数（例如：稀疏正则化因子、展开迭代次数、平滑正则化和卷积核数量）。我们为参数选择提供了指导。例如，合适的卷积核数量可以通过识别和量化层与层之间的交叉相关性来确定。重要的是，必须指定卷积核的数量和核时间窗口——不需要额外的参数化。之前的方法³ DUNL 可以学习任何卷积核（另见下文）。当条目数量已知时，DUNL 具有其展开架构的 k-稀疏操作对参数的选择具有鲁棒性。

# 作者贡献

- 概念构化：B.T., S.M., P.M., 和 D.B.
- 方法论：B.T. 和 D.B.
- 形式分析：B.T. 和 S.M.
- 可视化（体内实验）：S.M., H.W., 和 S.T.
- 研究：N.U., V.N., 和 D.B.
- 数据整理：B.T., S.M., H.W., 和 S.T.
- B.T., S.M., V.N., V.A., P.M., 和 D.B. 
- 项目管理：P.M. 和 D.B.
- 资金获取：S.M., N.U., V.A., P.M., 和 D.B.



通过 k-稀疏操作，可以使用变分集对 `j` 进行调优。关于 DUNL 局限性的详细讨论，请参见补充材料。

# 利益声明

作者声明无竞争性利益。

为了证明我们模型的通用性，我们将其应用于不同的实验设置，突出了现有工具的功能。我们的框架可以扩展到稀疏区域之外，提供可解释的表示。对于更复杂的模型，例如基于卡尔曼滤波的神经网络或具有自适应常数的 2D 滤波器，我们的工作迈出了通过卷积字典学习利用深度学习优势的第一步，以获得对神经动力学及其计算过程的机制性见解。

# AI 及 AI 辅助方法声明

在准备本项工作期间，作者没有使用任何推理或内容生成技术。作者对出版内容承担全部责任。

# STAR*

详细方法见论文的在线版本，包括以下内容：

- 关键资源表
- 方法详述
- 体内实验
- 符号说明
- 数据分布
- 生成式模型
- 平滑稀疏卷积学习
- 可解释的展开神经网络 (DUNL)
- 评估
- 深度学习中的可解释性
- DUNL 局限性
- D.U.N.L. 用于神经信号分析的前期工作
- 量化与统计分析
- 模拟细节
- 实验细节
- 模型比较
- 模型训练细节

# 资源可用性

# 主要联系人

更多信息和资源的请求请联系主要联系人 Dean Baamba (baamba@seas.harvard.edu)。

# 可用材料

本研究未产生新的试剂。

# 数据和代码可用性

- 所有代码和模型已存储在 GitHub 仓库：https://github.com/debaamba/dunl-model。
- 本研究的部分数据已存储在数据仓库：https://doi.org/10.1763/zenodo.39253
- 使用这些数据所需的任何额外信息可根据要求向主要联系人获取。

# 致谢

我们感谢评审员提出的建设性反馈。感谢 Ignacio Sanchez-Sánchez 在多巴胺区域的概念和技术性合作。感谢实验室的所有成员、Murthy 以及其他人提供的有帮助的讨论，特别是 Carlos Janevatin-Zadeh、Adam S. Lowell 和 Henry S. Ford 在统计分析方面提供的帮助 (https://doi.org/10.5291/zenodo.392953)。我们感谢支持本工作的资助机构：美国英国国防 (US UK DO)、MOQ 以及欧洲研究委员会 (ERC) 的 ERCPIERC (资助号 11-WFF-1516-8) 以及加拿大科学基金计划 (L10000/2018) 资助 S.M.；大脑与行为基金。

# 补充信息

补充信息可以在 https://doi.org/10.1016/j.neuron.2022.05.006找到。

# 参考文献

1. Jun, J.J., Sternnetz, N.A., Siegle, J.H., Derman, D.J., Bauza, M., Barbardt, L., Bee, K.A., Anastasiou, C.A., Andrews, Y., Adyn, C., et al. (2017). 用于高分辨率神经活动记录的全集成光子光测量。Science 355, 222–236. https://doi.org/10.1126/science24636

2. Steinmetz, N., Koch, C., Haris, K., and Carandin, M. (2018). 神经探针的人群误差模型和大规模经验。Curr. Opin. Neurobi., 50, 92–100. https://doi.org/10.1016/j.conneuro.2018.009.

3. Wong, O., Ohnason, H., Skayten, E., Eneqvist, E., Wang, L., Miller, M., and E. (22). 双神经元模型解释视觉皮层的决策过程。Cell 185, 1236–1250. https://doi.org/10.1016/j.cell.2022.017.

4. Rigotti, M., Barak, A., Morgan, R., Wang, J., Davis, N., Miller, E., and Fuis, S. (2013). 复杂编码中的选择性。Nature 497, 595–600. https://doi.org/10.1038/nature1216.

5. Hiroiwaka, J., Hassawa, A., Mastet, P., Ott, T., and Kipp, A. (2019). 额叶皮层编码决策变量。Nature 576, 473–478. https://doi.org/10.1038/s41586-019-9.

6. Zhang, A., and Adams, A. M. (2023). 感觉和感觉任务变量的神经表示。Nature Communications 14, 4153. https://doi.org/10.1038/s41467-023-3951.

7. Dubreil, A., Beiran, M., Mastet, P., Faustopoulos, G., and Ott, S. (2022). 神经动力学计算中群体结构的作用。Nat. Neurosci. 25, 77–83. https://doi.org/10.1038/s41593-022-0784.

8. Langdon, C., and Earl, S. H. (2015). 决策期间来自异性神经网络的潜信息。Nature Neurosci 18, 1055–1060. https://doi.org/10.1038/nns4003.

9. Kaufman, K. T., Miller, E. K., Right, M., Stefani, F., Shen, S., and Chang, A. (2012). 从表示几何解码选择和意图。Curr. Opin. Neurobi., 22, 1024–1030. https://doi.org/10.1016/j.conneuro.2012.0604.

10. Lee, R. S., Saily, Y., England, G., Winter, L. B., and Day, N. D. (2024). 决策期间多巴胺神经元中的任务驱动预测误差。Nat Neurosci 20, 482–494. https://doi.org/10.1038/s41593-017-0060-w.

11. Lee, R. S., Saily, Y. 多巴胺神经元中的预测误差。Nat. Neurosci., 27, 1571–1578. https://doi.org/10.1038/s41593-014-0268-1.

12. Schwartz, S. (2016). 解码驱动的预测误差：概念视角。Nat. Neurosci, 19, 177–183. https://doi.org/10.1038/nn4315-5.

13. Matsumoto, S., Han, J., Uchida, N., and Wadato, M. (2006). 多巴胺神经元揭示了奖励学习中的显著信号。Science 294, 973–976. https://doi.org/10.1126/science.112933.

14. Williams, A. H., and Linderman, S. W. (2001). 单细胞中的统计神经科学。Opin. Neurobi., 78, 203–215. https://doi.org/10.1016/j.conneuro.2001.0617.

15. Czerniak, G. E., Itzen, Y., Sinha, S., Muka, W. B., and Brown, E. R. (2008). 高维神经空间决策的群体活动模型。J. Neurosci., 29, 2762–2769. https://doi.org/10.1523/jneuro1.

16. Miller, C. G., Dore, K., Huck, A., Leopold, D., Ska, M., Tursen, T., and Miles, J. (2002). 大脑的神经语言。Cell, 32, 482–493. https://doi.org/10.1016/j.cell.2002.031.

17. Green, C., and Konrath, A. (2012). 激活神经元。Nature Reviews Neuroscience, 13, 693–702.

18. Helmholtz, H. (1867). 心理学中的光学。Phys. Soc. B, 36, 815–839. https://doi.org/10.1038/s41586.

19. Smaragdos, P. (2000). 非负矩阵因子提取：重叠信号的分解。Component Analysis and Blind Signal Separation: International Conference, ICA 2004, Geneva, Spain, September 22–24, 2004.

20. Smaragdos, P. (2007). 卷积分离及其在语音分离中的应用。Audio Signal Process., 15, 1–12. https://doi.org/10.1016/j.aasp.2006.11.009.

21. Xu, J., and Wei, X. (2017). 用于恢复低维动态的变分因子分析。Deep learning, 30, 989–996. https://doi.org/10.1038/s41586.

22. Mackveus, E. L., Bach, H. A., Williams, A. H., Gu, S. G., Denarko, N., and Johnston, J. A. (2014). 高维动力学中的时间序列解码：神经科学的应用。Science e, 8(7), e1214847. https://doi.org/10.1126/science.1214847.

