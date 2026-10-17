
从表 10.2 可以清楚看出，与其他六种算法相比，`LF-IGWO` 的 `THD` 值最低。通过输出波形进行了 `FFT` 分析，并计算了这七种算法的每个 `THD`。图 10.5、图 10.6、图 10.7、图 10.8、图 10.9、图 10.10 和图 10.11 描述了 `FFT` 分析，而图 10.12、图 10.13、图 10.14、图 10.15、图 10.16、图 10.17 和图 10.18 展示了从不同优化技术中获得的波形。

![图 10.5 GWO 的 THD 频谱。](img/9781032900520_C010_005.jpg)

**图 10.5** GWO 的 THD 频谱。](#ch18.xhtml#f71b)

![图 10.6 HBA 的 THD 频谱。](img/9781032900520_C010_006.jpg)

**图 10.6** HBA 的 THD 频谱。](#ch18.xhtml#f72b)

![图 10.7 SMA 的 THD 频谱。](img/9781032900520_C010_007.jpg)

**图 10.7** SMA 的 THD 频谱。](#ch18.xhtml#f73b)

![图 10.8 ALO 的 THD 频谱。](img/9781032900520_C010_008.jpg)

**图 10.8** ALO 的 THD 频谱。](#ch18.xhtml#f74b)

![图 10.9 WOA 的 THD 频谱。](img/9781032900520_C010_009.jpg)

**图 10.9** WOA 的 THD 频谱。](#ch18.xhtml#f75b)

![图 10.10 PDO 的 THD 频谱。](img/9781032900520_C010_010.jpg)

**图 10.10** PDO 的 THD 频谱。](#ch18.xhtml#f76b)

![图 10.11 LF-IGWO 的 THD 频谱。](img/9781032900520_C010_011.jpg)

**图 10.11** LF-IGWO 的 THD 频谱。](#ch18.xhtml#f77b)

![图 10.12 ALO 的输出波形。](img/9781032900520_C010_012.jpg)

**图 10.12** ALO 的输出波形。](#ch18.xhtml#f78b)

![图 10.13 GWO 的输出波形。](img/9781032900520_C010_013.jpg)

**图 10.13** GWO 的输出波形。](#ch18.xhtml#f79b)

![图 10.14 HBA 的输出波形。](img/9781032900520_C010_014.jpg)

**图 10.14** HBA 的输出波形。](#ch18.xhtml#f80)

![图 10.15 SMA 的输出波形。](img/9781032900520_C010_015.jpg)

**图 10.15** SMA 的输出波形。](#ch18.xhtml#f81b)

![图 10.16 WOA 的输出波形。](img/9781032900520_C010_016.jpg)

**图 10.16** WOA 的输出波形。](#ch18.xhtml#f82b)

![图 10.17 PDO 的输出波形。](img/9781032900520_C010_017.jpg)

**图 10.17** PDO 的输出波形。](#ch18.xhtml#f83b)

![图 10.18 LF-IGWO 的输出波形。](img/9781032900520_C010_018.jpg)

**图 10.18** LF-IGWO 的输出波形。](#ch18.xhtml#f84b)

## 10.6 结论

从上述决定可以认为，受启发的莱维飞行改进灰狼优化算法（`LF-IGWO`）为逆变器的 `THD` 最小化问题提供了最佳解决方案。根据 IEEE 标准 12，逆变器的 `THD` 应低于 5%，通过该算法我们达到了这一限制。根据对所有七种算法的分析，`LF-IGWO` 的 `THD` 为 4.5，`PDO` 为 6.62，`SMA` 为 13.77，`GWO` 为 14.68，`HBA` 为 13.5，`ALO` 为 6.86。从收敛曲线可以观察到，与其他算法相比，`ALO` 和 `HBA` 具有较高的收敛速率，而 `GWO` 的收敛速率较低。根据 `NFL` 术语告诉我们没有适用于所有问题的算法。在这里，`NFL` 的影响表明用于获得最佳结果的 `SMA` 未能提供更好的输出。

## 参考文献

1. K. Kaur and Y. Kumar, "群智能及其各种应用：系统综述," In2020 International Conference on Intelligent Engineering and Management (ICIEM), London, UK, 2020, pp. 57–62, doi:[10.1109/ICIEM48762.2020.916017](http://dx.doi.org/10.1109/ICIEM48762.2020.916017).](#ch18.xhtml#r339b)

2. Mirjalili, Seyedali. "粒子群优化." *Studies in Computational Intelligence*, vol. 780, Springer Verlag, 2019, pp. 15–31. [`doi.org/10.1007/978-3-319-93025_2`](https://doi.org/10.1007/978-3-319-93025_2).](#ch18.xhtml#r340b)

3. Wolpert, D. H. and Macready, W. G. (1997). "优化的无午餐定理," IEEE Transactions on Evolutionary Computation, 1(1), 67–82. doi:[10.1109/4235.585893](http://dx.doi.org/10.1109/4235.585893).](#ch18.xhtml#r341b)

4. Mirjalili, Seyedali, Seyed Mohammad Mirjalili, and Andrew Lewis. "灰狼优化器." *Advances in Engineering Software*, vol. 69, 2014, pp. 46–61. [`doi.org/10.1016/j.advengsoft.2013.12.007`](https://doi.org/10.1016/j.advengsoft.2013.12.007).](#ch18.xhtml#r342b)

5. Bhatt, B., Sharma, H., Arora, K., Joshi, G. P., and Shrestha, B. (2023). "基于莱维飞行的改进灰狼优化：各种工程问题的解决方案," Mathematics, 11, 1745. [`doi.org/10.3390/math11071745`](https://doi.org/10.3390/math11071745).](#ch18.xhtml#r343b)

6. Mirjalili, S. (2015) 蚁狮优化算法. 丹麦.](#ch18.xhtml#r344b)

7. Faris, F. A., Houssein, E. H., Hussainc, K., Mabroukd, M. S. and Al-Atabany, W. (2018). 基于蚁狮和萤虫算法的新型优化技术. *Evolutionary Intelligence*, vol. 15, no. 4, pp. 1383–1422. [`doi.org/10.1007/s00521-017-3272`](https://doi.org/10.1007/s00521-017-3272).](#ch18.xhtml#r345b)

8. Amaire, Anas Atef, Asem S. Al-Zoubi, and Nihad I. Dib. 基于蜜蜂算法的径向配电网中多分布式发电和电容器最优配置的新颖方法. *Neural Computing and Applications*, 30, pp 413–435.](#ch18.xhtml#r346b)

9. Reddy, D. P., Reddy, V.C., and Manohar, G. (2017). 蚁狮优化在配电系统中的最优尺寸. 新纽约: Elsevier.](#ch18.xhtml#r347b)

10. Mirjalili, S. and Lewis, A. (2016). 鲸优化算法. 丹麦: Elsevier.](#ch18.xhtml#r348b)

11. Kumar, V. and Kumar, D. (2020). "二进制鲸优化算法及其在机组组合问题中的应用", Neural Computing and Applications, Vol. 1, pp. 1–17.](#ch18.xhtml#r349b)

12. Hashima, F. A., Houssein, E. H., Hussainc, K., Mabroukd, M. S. and Al-Atabany, W. (2021). 蜜蜂算法：用于解决优化问题的新元启发算法. 香港: Elsevier B.V.](#ch18.xhtml#r350b)

13. Elseify, M. A., Kamel, S., Abdel-Mawgoud, H. and Elattar, E. E. (2022). "基于蜜蜂算法的径向配电网中多分布式发电和电容器最优配置考虑功率损耗敏感性的新方法," Mathematics, Vol. 1, pp. 1–19.](#ch18.xhtml#r351b)

14. Almodfer, R., Mudhsh, M., Alshathri, S. and Abualigah, L. (2022). "利用蜜獾优化算法改进燃料电池的参数估计，"Frontiers in Energy Research, Vol. 5, pp. 231-243.

15. Li, S., Chen, H., Wang, M., Heidari, A. A., and Mirjalili, S. (2020). 粘菌算法：一种随机优化的新方法。Denmark: Elsevier B.V.

16. Ezugwu, A., Agushaka, O., Abualigah, L., Mirjalili, S., and Gandomi, A. (2022). "土鼠优化算法，"Neural Computing and Applications, 34. pp. 1–23. doi:10.1007/s00521-022-07530-9

17. Dorigo, M., Birattari, M. and Stutzle, T. (2006). "蚁群优化，"IEEE Computational Intelligence Magazine, 1(4), 28–39. doi:10.1109/MCI.2006.329691

18. Jacob, T. and Suresh, L. P. "基于生物启发算法消除多电逆变器谐波的综述，"收于 2016 年国际电路、电力与计算技术国际会议 (ICCPCT), Nagercoil, India, 2016, pp. 1–8, doi:10.1109/ICCPCT.2016.7530273

19. Krishna, A. R. and Suresh, L. P. "多电逆变器拓扑结构简要回顾，"收于 2016 年国际电路、电力与计算技术国际会议 (ICCPCT), Nagercoil, India, 2016, pp. 1–6, doi:10.1109/ICCPCT.2016.7530373

20. BarathKumar, T., Vijayadevi, A., Brinda Dev, A., and Sivakami, P. S. (2017). "利用粒子群优化减少多电逆变器谐波，"International Journal of Innovative Science, Engineering & Technology, 4(11). pp. 1–14.

21. Firdoush, S., Kriti, S., Raj, A., and Singh, S. K. (2016). "逆变器输出电压谐波的，"International Journal of Engineering Research & Technology CMRAES, 4 (02). pp. 1–17

22. Najafi, E. and Yatim, A. H. (2012). "新型多电逆变器拓扑的设计与实现，"IEEE Transactions on Industrial Electronics, 59, 4148–4154. doi:10.1109/TIE.2011.2176691

23. Arora, K., Joshi, G. P., Ragab, M., Rawa, M., Milyani, A. H., Mansour, R. F., and Yang, E. (2022). "使用先进控制器的负载频率与可再生能源双边合约，"Computers, Materials & Continua, 73(2), 3165–3180, doi:10.32604/cmc.2022.026966

24. Brest, J., Maučec, M. S. and Bošković, B. (2020). "单目标边界约束优化的差分进化算法：算法 j2020，"收于 2020 年 IEEE 进化计算国际会议 (CEC), Glasgow, UK, pp. 1–8, doi:10.1109/CEC48606.2020.9185551

25. Shi, Y., Gao, H., and Wu, D. (2014). "带变异策略的改进进化算法，"收于 2014 年 IEEE 差分进化会议 (SDE), Orlando, FL, pp. 1–8, doi:10.1109/SDE.2014.703154

# 区块链在食品供应链中的可持续应用

## 选择区块链技术服务提供商的标准

## 11.1 引言

先进技术对食品行业及其供应链的影响值得探讨，因为食品是生存的首要基本需求。如今，`IT` 领域的巨大发展和创新已将许多行业转变为更快、更顺畅的版本。Guo 等人 (2022) 声称，作为 `IT` 的最新趋势，`blockchain` 对商业革命做出了巨大贡献。Zut 等人 (2021) 报告说，区块链技术（`BT`）改变了许多行业。简单来说，区块链是一个存储点对交易详情的公共账本。这种系统没有中央权威或管理员，因此增加了透明度和安全性（Lawrence et al., 2020）。凭借新属性，`BT` 拓宽了 `IT` 的视野。食品供应链（`FSC`）是一个伙伴间（农民、加工商、运输员、店主等）之间存在信息流的环境，似乎是应用 `BT`——一种公共的点对点账本系统来缓解现有问题的完美场所。

如上所述，`FSC` 是一个涉及许多方的复杂场所。与 Chandan 等人 (2023) 的观点一致，`FSC` 不仅高度分散、集体化且多样化，而且在输出、任务流程和目的地方面也互不相同。这种复杂性导致了 `FSC` 的效率低下。Saha 等人 (2022) 指出，`FSC` 作为一个多层系统，面临着一些挑战，包括追溯性和食品安全。这些问题可能会干扰人类获得优质食品的基本权利；因此，必须对其处理和解决。

然而，技术与现实生活的融合并非风顺。良好的结果还很遥远，改变行业传统面貌和方式的探索必须首先克服由于未知以及许多人离开舒适区的恐惧带来的困惑。正如 Chandan 等人 (2023) 所述，`IT` 的利用率最低的是农食品行业。`BT` 已为人知近十年，但其在 `FSC` 中的应用仍然较低（Saha et al., 2022）。根据 Vu 等人 (2021) 的观点，尽管 `BT` 已获得食品行业的认可，但由于缺乏知识、研究和成功案例，其实践受到了阻碍。Choi 等人 (2020) 也发现，尽管 `BT` 因创建可持续供应链而受到赞赏，但其接受率很低。此外，更高的复杂度、隐私问题和相关成本是抵抗 `BT` 的一些原因（Choi et al., 2020）。就此而言，`BT` 的巨大潜力尚未被某些社会商业领域认可，其在 `FSC` 中的采用速度明显缓慢。

此外，`BT` 被世界视为一把双刃剑，并受到公众审查。一些人赞扬技术是可持续发展的工具。世界银行 (2019) 认为 `BT` 是工业革命的支柱，就像蒸汽机和互联网一样，彻底改变了工业格局。无论如何，一些人因高能耗而拒绝 `BT`。`BT` 的采用可能会通过过度电力消耗和排放导致环境破坏，打击循环经济中采用者的积极性（Rajeb et al., 2022）。

然而，`BT` 是一种多功能且丰富的技术，可以根据用户需求定制。Rieger 等人 (2022) 详述了某些高效能的 `BT` 解决方案，并认定 `BT` 是环境可持续的。在这里，他们要求进行公平的辩论。可持续性是当今的热点，各国正朝着可持续目标迈进。加拿大政府在《联邦可持续发展战略》（`FSDS`）中描述了对可持续供应链的需求。此外，下议院报告指出 `BT` 是增强 `FSCs` 的工具。因此，由于联邦的压力，`FSC` 参与者很快将负责可持续供应链，而 `BT` 将成为他们的解决方案。

然而，大多数食品供应链（`FSC`）参与者对区块链（`BT`）仍持有怀疑态度。考虑到他们的生计与食品供应链紧密相连，且知识有限，潜在的采用者在现阶段过于谨慎，不敢尝试。遗憾的是，在一个科技化的世界，尽管积累了所有的技术专业知识，食品行业（解决人类对食物最关键需求行业）却无法利用这些优势。
