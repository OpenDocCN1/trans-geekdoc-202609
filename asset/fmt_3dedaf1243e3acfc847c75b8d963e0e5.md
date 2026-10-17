
其中 $level_c$ 和 $level_s$ 分别表示解集 $A$ 在收性和稀疏性方面的水平。然后，通过对所有解集的水平调和平均值进行排序，得到每个解集 $A$ 的排名 $rank_A$。最后，通过以下公式计算每个解集的 CSD 值：

$$
CSD(A) = diversity(A) + \sum_{i=1}^{rank_A-1} \max_{rank_B=i} diversity(B),
$$

其中 $max_{rank_B=i}$ 表示排名为 $i$ 的解集中的多样性值。

![图 2.6 基于两组不同参考向量的多样性评估差异。(a) $c_x$ 分别等于 1, 0, 2, 1, 2, 0, 1。(b) $c_x$ 分别等于 1, 1, 1, 1, 1, 1, 1。](img/c02f006.png)

## 2.6 总结

在本章中，首先对演化大规模多目标优化进行了简要介绍。然后，介绍了一些基本概念，随后介绍了若干常用的大规模多目标优化测试问题。接下，详细阐述了三类性能指标，即仅评估收敛性的指标、仅评估多样性的指标，以及同时评估收敛性和多样性的指标。之后，本章介绍了为稀疏大规模多目标优化量身定制的测试问题。最后，详细介绍了一种能够同时对评估收敛性、稀疏性和多样性的专用性能指标。

在接下来的章节中，分别在第 3 章和第 4 章中详细阐述针对 LSMOPs 和稀疏 LSMOPs 的定制化 MOEAs，随后介绍了针对某些代表性应用定制的 MOEAs，主要包括社区检测、逻辑调度、电力系统、深度学习和放射治疗计划领域。

## 参考文献

1. X. Zhang, K. Zhou, H. Pan, L. Zhang, X. Zeng, and Y. Jin, “一种基于网络归约的用于大规模复杂网络社区检测的多目标演化算法，” IEEE Transactions on Cybernetics, vol. 50, no. 2, pp. 703–716, 2018.
2. Y. Su, K. Zhou, X. Zhang, R. Cheng, and C. Zheng, “一种用于大规模复杂网络社区检测的并行多目标演化算法，” Information Sciences, vol. 576, pp. 374–392, 2021.
3. S. Yang, Y. Tian, C. He, X. Zhang, K. C. Tan, and Y. Jin, “一种用于训练深度神经网络的梯度引导演化方法，” IEEE Transactions on Neural Networks and Learning Systems, vol. 33, no. 9, pp. 4861–4875, 2021.
4. J. Xiao, T. Zhang, J. Du, and X. Zhang, “一种基于演化多目标路径分组的用于大规模带容量车辆路径问题的启发式算法，” IEEE Transactions on Cybernetics, vol. 51, no. 8, pp. 4173–4186, 2019.
5. X. Xiang, Y. Tian, J. Xiao, and X. Zhang, “一种用于路网不确定性下选址问题的聚类辅助多目标演化算法，” IEEE Transactions on Industrial Informatics, vol. 16, no. 12, pp. 7544–7555, 2019.
6. C. He, R. Cheng, C. Zhang, Y. Tian, Q. Chen, and X. Yao, “用于变压器比率估计的演化大规模多目标优化，” IEEE Transactions on Evolutionary Computation, vol. 24, no. 5, pp. 868–881, 2020.
7. Y. Tian, Y. Feng, C. Wang, R. Cao, X. Zhang, X. Pei, K. C. Tan, and Y. Jin, “一种用于强度调制放射治疗计划的大规模组合多目标演化算法，” IEEE Transactions on Evolutionary Computation, vol. 26, no. 6, pp. 1511–1525, 2022.
8. Y. Tian, X. Zheng, and Y. Jin, “基于竞争优化器的有效大规模多目标优化，” IEEE Transactions on Cybernetics, vol. 50, no. 8, pp. 3696–3708, 2019.
9. W. Hong, P. Yang, and K. Tang, “大规模多目标优化演化计算：十年的进展，” International Journal of Automation and Computing, vol. 18, no. 2, pp. 185–203.
10. S. Huband, P. Hingston, L. Barone, and L. While, “多目标测试问题及其可扩展测试工具综述，” IEEE Transactions on Evolutionary Computation, vol. 10, no. 5, pp. 477–506, 2006.
11. H. Li, Q. Zhang, and J. Deng, “偏置多目标优化与分解算法，” IEEE Transactions on Cybernetics, vol. 47, no. 1, pp. 52–66, 2016.
12. R. Cheng, M. Li, Y. Tian, X. Zhang, S. Yang, Y. Jin, and X. Yao, “多目标优化基准测试集，” Complex & Intelligent Systems, vol. 3, pp. 67–81, 2017.
13. R. Cheng, Y. Jin, M. Olhofer, and B. Sendhoff, “大规模多目标和多目标优化的测试问题，” IEEE Transactions on Cybernetics, vol. 47, no. 12, pp. 4108–4121, 2016.
14. S. Liu, Q. Lin, K.‐C. Wong, Q. Li, and K. C. Tan, “演化大规模多目标优化：基准与算法，” IEEE Transactions on Evolutionary Computation, vol. 27, no. 3, pp. 401–415, 2021.
15. M. Li and X. Yao, “多目标优化中解集的质量评估：综述，” ACM Computing Surveys, vol. 52, pp. 1–38, 2019.
27. K. C. Tan, T. H. Lee, and E. F. Khor, “多目标优化的进化算法：性能评估与对比，” Artificial Intelligence Review, vol. 17, no. 4, pp. 251–290, 2002.
28. S. Bandyopadhyay, S. Pal, and B. Aruna, “多目标遗传算法、定量索引与模式分类，” IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), vol. 34, no. 5, pp. 2088–2099, 2004.
29. D. A. Van Veldhuizen and G. B. Lamont, “进化计算与向帕累托前沿的收敛，” *Proceedings of Late Breaking Papers at the 1998 International Conference on Genetic Programming*, 1998, pp. 221–228.
30. X. Zhang, Y. Tian, R. Cheng, and Y. Jin, “进化多目标优化中非支配排序的高效方法，” IEEE Transactions on Evolutionary Computation, vol. 19, no. 2, pp. 201–213, 2014.
31. J. R. Schott, 使用单标准和多标准遗传算法的容错设计。马萨诸理工学院，1995.
32. J. Wu and S. Azarm, “多目标设计优化解解的质量评估指标，” Journal of Mechanical Design, vol. 123, no. 1, pp. 18–25, 2001.
33. Y. Tian, R. Cheng, X. Zhang, M. Li, and Y. Jin, “多目标进化算法的多样性评估：性能指标与基准问题[研究前沿]，” IEEE Computational Intelligence Magazine, vol. 14, no. 3, pp. 61–74, 2019.
34. P. Bosman and D. Thierens, “多目标进化算法中接近性与多样性之间的平衡，” IEEE Transactions on Evolutionary Computation, vol. 7, no. 2, pp. 174–188, 2003.
35. K. Shang, H. Ishibuchi, L. He, and L. M. Pang, “进化多目标优化中超体积指标的综述，” IEEE Transactions on Evolutionary Computation, vol. 25, no. 1, pp. 1–20, 2020.
36. C. A. C. Coello Coello and M. Reyes Sierra, “协同进化多目标进化算法的并行化研究，” *Proceedings of the 2004 Mexican International Conference on Artificial Intelligence*, 2004, pp. 688–697.
37. H. Ishibuchi, T. Yoshida, and T. Murata, “多目标排列流水车间调度启发式算法中遗传搜索与局部搜索的平衡，” IEEE Transactions on Evolutionary Computation, vol. 7, no. 2, pp. 204–223, 2003.
38. P. Czyzżak and A. Jaszkiewicz, “用于多目标组合优化的帕累托模拟退火元启发式技术，” Journal of Multi‐Criteria Decision Analysis, vol. 7, no. 1, pp. 34–47, 1998.
39. E. Zitzler and L. Thiele, “多目标进化算法：比较案例研究与强力帕累托方法，” IEEE Transactions on Evolutionary Computation, vol. 3, no. 4, pp. 257–271, 1999.
40. E. Zitzler, 多目标优化的进化算法：方法与应用。苏黎世联邦理工学院，1999.
41. M. Fleischer, “帕累托最优测量在多目标启发式算法中的应用，” *Proceedings of IEEE International Conference on Evolutionary Multi-Criterion Optimization*, 2003, pp. 519–533.
42. D. A. Van Veldhuizen, 多目标进化算法：分类、分析与新创新。美国空军学院，1999.
43. Y. Tian, X. Zhang, R. Cheng, and Y. Jin, “基于改进反向代际距离指标的多目标进化算法，” *Proceedings of the 2016 IEEE Congress on Evolutionary Computation*, 2016, pp. 5222–5229.
44. O. Schutze, X. Esquivel, A. Lara, and C. A. Coello Coello, “将平均豪斯夫距离作为进化多目标优化的性能指标，” IEEE Transactions on Evolutionary Computation, vol. 16, no. 4, pp. 504–522, 2012.
45. H. Ishibuchi, H. Masuda, Y. Tanigaki, and Y. Nojima, “代际距离和反向代际距离中的改进距离计算，” *Proceedings of IEEE International Conference on Evolutionary Multi‐Criterion Optimization*, 2015, pp. 110–125.
46. M. Li, S. Yang, and X. Liu, “许多目标优化中基于帕累托算法的基于偏移密度估计，” IEEE Transactions on Evolutionary Computation, vol. 18, no. 3, pp. 348–365, 2014.
47. J. E. Fieldsend, R. M. Everson, and S. Singh, “使用无约束精英存档进行多目标优化，” IEEE Transactions on Evolutionary Computation, vol. 7, no. 3, pp. 305–323, 2003.
48. H. Ishibuchi, R. Imada, Y. Setoguchi, and Y. Nojima, “三角形线性帕累托前沿在反向代际距离中的参考点规范，” IEEE Transactions on Evolutionary Computation, vol. 22, no. 6, pp. 961–975, 2018.
49. M. Lalou, Q. Tahra, and H. Kheddou, “网络中的关键节点问题：综述，” Computer Science, vol. 28.
50. E. Zitzler, L. Thiele, S. Bandyopadhyay, and B. Aruna, “基于帕累托的多目标机器学习：综述与案例研究，” IEEE Transactions on Systems, Man, and Cybernetics, Part B (Cybernetics), vol. 34, no. 5, pp. 2088–2099, 2004.
51. G. Roff, U. Melzi, C. Castellani, and M. Cristani, “通过无监督神经网络求解大规模多目标优化，” IEEE Transactions on Cybernetics, vol. 51, no. 6, pp. 3115–3128, 2020.
52. A. Pons, A. Jaimes, and C. A. Coello, “多目标设计优化解集的质量评估指标，” Journal of Mechanical Design, vol. 123, no. 1, pp. 18–25, 2001.
53. H. Li, Q. Zhang, and Z. Deng, “许多目标优化中基于帕累托算法的基于偏移密度估计，” IEEE Transactions on Neural Networks and Learning Systems, vol. 29, no. 5, pp. 1716–2017.
54. Y. Tian, J. Pan, S. Yang, X. Zhang, and S. He, “通过双种群进化算法实现不可感知与稀疏攻击，” IEEE Transactions on Artificial Intelligence, vol. 4, no. 2, pp. 268–2022.
55. Y. Tian, X. Zhang, C. Wang, and Y. Jin, “用于大规模事实多目标优化的进化算法，” IEEE Transactions on Evolutionary Computation, vol. 24, no. 2, pp. 380–393, 2019.
