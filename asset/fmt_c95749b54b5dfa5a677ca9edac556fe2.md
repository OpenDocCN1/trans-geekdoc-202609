
如图 3 所示，识别出两个峰并用红色虚线标出。我们假设这些峰源于 `Li+` 环境中的两种氧原子。这与我们的模拟观察一致，即在 0.5 m 时，由于低浓度和 AG 相互作用，`Li+` 周围着溶剂和阴离子原子。这些单元可能没有通过溶剂分子的稳定。在锂离子电解质中，溶剂分子带电，DM 设计用于极化正离子，导致阴离子释放溶剂分子。-0.370 和 -0.360 的电荷分布表明自由 FST 潜在的四面体差异。

节点级和边缘。补充方程 (1)–(2) 中提供了更多关于 `GET` 模型的内容。

作为损失函数对随机选择的模型进行微调的标签（补充方程 (52)）。关于 `BAMBOO` 集合知识解构的更多细节请见补充方程 (47–53)、补充材料 3 和 4 以及补充。

## 相互作用的分离

一旦到达第一层，我们使用两个全连接网络利用基于神经网络的每个原子能量 `E_i` 和原子电荷 `q_i`。然后，我们根据电荷密度理论定义静电能。在这项工作中，我们使用机器学习力场（`MLFF`）改进了电荷密度以提高效率。我们对 `GNN` 使用了正则化策略来生成，并包含了通过 MD 步长生成的昂贵平衡求解器。此外，对于结构，我们可以通过密度 `D^{(i)}` 定义势能面。最后，我们将神经网络、静电和色散相互作用结合起来，计算每个原子的总能量和力。关于相互作用分离的更多细节请见补充方程 (22–45)、补充表 1 以及补充。

## 密度对齐

我们使用集合模型作为执行密度对齐的基准。为了对齐混合物，我们首先计算每种液体的概率 `P(ρ)`。通过训练 `BAMBOO` 模型来适应均匀压力（`ΔP`）。使用这些不同的 `MLFF`，我们使用 600 pN 步生成密度分布。然后，我们为每种液体建立 `Δρ` 与 `ΔP` 之间的线性相关性。利用这一点，我们可以确定每种液体的值 `V`。通过此，我们确定了应整合到每种液体 `MLFF` 中的特定 `ΔP` 值，以实现对齐。最后，我们使用补充方程 (58) 提供的结果——为每种液体确定的适当 `ΔP` 值——将基准模型与集合数据进行对齐。关于 `BAMBOO` 密度对齐的细节请见补充方程 (54–58) 和补充图 9–13。

## BAMBOO 的初始训练

我们使用 `GET` 架构和结构来生成不同的相互作用，使用结合能量、力、维里张和应力的损失函数来训练 `BAMBOO` 中的神经网络。具体而言，`BAMBOO` 对电荷的训练通过四个方面：首先是训练神经网络、力和电荷，以及其他来自电势电荷密度的静电势；第三点是训练密度，即通过 `DFT` `D` 来自电荷密度的宏观观测值；第四点是对齐平衡结构。

在这项工作中，我们使用 `PyTorch` 在 `BAMBOO` 中构建了神经网络，并使用学习率为 `10^{-2}` 的 `AdamMax` 优化器。在训练过程中，权重衰减设置为 0.0001，而学习率以 `10^{-4}` 的速率降低。批大小为 128。该模型由三层组成，嵌入维度为 64。它具有 16 个注意力头，每层消息传递层使用 0.5 Å 的截断，并包含了用于预测能量和力的双层全连接网络。

## MLFFs

我们使用 `LAMMPS` 进行 `BAMBOO` 的 MD 模拟。对于每个系统，初始步骤是能量最小化，限制为最大 10000 次迭代和 100000 次评估。之后，系统处于平衡状态，步长保持在至少 1 fs。密度值如表所示。然后，我们在 `DFT` 集合下运行 4-ns 的生产运行，以估计液体的密度和电导率。我们使用 Einstein-Nernst 方法以及之前工作“On-surface of Maxwell-Wagner”中描述的方法计算电导率。MD 模拟的细节请见补充方程 (64)。

## 数据可用性

数据集可在 https://huggingface.co/datasets/ml-bamboo 获取。完整数据集包含参数、`LAMMPS` 的原子结构以及最终结果，集合数据和结果也可在 Zenodo 获取：https://doi.org/10.5281/zenodo.6460320 (参考文献)。

## 代码可用性

源代码、`GET` 训练模型以及用于模拟的 `LAMMPS` 输入文件可在 https://github.com/bydentance/bamboo 获取，也可在 Zenodo 获取：https://doi.org/10.5281/record.6460320 (参考文献)。

## MLFF 的集合知识发现

在这项工作中，我们使用带有随机种子的 `DFT` 测试了四个模型。随后，我们为所有系统从600 ps 等向同性 (`NPT`) MD 和 400 ps 正则系 (`NVT`) MD 中选择了一个模型（补充图 7）。基于此目标，我们训练模型来预测每个系统轨迹中随机选择的 100 个样本的能量和力。最后，我们使用预测平均值

# 参考文献

- 1. Xu, K.. 锂离子电池的纳米级电解质。Chem. Rev. 104, 4303–4318 (2004).
- 2. Xu, K., et al.. Interfaces and Functions: Applications in Batteries (Royal Society of Chemistry, 2023).
- 3. Meng, Y., S., Viswan, V., & Xu, K.. Designing electrolytes. Science 378, e3750 (2022).
- 4. Unke, O. T., et al.. Machine learning for fields. Chem. Rev. 121, 10102–10133 (2021).
- 5. Frenkel, D. & Smith, B.. Understanding Molecular Simulation: From Atoms to Applications (Elsevier, 2023).
- 6. Behler, J., & Parrinello, M. 神经网络的泛化表示。
- 7. Zhang, L., Wang, H., Car, R., & E. 高维势能面。
- 8. Montes-Campos, H., Carrette, J., Bichemeier, S., Varela, L. & M. 机器学习的场。
- 9. Wang, J., & Wang, C. 深度学习的场。
- 10. Batner, S., et al. 可伸缩的等变力场。
- 11. Thölke, P. Ko, J., Goedicker, S. & Behler, J. 等变力场。
- 12. Yao, Y. & Smith, J. 等变变换器。
- 13. Ko, T., Finker, G., Goedicker, J. 具有局部原子表示的势能面。
- 14. Doj, S., et al. 密度值。
- 15. Jackson, L., et al. 局部原子表示。
- 16. Fu, X., et al. 预测的挑战。
- 17. Onke, U. & Muhovsky, M. 预测能量和力。
- 18. Onke, et al. 旋旋相关的深度学习。
- 19. Wang, Y. et al. 向量标量相互作用的等变表示。
- 20. Chen, C., & Wang, S. 化学结构的图神经网络的局限性。
- 21. Deng, D., et al. 边界不变性。
- 22. Zhang, J., et al. s1467-。
- 23. Batista, I., et al. 基于注意力机制的模型。
- 24. Kovacs, D., et al. 可迁移的 ACE-MP。
- 25. Wang, J., et al. 使用机器学习力场的分子动力学。
- 26. Schneider, H., Creon, A., & Schwaluber, T. (B96)/Becke-Johnson) 色散修正。
- 27. Vaswani, A. et al. 注意力即一切。
- 28. Gong, S., et al. 化学结构的图神经网络。
- 29. Thorne, D., et al. LAMMPS：一种用于跨尺度粒子基分子模型的灵活模拟工具。
- 30. Musaleik, A. et al. 使用局部原子表示的分子力学。
- 48. Pezeikh, P. R., 等。DeepMD-net: 用于分子模拟的快速神经网络势能。预印本于 https://arxiv.org/abs/2407.09666 (2024)。
- 70. Shao, Y., 等。Q-chem 软件包中用于分子量子化学的注意力机器学习。自然-化学 (*Nature chemistry*), 11, 184–195 (2023)。
- 49. Mathias, G. A., & Lang, C. H. 外推与学习方程。在：第 35 次国际机器学习会议 https://proceedings.mlr.org/v801.html (PMLR, 2018)。
- 71. Wang, L. J., Zhang, Z., & Srinivasan, V. 电解质输运中车辆设计与结构设计的相对重要性。电化学学会杂志 (*J. Electro. Soc.*), 170, 110536 (2023)。
- 50. Dove, A. R. 锂离子电池电解质的自动化设计与发现：硫电池 (Phethio Cell)，自然医学 (*Nature Medicine*) (2023)。
- 51. Higashiyama, K., 等。1,3-二氧烷-水混合物的物理性质。自然 (*Nature*), 7, 210–218 (2016)。
- 52. Sasaki, Y., & Furimoto, H. 用于能量转换与存储的材料。能量 (*Energy*) (Else)。
- 74. Simon, G., & Fischer, B. GraphNet: 基于 Transformer 的表示方法。神经网络与信息处理系统 (*Neural. Inf. Process.*), 36, 3733–3754 (2022)。
- 53. Janssen, A., Thorbersen, S., Jung, J., & Lu, E. 用于电容器的氟代电解质。电化学学会传输 (*ECS Trans.*), 35, 51 (2007)。
- 74. Goes, J., 等。电池技术手册 (*Handbook of Battery Technology*) 525–626 (Wiley)。
- 55. Dove, A. R. 优化准水电解质。自然通讯 (*Nature Commun.*), 13, 5542 (2022)。

# 致谢

感谢来自科罗拉多矿学院的 Misty A 教授。我们感谢卡内基梅隆大学的 Dove 提供的数据。

56. Logan, E., 等。碳酸盐基电解质的研究。电化学学会杂志 (*J. Electro. Soc.*), 165, A473 (1960)。

# 作者贡献

概念构思：Weihao Gao；方法：Jia Yu；撰写初稿：Weihao；审阅与编辑：Jia Yu；监督：Weihao。

# 利益冲突

所有作者均声明无利益冲突。研究项目获得 Nature Research 的资助。此外，此处描述的创新已提交专利申请（编号 202312246），正在审核中。

# 补充信息

在线版本包含补充材料 https://doi.org/10.1038/s41586-025-01009-7

Nature 感谢 Jia Yu 和其他评审员对本文工作的同行评审。

重印与许可请访问 https://www.nature.com/reprints

出版社说明 Nature Research 在司法管辖和机构隶关系方面保持中立。作者或其他持有者根据与 Springer Nature Limited 的协议拥有文章的独占权利。Nature Intelligence 2025

57. Zhu, S., 等。利用深度几何学习进行非水基电解质的可微建模与优化。自然-化学 (*Nature Chem.*), 15, 5884 (2023)。
58. Li, Y., Ko, J., & Wang, G. 从分子势能确定阳离子输运。预印本于 https://arxiv.org/abs/2111.06745 (2021)。
59. Beneman, C. M. & Wieberg, K. 从分子势能确定阳离子分子。物理化学杂志 (*J. Chem. Phys.*), 1, 01109 (2021)。
60. Paske, A., 等。PyTorch：一种直观、高性能的深度学习库。神经网络与信息处理系统 (*Neural Net. Inf. Process.*), 31, 80–98 (2019)。
61. Kingma, D. P., & Ba, J. A. Adam：一种随机优化方法。预印本于 https://arxiv.org/abs/1412.6980 (2014)。
62. Beck, A. D. 泛函理论 III：交换的作用。物理化学杂志 (*J. Chem. Phys.*), 88, 5568–5573 (1993)。
63. Helweg, A. R. & Scharfetter, D. 为 RI-MP2 和 RI-CC 计算开发新的 Kohn-Sham 函数辅助基（DZS, 2DZVP 和 def-2DZVP）。物理化学 (*Phys. Chem. Chem.*), 17, 1010–1017 (2015)。

Weigert, F. 从 H 到 Na 的 Hartree-Fock 交换拟集。计算化学杂志 (*J. Comput. Chem.*), 29, 167–178 (2008)。

64. Wu, X., 等。带有 GPU 加速的基于 PyTorch 的量子化学计算。预印本于 https://arxiv.org/abs/2404.09452v1 (2024)。
