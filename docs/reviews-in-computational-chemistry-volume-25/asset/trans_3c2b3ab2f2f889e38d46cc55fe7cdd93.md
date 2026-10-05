

## 242 过渡元素原子簇的磁性

电子态密度可以写为：

$D(\varepsilon) = \text{Tr}\delta(\varepsilon - H) \quad [A.2]$

其中 $\text{Tr}$ 表示算符 $\delta(\varepsilon - H)$ 的迹。态密度的矩 $\mu^{(p)}$ 定义为：

$$\mu^{(p)} = \int e^{ip}D(\varepsilon)d\varepsilon = \text{Tr}H^p \quad [A.3]$$

这些矩可以使用紧束结合近似来计算。通过引入满足方程的完备原子轨道组 $|x\rangle$：

$[T + V_{ij}(\tilde{R}_i - \tilde{R}_j)]\phi_{i_j}(\tilde{R}_i) = \varepsilon_{ij}\phi_{i_j}(\tilde{R}_i) \quad [A.4]$

可以通过展开迹函数来计算矩 $\mu^{(p)}$：

$$\mu^{(p)} = \sum_{i_1,i_2...i_p} \langle\phi_{i_1}|H|\phi_{i_2}\rangle\langle\phi_{i_2}|H|\phi_{i_3}\rangle\dots\langle\phi_{i_p}|H|\phi_{i_1}\rangle \quad [A.5]$$

并仅保留两中心邻域积分。此外，与 $\langle\phi_i|V|\phi_j\rangle$ 积分相比，积分 $\langle\phi_j|V|\phi_i\rangle$ 将被忽略。公式 [A.5] 中的求和涵盖所有从给定原子开始并结束的长度为 $p$ 的路径，使得电子在最近邻原子之间跳跃。

如果我们使用局部（且依赖轨道的）态密度 $D_{i_2i_2}(\varepsilon)$，则也可以计算矩 $\mu^{(p)}$：

$$\mu_{i_2i_2}^{(p)} = \int e^{ip}D(\varepsilon)d\varepsilon = \sum_{i_1,i_2...i_p} \langle\phi_{i_1}|H|\phi_{i_2}\rangle\langle\phi_{i_2}|H|\phi_{i_3}\rangle\dots\langle\phi_{i_p}|H|\phi_{i_1}\rangle \quad [A.6]$$

公式 [A.6] 显示了原子的局部键合与其电子结构之间的联系。态密度由所有的矩 $\mu^{(p)}$ 计算得出。该理论为计算态密度提供了一种很有前景的方法。许多数值方法是不稳定的，尽管 Haydock$^{20}$ 的递归方法非常有效。在这一格林函数方法中，局部态密度用局部格林函数 $G_{i_2i_2}(\varepsilon)$ 表示为：

$D_{i_2i_2}(\varepsilon) = -\frac{1}{\pi} \lim_{\eta\to0} \text{Im}G_{i_2i_2}(\varepsilon + i\eta) \quad [A.7]$

## 参考文献 243

## 致谢

这项工作得到了 MEC（资助号 MAT2005-06544-C03-01）和卡斯蒂利亚莱昂州政府（资助号 VA039A05）的支持。感谢 DIPC 在 2006 年夏季期间提供的招待和支持。

## 参考文献

- 1. I. M. Billas, A. Chatelain, and W. D. de Heer, *Science*, **265**, 1682 (1994). 分子带中铁、钴和镍簇的磁性。
- 2. I. M. Billas, A. Chatelain, and W. D. de Heer, *Phys. Magn. Mater.*, **168**, 64 (1997). 从原子到体相铁、钴和镍的磁性。
- 3. S. E. Apel, J. W. Emmert, J. Deng, and L. Bloomfield, *Phys. Rev. Lett.*, **76**, 1441 (1996). 镍的表面增强磁性。
- 4. M. B. Kleinbauer, *J. Chem.*, **116**, 9703 (2002). 镍：吸附对磁性的影响。
- 5. A. J. Cox, J. M. Montenegro-Carrizales, and L. Bloomfield, *Phys. Rev. B*, **49**, 1229 (1994). 过渡金属簇的磁性。
- 6. J. Zhao, X. Chen, F. Liu, and G. Wang, *Phys. Lett. A*, **205**, 308 (1995). 铁磁过渡金属簇的简单 d 模型。
- 7. J. Friedel in *The Physics of Metals*, J. M. Ziman, Cambridge University, 1996, pp. 340-308, 过渡金属。d 带在晶体和磁结构中的作用。
- 8. G. Pastor, J. Dorantes-Dvila, and K. Bennemann, *Phys. Lett.*, **148**, 458 (1998). 簇离离和尺寸依赖理论。
- 9. F. Aguilera-Granja, J. M. Montenegro-Carrizales, and L. López, *Solid State Communications*, **107**, 25 (1998). 镍簇的几何结构。
- 10. P. Jensen and K. Bennemann, **35**, 273 (1995). 簇原子壳和磁电阻理论。
- 11. K. Callaway, Academic Press, London, 1964.
- 12. J. C. Slater and F. Foster, *Phys. Rev.*, **94**, 1498 (1954). 周期电位的简化 LCAO 方法。
- 13. P. Löwdin, *J. Chem.*, **38**, 165 (1950). 分子和簇理论中使用原子波函数的非正交问题。
- 14. A. Fetter and J. Walecka, *Quantum Theory of Many Particle Systems*, McGraw Hill, New York, 1971.
- 15. A. Vega, J. Dorantes-Dvila, L. C. Balazs, and G. Pastor, *Phys. Rev. B*, **47**, 4742 (1993). 计算 sp 电子和 sp 杂化对小簇磁性的影响。
- 16. V. Heine, *Phys. Rev.*, **153**, 673 (1967)—过渡金属中的 s-d 作用。
- 17. G. M. Pastor, J. Dorantes-Dvila, and K. Bennemann, *Physica B*, **149**, 22 (1988). 铁簇的磁性。
- 18. G. M. Pastor, J. Dorantes-Dvila, and K. Bennemann, *Phys. Rev. B*, **40**, 7642 (1989). 3d 过渡金属簇磁性的尺寸和结构依赖性。
- 19. W. A. Harrison, Electronic Structure and the Properties of Solids, San Francisco, California, 1980.

## 244 元素簇的磁性

- 20. R. Haydock, in *Solid State Physics*, H. Ehrenreich, F. Seitz, and D. Turnbull, Eds., Academic Press, New York, 35 (1980), p. 215–24. 薛定谔方程的递归解。
- 21. J. Guevara, F. Parisi, A. M. Llois, and M. Weissmann, *Phys. Rev. B*, **55**, 13238 (1997). 过渡金属簇的电子性质：参数化中的溢出考虑。
- 22. P. Hohenberg and W. Kohn, *Phys. Rev.*, 136, B864 (1964). 不均匀电子气体。
- 23. W. Kohn and L. J. Sham, *Phys. Rev.*, 140, A1133 (1963), 包含交换和关联效应的自洽方程。
- 24. S. Lundqvist and W. H. March, Eds., *Theory of the Inhomogeneous Electron Gas*, Phys. Press, New York, 1986.
- 25. D. M. Ceperley and B. J. Alder, *Phys. Rev. Lett.*, **45**, 566 (1980). 随机方法研究电子气体的基态。
- 26. J. P. Perdew and A. Hunger, *Phys. Rev. B*, **23**, 5048 (1981). 多系统密度泛函近似的自相互作用修正。
- 27. A. Becke, *Phys. Rev.*, **38**, 908 (1988). 渐近行为密度。
- 28. J. P. Perdew, K. Burke, and M. Ernzerhof, *Phys. Rev. Lett.*, **77**, 386 (1996). 梯度方法。
- 29. J. P. Perdew, *Primer in Density Functional*, Vol. 620, C. Fiolha, M. Marques, Eds., Springer, Berlin, 2003. 用于非共线磁性的密度泛函理论。
- 30. U. Barth and L. Hedin, *Solid State*, S, 1629 (1972). 极化簇的局部交换相关势。
- 31. J. K, *Theory of Itinerant Magnetism*, Oxford, 2000.
- 32. D. J. Singh and D. Apopstant, Eds., *Structure and Magnetism of Complex Clusters*, Springer, Berlin, 2003.
- 33. S. H. Vosko, L. White and M. Nasar, *J. Phys.*, **58**, 1200 (1980). 立方铁中的自旋
- 34. Y. Tsunuda, *J. Phys.*, 10427 (2018)
- 35. R. Lorenz, J. Hafner, *Phys. Rev. Lett.*, **74**, 3688 (1995). Mn12 结构中的非共线磁性。
- 36. M. Liebs, K. Hummer, and M. Fähle, *Phys. Rev. B*, **51**, 5664 (1995). 结构对无定形铁、钴簇的影响。
- 37. V. Antropov, M. I. Katselson, M. Schlifgaarde, and B. N. Harmon, *Phys. Rev. Lett.*, **75**, 729 (1995). 簇中的从头计算自旋动力学。
- 38. M. Uhl and J. Kübler, *Phys. Rev. Lett.*, **77**, 334 (1996). 耦合自旋涨落理论。应用于铁、钴和镍。
- 39. T. Oda, A. Pasquarello, and R. Car, *Phys. Rev. Lett.*, 80, 3622 (1998). 全无约束的非共线磁性方法：应用于小铁簇。
- 40. C. Kohl and G. F. Bertsch, *Phys. Rev. B*, **60**, 4205 (1999). 小铬簇中的非共线有序化。
- 42. J. Kübler, K. H. Jock, J. Sticht, and A. R. Williams, *J. Phys. F*, 18, 468 (1988). 非共线磁性的密度泛函理论。

