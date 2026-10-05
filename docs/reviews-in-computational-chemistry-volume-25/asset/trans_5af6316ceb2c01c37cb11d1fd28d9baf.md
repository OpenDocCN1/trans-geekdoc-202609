

## Adam-Gibbs 模型的替代方案？151

![](img/fa9d34afc1bcb785fd3792baa6c5c679_182_0.png)

**图 14** 在两种不同密度 $\rho$ 值下，BKS 硅模型的自扩散系数 $D$ 随构型熵 $SC$ 变化的数据（符号）。实线为公式 [10] 给出的 AG 模型拟合曲线。重印自文献 91。

## ADAM–GIBBS 的替代方案？

最后，我们注意到另一种将单粒子动力学与熵联系起来的指数标度律发现在原子过冷液体中成立$^{122}$。特别是，这种关系：

> $D = D_0 \exp[Bs^{ex}]$ $[15]$

极好地捕捉了多种不同模型液体在等容过冷时的行为。这里，$s^{ex}$ 是摩尔过量熵，即液体的摩尔熵与相同密度理想气体的摩尔熵之差。量 $D_0$ 和 $B$ 是与温度无关的参数，因此，公式 [15] 表明过冷液体 $D$ 的非平凡 $T$ 依赖性完全被 $s^{ex}$ 所捕捉。

由于公式 [15] 中的关系涉及过量熵 $s^{ex}$ 而非构型熵 $S_C$，它相比 AG 关系具有三个重要的实际优势，使其成为未来研究特别感兴趣的主题。首先，与 $S_C$ 不同，$s^{ex}$ 是标准热力学变量$^{123}$，不需要了解能量景观（PEL）的详细拓扑信息。其次，确定 $s^{(2)}$（见公式 [3]）近似只需要知道实验可获取的径分布函数 $g(r)$$^{40}$。因此，公式 [15] 将为过冷液体结构与动力学之间难以捉摸的联系提供新见解$^{124}$。第三，尽管 $S_C$ 不被认为与冰点以上流体的动力学特别相关，但据报道，$s^{ex}$ 为平衡流体的传输系数提供了标度关系$^{125-130}$，这意味着 $s^{ex}$ 似乎是从“理想气体到气体”动力学相关的热力学量$^{122}$。然而，由于公式 [15] 的成功是非常最近的发现，还需要更多的研究来探测该关系在过冷液体态下的普适性。此外，与 AG 关系一样，仍然缺乏对 $s^{ex}$ 与流体动力学性质之间观测到的经验联系的根本“第一性原理”证明。

## 结论

在本章中，我们回顾了计算方法是如何成为研究液态和气态行为微观起源的工具的。我们的讨论集中在三个对这些系统的“基于物理”模型产生深远影响的概念上：粒子的结构有序、自由体积和熵。对于这些每一个概念，我们都提供了介绍性材料，并描述了一些基础算法工具，我们认为这些工具对研究生或该领域的新科学家可能会有所帮助。我们还强调了在模型系统中对这些思想进行广泛测试的一些发现。一个贯穿的主题是，研究液态的三种不同方法共享一个共同假设：静态（结构和热力学）性质与动力学之间存在着紧密的联系。尽管这种联系确实存在，但观测到的特定关系尚未证明其遵循形式的统计力学处理。然而，由于模拟可以提供关于模型系统结构、热力学和动力学的详细信息，它们将继续在未来旨在理解这些观测的理论测试中发挥不可或缺的作用。

## 致谢

T. M. Truss 感谢美国科学基金会、美国化学学会石油基金、David and Lucile Packard 基金、Alfred P. Sloan 基金以及德克萨斯先进计算中心的支持。W. P. Krekberg 感谢科学基金会的支持。J. R. Errington 感谢科学基金会、美国化学学会石油基金以及布法罗大学的支持。

## 参考文献

- 1. D. A. McQuarrie, 《统计力学》， Harper-Collins, New York, 1976.
- 2. S. Chapman and T. G. Cowling, 《非均匀气体数学理论》， Cambridge University Press, 1970.
- 3. O. O. Hirshfelder, C. Curtis, and R. B. Bird, 《气体与液体的分子理论》， Wiley, New York, 1954.
- 4. M. Goldstein, J. Phys., 51, 3728 (1999). 粘性液体与气体转变。
- 5. F. H. Stillinger and T. A. Weber, Phys. Rev. A, 25, 978 (1982). 液体中的隐藏结构。
- 6. F. H. Stillinger, Science, 267, 335 (1995). 过冷液体的拓扑视图。
- 7. J.-P. Hansen and J. R. McDonald, 《液体理论》， Academic Press, London, 1986.
- 8. S. C. Glotzer, J. Nono. Sol., 274, 342 (2000). 空间非均匀动力学：来自模拟的见解。
- 9. S. Tokort, 《非均匀材料：结构与宏观性质》， Springer, New York, 2002.
- 10. C. K, 《固体物理导论》， New York, 1996.
- 11. J.-L. Barrat and J.-P. Hansen, 《简单与复杂流体的基础概念》， Cambridge University Press, Massachusetts, 2003.
- 12. P. M. Chaik and T. C. Lubensky, 《凝聚态物理原理》， Cambridge University Press, Massachusetts, 1995.
- 13. G. P. Debenedetti, 《亚稳液体》， Princeton University Press, Princeton, New York, 1996.
- 14. P. G. Debenedetti and F. H. Stillinger, Nature (London), 410, 259 (2001). 过冷液体与玻璃转变。
- 15. M. P. Allen and D. J. Tildesley, 《液体模拟》， Oxford University Press, Oxford, Kingdom, 1989.
- 16. D. Frenkel and B. Smit, 《分子动力学模拟》， Florida, 2001.
- 17. D. C. Rapaport, 《分子动力学模拟艺术》， Cambridge University Press, Massachusetts, 2004.
- 18. M. D. Edgar, C. A. Angel, and S. R. Nagel, J. Phys. Chem., 100, 12320 (1996). 过冷液体与玻璃。
- 19. W. Gotze and L. Sjögren, Rep. Prog. Phys., 55, 241 (1992). 过冷液体中的松弛过程。
- 20. W. Kaufmann, Chem. Rev., 43, 219 (1948). 玻璃态的本质与低温下液体的行为。
- 21. D. R. Reichman and P. Charbonneau, J. Stat. Mech., P05013.
- 22. F. H. Stillinger, J. Chem. Phys., 112, 3072 (2005). 势能。
- 23. P. G. Deb.etti, J. Chem. Phys., 112, 3172 (2005).
- 24. 2 ...................... ............................................................. ....... ............., J. Chem. Phys., 52, 18 ( (2009).
- 25. ......................... ............................................................................................................................................................................................................................................................................................................. Phys. Rev. E., 60, 3817 (2009).
- 26. A. Baranyi and D. J. Evans, Phys. Rev. A, 40, 3817 (1989).
- 27. R. D. Mountain and H. J. Raviche, J. Chem. Phys., 55, 2250 (1971).
- 28. T. Lazaridis and M. Karplus, J. Chem. Phys., 105, 4294 (1996).
- 29. P. Steinhardt, D. R. Nelson, and M. Ronchetti, Phys. Rev. B, 28, 784 (1983).
- 30. E. W. Hobson, 《球形与椭圆哈密顿量理论》， Chelsea, New York, 1955.
- 31. J. D. Weeks, D. Chandler, and H. C. Anderson, J. Chem. Phys., 54, 1168 (1971).
- 32. R. W. Zwanzig, J. Chem. Phys., 22, 1420 (1954).
- 33. P. R. Wolde, M. J. Ruiz-Monaster, and D. Frenkel, J. Chem. Phys., 104, 9932 (1996).
- 34. A. Vishnyakov and A. V. Neimark, J. Chem. Phys., 118, 7585 (2003).

