

## 332 大规模特征问题的递归求解

及其离散方案。12,261,272,319–325 变分计算中使用的适当动能算符取决于感兴趣的势能最低点的分子几何结构。可以理解的是，对于柔性分子或存在多种分子构型的高谱区域，选择坐标系是非常困难的。

最近在递归方法的基收缩方案方面也取得了进展。这些方案的本质是构建规模更小、光谱范围更窄的非直接直积基。一种可能性是使用能量等准则来裁剪直接直积基。例如，在离散变量表示（DVR）中，这相当于移除所有高于截断势能的格点。这种策略已被多位作者成功使用。241,264,272,326 另一种收缩方案是将系统分为几个子系统，并在哈密顿量来构造完备基。262,273 这种方法不仅涉及求解全特征问题，还要求解较小的子系统，而这些系统都适用于递归对角化方法。这种收缩思想的应用使得确定自由度高达 12 的多原子系统的能级成为可能。200,201,205,327 预计这一研究领域将保持活跃，并进一步推动递归方法的发展。328–331

## 致谢

我深感谢我的研究小组：李国辉、李世敏、顾士、谢大强和徐定国，尤其是陈荣庆。感谢感谢 Stephen Gray、Vladimir Mandelstam、Tucker Carrington, Jr. 和于华根就递归对角化方法及相关问题的深入讨论。我将本综述献给我的父母，感谢他们永恒的爱与鼓励。这项工作由国家科学基金资助。

## 参考文献

- 1. A. Messiah, Quantum Mechanics, Wiley, New York, 1968.
- 2. W. J. Jehre, L. Radem, P. R. Scholz, and J. A. Pole, Ab Initio Molecular Orbital Theory, New York, 1996.
- 3. D. G. Carney, L. Spandel, and C. W. Kern, Adv. Chem. Phys., 37, 305 (1978). 多原子分子振动转光谱的变分法.
- 4. S. Carter and N. C. Handy, Comput. Phys. Rep., 5, 115 (1986). 计算转动振动能级的变分法.
- 5. Z. Bacic and J. C. Light, Annu. Rev. Phys. Chem., 40, 469 (1989). 柔性分子转振动态的理论方法.
- 6. D. G, Truhlar, Resonances in Electron-Molecule Scattering, van der Waals Complexes, and Reactive Chemical Dynamics, ACS, Washington, D.C., 1984.
- 7. J. Z. H. Zhang, Theory and Application of Quantum Molecular Dynamics, World Scientific, Singapore, 1999.
- 8. R. Shinke, Photodissociation, Cambridge University Press, Cambridge, United Kingdom, 1993.
- 9. R. Kosloff, in Dynamics of Molecular and Chemical Reactions, R. E. Wyatt and J. Z. H. Zhang, Marcel Dekker, New York, 1996, pp. 185–230. 网格上的量子动力学.
- 10. J. C. Light and T. Carrington Jr., Ads: Chem. Phys., 114, 263 (2000). 离散变量表示及其应用.
- 11. D. Feller and E. R. Davies, in Reviews in Computational Chemistry, Vol. 1, K. R. Lipkowitz and D. B. Boyd, VCH, Wiley, 1990, pp. 1–43. 从头计算的基组与分子间相互作用.
- 12. J. M. Bradley and T. Carrington Jr., Chem. Phys., 99, 8519 (1993). 计算四原子分子振动能级的通用方法.
- 13. J. M. Bradley and T Carrington Jr., Chem. Phys., 101, 8494 (1994). 三原子特征值的计算：收缩基、Lanczos 还是传统的？哪种最有效？
- 14. G. C. Corey, Y. W. Tromp, and D. Lemoine, Numerical Methods and Their Applications to Schrödinger Equation, C. Cerjan, Ed., Kluwer, The Netherlands, 1993, pp. 23. 伪谱曲线坐标.
- 15. J. M. Bradley, J. W. Tromp, T Carrington Jr., and G. C. Corey, Chem. Phys., 100, 6175 (1994). 至 35000 cm⁻¹ 多原子分子的高激发振动能级.
- 16. G. Gazko, V. Szalay, A. Costar, and T. Furrenbach, J. Chem. Phys., 122, 024101 (2005). 正交哈密顿量中的奇异性处理.
- 17. J. K. McDonald, Rev. Phys., 48, 830 (1993). Rayleigh-Ritz 方法的近似. Johns Hopkins University Press, Baltimore, 1996.
- 18. W. H. Press, S. A. Teukovsky, W. T. Vertering, and B. Flannery, Numerical Recipes, 2nd ed, Cambridge University Press, Cambridge, United Kingdom, 1992.
- 19. B. Parker, The Symmetric Eigenvalue Problem, Prentice-Hill, Englewood Cliffs, New Jersey, 1980.
- 20. J. M. Bowen and B. Gazay, J. Chem. Phys., 94, 454 (1991). 计算特征值和特征的截断/回收方法.
- 21. S. E. Choi and J. C. Light, J. Chem. Phys., 97, 7031–7054 (1992). 非线性三原子分子的高激发振动特征值。H2O的应用.
- 22. C. Offenschfeld, J. Kassmann, and D. S. Barnett, in Reviews in Computational Chemistry, Vol. 23, K. B. Lipkowitz and T. R. Cund,, Wiley, New York, 2006. 量子化学中的线性标放方法.
- 23. Y. Saad, Numerical Methods for Large Eigenvalue Problems, Manchester University Press, Manchester, United Kingdom, 1992.
- 24. C. Lanczos, Res. Nat. Bur. Stand., 45, 255 (1950). 线性微分积分算符特征问题的迭代法.
- 25. C. C. Paige, J. Inst. Math. Appl., 10, 373 (1972). 特征问题的 Lanczos 计算变.
- 26. J. K. Callum and R. Willoughby, Res. Nat. Bur. Stand., 45, 255 (1950). 线性微分积分算符特征问题的迭代法.
- 27. K. B. Lipkowitz and T. R. Cund,, Wiley, New York, 2006. 量子化学中的线性标放方法.
- 28. Y. Saad, Numerical Methods for Large Eigenvalue Problems, Manchester University Press, Manchester, United Kingdom, 1992.
- 29. C. C. Paige, J. Inst. Math. Appl., 10, 373 (1972). 特征问题的 Lanczos 计算变.
- 30. Y. Saad and M. Schultz, SIAM J. Sci. Comput., 7, 856 (1986). 共轭梯度法.
- 31. R. W. Freund and N. A. Nach, Numer. Math., 60, 315 (1991). QMR: 准最小方法.
- 32. R. W. Freund, SIAM J. Sci. Comput., 13, 425 (1992). 共轭梯度型方法.
- 33. R. Barrett, M. Terry, J. Demmel, J. Dong, V. Eijhout, R. Pozo, and H. van der, Templates for the Solution of Linear Systems: SIAM, Philadelphia, 1994.
- 34. J. H. Wilkinson, The Eigenvalue Problem, Clarendon Press, Oxford, 1965.
- 35. C. C. Paige, J. Inst. Math. Appl., 18, 34 (1976). Lanczos 算法误差分析.
- 36. C. C. Paige, Linear Algebra and Appl., 34, 235 (1980). Lanczos 算法的准确性与有效性.
- 37. J. Callum and R. Willoughby, Comput. Phys., 44, 329 (1981). 对称矩阵的特征值计算.
- 38. R. Chen and H. Guo, Chem. Phys., 111, 9994 (1999). 单 Lanczos 算法.
- 39. N. Pauline, M. J. Bramley, T. Carrington, Jr., G. Kjaergaard, and B. R. Henry, J. Chem. Phys., 104, 7807 (1996). 甲醛的振动（J）激发能量与结合相互作用计算.
- 40. R. Chen and H. Guo, Chem. Phys., 277, 191 (1997). Lanczos 算法收敛性的基准计算.
- 41. R. Chen and H. Guo, Chem. Phys., 369, 650 (2003). 光谱范围对 Lanczos 和切比夫残差法的影响.
- 42. R. Chen and H. Guo, Chem. Phys., 319, 5762 (2003). 关于 Lanczos 的收敛缩放：递归残留生成法.
- 43. A. Nauts and R. E. Wyatt, Phys. Lett., 51, 2238 (1983). 多态量子动力学新方法：递归残留生成法.
- 44. A. Nauts and R. E. Wyatt, Phys. Rev. A, 30, 872 (1984). 激光-分子相互作用理论：递归残留生成法.

