

## 摩擦的原子尺度建模

- 82. M. Aichele and M. Müser, Phys. Rev. E, 68, 016125 (2003). 边界润滑系统中的动力学摩擦与原子不稳定性。
- 83. N. J. Moses, H. Müser, and T. K. Woo, Science, 307, 1612 (2005). 润滑添加剂功能性的分子机制。
- 84. L. Lian and M. O. Robbins, Nature, 435, 929 (2005). 机械接触中连续介模型的失效。
- 85. Q. Yi, Y.-T. Cheng, T. Cagin, and W. A. Godard, Phys. Rev. B, 66, 085420 (2002). Ni(100)/(100) 界面上的摩擦各向异性：分子动力学研究。
- 86. S. J. Ko and A. J. Gellman, Langmuir, 16, 8343 (2000). Ni(100)/Ni(100) 界面上的摩擦各向异性。
- 87. J. M. Martin, C. Bonnet, and T. Le Monge, Phys. Rev. B, 48, 10583 (1993). 二硫化钼的超流性。
- 88. W. Guo and H. Gao, Comput. Model. Eng.-Sci., 7, 19 (2005). 多层碳纳米管中优化的轴承与层间摩擦。
- 89. J. Cumings and A. Zettel, Science, 289, 602 (2000). 多层碳纳米管的低摩擦线性轴承。
- 90. J. Cummins and A. Zettel, Nature, 405, 586 (2000). 多层纳米管的剥离与锐化。
- 91. W. Guo, Y. Guo, Y. Dai, and Z. Wang, Phys. Rev. Lett., 91, 125501 (2003). 多层碳纳米管上吉赫振荡器的能量色散。
- 92. P. Tanney, S. G. Louie, and M. L. Cohen, Phys. Rev. Lett., 93, 065503 (2004). 同心碳纳米管之间的动态滑动。
- 93. A. Soluciu, R. Benewitz, E. Gnecco, and E. Meyer, Phys. Rev. Lett., 92, 134001 (2004). 原子摩擦中从粘滞滑动到连续滑动的转变：引入超流摩擦的新范态。
- 94. Z. Xia and A. W. Curtin, Phys. Rev. B, 69, 233408 (2004). 多层碳纳米管中的拉出力与摩擦。
- 95. W. Guo, W. Zhong, Y. Dai, and S. Li, Phys. Rev. Lett., 92, 075409 (2004). 多层碳纳米管中层间摩擦的缺陷-尺寸耦合效应。
- 96. A. Ulman, Chem. Rev., 96, 1533 (1996). 自组装单分子与单层的形成与结构。
- 97. J. E. Houston and H. I. Kim, Acc. Chem. Rev., 35, 547 (2002). 功能化自组装单层子的粘附、摩擦与机械性能。
- 98. H. I. Kim and J. E. Houston, J. Am. Chem. Soc., 122, 12045 (2000). 分子级摩擦中机械与化学贡献的分。
- 99. B. Park, M. Chandra, M. J. Stevens, and G. S. Brest, Langmuir, 19, 9239 (2003). 化学对原子级烷基单层间粘附与摩擦的影响：分子动力学模拟。
- 100. B. C. D. Lorenz, M. Chandra, M. J. Stevens, and G. S. Brest, Langmuir, 20, 10007 (2004). 氟端自组装单层的功能性动力学。
- 101. E. D. Smith, M. O. Robbins, and M. Cieplak, Phys. Rev. B, 54, 8252 (1996). 吸附单层上的摩擦。
- 102. M. Nicholls, T. Do, P. R. Norton, M. Kasrai, and G. M. Bancroft, Tribol. Int., 38, 15 (2005). 二烷基二硫磷盐降低金属表面润滑的作用。
- 103. N. J. Moses, T. K. Woo, M. Kasrai, P. R. Norton, G. M. Bancroft, and H. Müser, Trib. Lett., 24, 105 (2000)。

## 自由体积、结构有序与熵

材料的宏观性质与粒子间的相互作用密切相关，无论是原子、分子还是胶体。例如，低密度气体的压力可以通过维尔展开进行准确描述，而其传输系数可以从动力学理论中估计。

然而，液体、玻璃态以及其他软物质的概念图景要复杂得多。一方面，这些材料的平均结构密度过大（即相关性太强），而不适用于“稀疏气体”描述；另一方面，它们又太无序，而不适用于晶体单元框架。结果是，液体和玻璃态理论（以及玻璃化转变本身）的进展在很大程度上得益于气体模型。尽管如此，在过去的20年里取得了重大进展，这些进展得益于 (1) 模拟液态高效算法的发展，以及 (2) 能够在更广阔长度和时间尺度上探索这些系统的更快速计算机。

从某种意义上说，理解液体和玻璃态的许多进展可以直接归功于计算机模拟能够为各种模型系统的相关材料属性“三位一体”（结构、热力学和动力学）提供精确信息。这些新信息使得对关于液体和玻璃态特征行为微观起源的最普遍观点能够严格测试。本章重点关注三个核心概念（结构有序性、自由体积和熵），这些概念在这一领域继续受到关注，很大是因为它们为连接静态或热力学属性与动力学提供了有前景的（尽管仍是经验性的）方法。对于每个概念，我们给出了基础定义并采用了一些相关的计算策略。我们讨论了继续使用它们的理由，但也提到它们的一些实际局限性。最后，给出了一些示例，说明这些概念的计算应用如何导致新的物理见解。

