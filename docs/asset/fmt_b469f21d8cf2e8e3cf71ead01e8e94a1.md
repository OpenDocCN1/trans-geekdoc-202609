
从表 6.7 可以观察到，与其他算法相比，`AR-MOEA+SA` 在所有实例的无受损和受损场景下的疏散距离方面总体实现了最佳性能。此外，`AR-MOEA+SA` 使用的避难所建设最少。考虑到上述 `AR-MOEA+SA` 的结果仅经过 2000 次评估后获得的，与非代理模型辅助的算法 `BD`、`MNSGA-II` 和 `AR-MOEA` 相比，`AR-MOEA+SA` 以更小的计算代价在所有实例上实现了最佳性能。

为了深入了解 `AR-MOEA` 的计算效率，表 6.8 列出了四种对比算法和 `AR-MOEA+SA` 在四个实例上的运行时间，其中三种非代理模型辅助的算法执行了 20,000 次评估，而两种代理模型辅助的算法执行了 2000 次评估。从表中可以看出，与其他三个非代理模型辅助算法相比，两种代理模型辅助算法 `AR-MOEA+SA` 和 `SA-COSO` 在所有实例上具有最高的计算效率。这是因为两种代理模型辅助算法在进化过程中使用了大量的计算高效评估来替代昂贵的评估，从而导致了两种算法的高效率。

表 6.8 `BD`、`AR-MOEA`、`MNSGA-II`、`SA-COSO` 和 `AR-MOEA+SA` 在实例 A、B、C 和真实案例上的单次运行时间，其中 `BD`、`AR-MOEA` 和 `MNSGA-II` 执行了 20,000 次精确函数评估，`AR-MOEA+SA` 和 `SA-COSO` 执行了 2000 次精确函数评估。`AR-MOEA`、`MNSGA-II`、`SA-COSO` 和 `AR-MOEA+SA` 的运行时间为 20 次独立运行的平均值。

| 实例 | `BD` | `AR-MOEA` | `MNSGA-II` | `SA-COSO` | `AR-MOEA+SA` |
| --- | --- | --- | --- | --- | --- |
| A | 3.21e+4 | 3.53e+4 | 3.74e+4 | 3.33e+3 | 3.28e+3 |
| B | 1.31e+5 | 1.45e+5 | 1.55e+5 | 1.46e+4 | 1.33e+4 |
| C | 3.87e+5 | 4.10e+5 | 4.27e+5 | 4.19e+4 | 3.91e+4 |
| 真实案例 | 1.23e+6 | 1.52e+6 | 1.70e+6 | 1.58e+5 | 1.43e+5 |

此外，图 6.5 显示了随着代数的增加，`AR-MOEA`、`MNSGA-II`、`SA-COSO` 和 `AR-MOEA+SA` 在四个实例上执行的精确函数评估次数。从图 6.5 可以观察到，当处于相同代时，两种非代理模型辅助算法 `AR-MOEA` 和 `MNSGA-II` 执行的精确函数评估远多于两种代理模型辅助算法 `SA-COSO` 和 `AR-MOEA+SA`。这进一步验证了 `AR-MOEA+SA` 处理昂贵的 LSUSPs 是高效的。

![图 6.5 (a–d) `AR-MOEA`、`MNSGA-II`、`SA-COSO` 和 `AR-MOEA+SA` 在实例 A、B、C 和真实案例下不同代数下的精确函数评估次数](img/c06f005.png)

图 6.5 (a–d) `AR-MOEA`、`MNSGA-II`、`SA-COSO` 和 `AR-MOEA+SA` 在实例 A、B、C 和真实案例下不同代数下的精确函数评估次数。

从图 6.5 也可以看出，当处于相同代时，`AR-MOEA+SA` 执行的精确函数评估比另一种代理模型辅助算法 `SA-COSO` 多。然而，如图 6.6 所示，`AR-MOEA+SA` 在所有实例上的运行时间反而比 `SA-COSO` 短。原因在于进化过程中，`AR-MOEA+SA` 的代理模型训练消耗的时间远少于 `SA-COSO`。`SA-COSO` 的代理模型训练有助于创建比精确评估廉便宜的近似评估，但相对比 `AR-MOEA+SA` 的模型训练要贵。因此，仍有开发同时具有高模型精度和低训练成本的代理模型辅助遗传算法。

![图 6.6 (a–d) `SA-COSO` 和 `AR-MOEA+SA` 在实例 A、B、C 和真实案例上的训练时间（秒）](img/c06f006.png)

图 6.6 (a–d) `SA-COSO` 和 `AR-MOEA+SA` 在实例 A、B、C 和真实案例上的训练时间（秒）。

总而言之，从对比结果可以得出，`AR-MOEA+SA` 是一种在求解质量和计算效率方面求解 LSUSLPs 的有效且高效的优化算法。

## 6.4 总结

本章分别介绍了求解 LSCVRPs 的 CVRP 优化算法和求解 USLPs 的 USLP 优化算法。具体而言，引入了分治启发式算法 `EMRG-HA` 来求解 LSCVRPs，其中开发了一种名为 `EMRG` 的进化多目标路线分组方法对给定的路线集进行分组。通过在计算效率和求解质量方面与五种现有 LSCVRP 启发式算法进行对比，实验验证了 `EMRG-HA` 的竞争力。

1. K. Zheng, Z. Zhang, and B. Song, "大数据下的电子商务物流配送模式：以京东案例分析", *Industrial Marketing Management*, vol. 86, no. 1, pp. 154–162, 2020.
2. R. Kain and A. Verma, "供应链中的物流管理——综述", *Materials Today: Proceedings*, vol. 5, no. 2, pp. 3811–3816, 2018.
3. R. Lahyani, L. C. Coelho, M. Khemakhem, G. Laporte, and F. Semet, "突尼斯橄榄油采集中产生的多舱车辆路径问题", *Omega*, vol. 51, pp. 1–10, 2015.
4. S. Wang and J. Watada, "一种用于模糊随机不确定性下变容量基于 VaR 的选址问题的混合改进 PSO 方法", *Information Sciences*, vol. 192, pp. 3–18, 2012.
5. Y. Li, M. Chen, and J. Huo, "一种用于大规模异质容器装箱问题的混合自适应大领域搜索算法", *Expert Systems with Applications*, vol. 189, p. 115909, 2022.
6. C. Novoa and R. Storer, "一种用于随机需求车辆路径问题的近似动态规划方法", *European Journal of Operational Research*, vol. 196, no. 2, pp. 509–515, 2009.
7. J. Chen, F. Ling, Y. Zhang, T. You, Y. Liu, and X. Du, "基于蚁群系统的异质无人机覆盖路径规划", *Swarm and Evolutionary Computation*, vol. 69, p. 101005, 2022.
8. H. Zhang, Q. Zhang, L. Ma, Z. Zhang, and Y. Liu, "一种用于具有柔性时间窗的多目标车辆路径问题的混合蚁群优化算法", *Information Sciences*, vol. 490, pp. 166–190, 2019.
9. D. Cinalli, L. Martín, N. Sanchez‐Pi, and A. Garcia, "扩展集体智能进化算法：一种选址问题的应用", *Proceedings of the IEEE Congress on Evolutionary Computation*, 2020, pp. 1–8.
10. A. N. Letchford and J.‐J. Salazar‐González, "带容量车辆路径问题：伪多项式时间内的强下界", *European Journal of Operational Research*, vol. 272, no. 1, pp. 24–31, 2019.
11. X. Zhang, Y. Tian, R. Cheng, and Y. Jin, "一种基于决策变量聚类的大规模多目标优化算法", *IEEE Transactions on Evolutionary Computation*, vol. 22, no. 1, pp. 97–112, 2016.
12. W. Hong, K. Tang, A. Zhou, H. Ishibuchi, and X. Yao, "一种基于指标的可扩展大规模多目标进化算法", *IEEE Transactions on Evolutionary Computation*, vol. 23, no. 3, pp. 525–537, 2018.
13. H. Zille, H. Ishibuchi, S. Mostaghim, and Y. Nojima, "基于问题转换的大规模多目标优化框架", *IEEE Transactions on Evolutionary Computation*, vol. 22, no. 2, pp. 260–275, 2017.
14. X. Zhang, K. Zhou, H. Pan, L. Zhang, X. Zeng, and Y. Jin, "一种用于大规模复杂网络社区检测基于网络网络的多目标进化算法", *IEEE Transactions on Cybernetics*, vol. 50, no. 2, pp. 703–716, 2018.
15. M. N. Omidvar, X. Li, Y. Mei, and X. Yao, "用于大规模优化的基于差分分组的协同进化", *IEEE Transactions on Evolutionary Computation*, vol. 18, no. 3, pp. 378–393, 2013.
16. É. Taillard, "用于车辆路径问题的并行迭代搜索方法", *Networks*, vol. 23, no. 8, pp. 661–673, 1993.
17. R. He, W. Xu, J. Sun, and B. Zu, "用于大规模车辆路径问题区域划分的平衡 K-means 算法", *Proceedings of the 3rd International Symposium on Intelligent Information Technology Application*, 2009, pp. 87–90.
18. J. Zhang, "一种用于带容量车辆路径问题的基于密度的聚类算法", *Proceedings of International Conference on Computer Network, Electronic and Automation*, 2017, pp. 465–469.
19. D. Mester, O. Bräysy, and W. Dullaert, "一种用于车辆路径的多参数进化策略", *Expert Systems with Applications*, vol. 32, no. 2, pp. 508–517.
20. R. Bent and P. Van Hentenryck, "用于带时间窗的大规模车辆路径随机自适应空间解耦", *Proceedings of AAAI Conference on Artificial Intelligence*, 2007, pp. 173–178.
21. V. Praveen, V. Hemalatha, and K. R. Gomathi, "一种用于解决车辆路径的基于最近质心的聚类算法", *Proceedings of the Innovations in Electronics and Communication Engineering*, 2018, pp. 575–586.
22. J. Xiao, T. Zhang, J. Du, and X. Zhang, "一种用于大规模带容量车辆路径的进化多目标路径分组启发式算法", *IEEE Transactions on Cybernetics*, vol. 51, no. 8, pp. 4173–4173.
23. P. Toth and D. Vigo, "用于带容量车辆路径问题的松弛与方法", *Discrete Applied Mathematics*, vol. 123, no. 3, pp. 487–512.
24. K. Deb, A. Pratap, and T. Meyar, "快速遗传算法：NSGA-II", *IEEE Transactions on Evolutionary Computation*, vol. 6, no. 2, pp. 182–197.
25. B. L. Golden, E. Wasil, and I. Kelly, "用于车辆路径问题的元启发式算法", *Fleet Management*, 1998.
26. F. Li, B. Golden, and E. Wasil, "极大规模车辆路径问题的退火算法", *Computers & Operations Research*, vol. 87, pp. 52–62.
27. T. Vidal, M. Gendre, and N. Lahrichi, "用于带容量车辆路径问题的并行算法", *Operations Research*, vol. 60, no. 3, pp. 611–624.
28. J. Jin, T. Grainic, and E. Wasil, "用于带容量车辆路径问题的协同元启发式算法", *Computers & Operations Research*, vol. 44, no. 2, pp. 33–41.
29. C. Groër, "用于车辆路径问题的并行算法", *INFORMS Journal of Computing*, vol. 23, no. 2, pp. 315–330.
30. A. Syrichas and A. Crispin, "大规模车辆路径问题", *Computers & Operations Research*, vol. 87, pp. 52–62.
31. Y. Xiao, Q. Zhao, I. Kaku, and N. Mladenovic, "用于带容量车辆路径问题的变邻域模拟火算法", *Engineering Optimization*, vol. 46, no. 4, pp. 562–579.
32. F. S. Salman and E. Yücel, "随机网络损坏下的应急选址：来自伊斯坦布尔的案例", *Computers & Operations Research*, vol. 62, pp. 266–281.
33. V. Bayram and H. Yaman, "不确定性下的避难所选址与疏散路径分配：一种 Benders 分解方法", *Transportation Science*, vol. 52, no. 2, pp. 416–436.
34. M. Saadatseresht, A. Mansourian, and M. Taleai, "使用多目标进化优化方法的疏散规划", *European Journal of Operational Research*, vol. 198, no. 1, pp. 305–314.
35. Z. Chen, X. Chen, Q. Li, and J. Chen, "避难所的时间层次：用于地震避难所规划的层级选址模型", *International Journal of Geographical Information Science*, vol. 27, no. 8, pp. 1612–1630.
36. A. Ghaderi, M. S. Jabalameli, F. Barzinpour, and R. Rahmaniani, "用于解决无容量连续选址分配问题的有效混合粒子群优化算法", *Networks and Spatial Economics*, vol. 12, no. 3, pp. 421–439.
37. M. Karatas and E. Yakící, "一种多目标设施选址问题的迭代求解方法，" *Applied Soft Computing*, vol. 62, pp. 272–287, 2018.
38. V. Arya, N. Garg, R. Khandekar, A. Meyerson, K. Munagala, and V. Pandit, "用于 k 中位数和设施选址问题的局部搜索启发式算法，" *Proceedings of the thirty‐third annual ACM symposium on Theory of computing*, 2001, pp. 21–29.
39. X. Xiang, Y. Tian, J. Xiao, and X. Zhang, "一种用于路网不确定避难所选址问题的聚类代理辅助多目标进化算法，" *IEEE Transactions on Industrial Informatics*, vol. 16, no. 12, pp. 7544–7555, 2019.
40. Y. Tian, R. Cheng, X. Zhang, F. Cheng, and Y. Jin, "一种具有参考点适应性以提高通用性的指标多目标进化算法，" *IEEE Transactions on Evolutionary Computation*, vol. 22, no. 4, pp. 609–622, 2017.
41. B. Ji, X. Yuan, and Y. Yuan, "求解连续泊位分配问题的改进 NSGA‐II：使用多目标约束处理策略，" *IEEE Transactions on Cybernetics*, vol. 47, no. 9, pp. 2885–2895, 2017.
